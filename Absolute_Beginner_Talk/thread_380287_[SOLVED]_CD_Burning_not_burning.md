---
title: "[SOLVED] CD Burning not burning?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Niedzwiedz on 2007-03-09
[B]Ok, I tried to find answers and it time I ask. I have tried different ways of Burning an ISO to Data CD. I tried the instructions from Ubuntu about the Copy to Disk, Graveman, K3B. I did apt-get and aptitude installs. OK, now I trying K3B again after atitude install. I get the same results as with other Burning Applications. They detect my Burner show the model. I start the Burn and it just sit there. Graveman had the Artist working away and doing nothing. CDrecorder spinning a CD. K3B saying it preparing to write and do nothing. Also, I can not cancel any of the Applications when they start and have to Re-Boot. Is there something I not turning on like a Password or what?
My woman friend says to install my Windows and burn it, but, I say we will never learn Ubuntu if we keep depending on Windows.
Thanks for any help. [/B]

---

### Post by dstew on 2007-03-09
What error messages are you getting?

---

### Post by Niedzwiedz on 2007-03-09
There are no error messages. Everything act like it working but it not. I can play CDs and DVDs run Basic Windows Programs with Wine. I was very impressed how everything works, except it just not want to Burn. I try a CD-R and wonder if a DVD work, but, it really not act like it even acess the drive for a Burn to start. I not sure how long to wait. But, waited as much as 1 hour and nothing.

---

### Post by wpshooter on 2007-03-09
The first obvious question is, you do know for a fact that your drive is a CD-RW ?

Do you have some CD-RW **MEDIA** to try ?  If so, use the erase CD-RW media function found on one of the drop down menus in K3b and once the CD-RW has been erased then try the burn ISO image function.

If K3b is installed correctly there is a minor pause before the writing actually starts to take place but unless you have just an extremely slow system, it should not take over a matter of minutes at the most for it to start showing progress.

Good luck.

---

### Post by dstew on 2007-03-09
Another way to troubleshoot is to run cdrecord from the terminal. Then you can see what is going on, all the error messages will be there.

---

### Post by Niedzwiedz on 2007-03-09
OK. I going to try what mentioned. I do have a clean CD-R and have burned with the drive using windows. I just tried burning as Root using; gksudo k3b and it still do the same. I do want mentioned and cross my fingers.

---

### Post by Niedzwiedz on 2007-03-09
I just tried to copy a simple file to see what happen with a click to start application for the desktop. The report seem to say some bad things, but, that may be good as far as fixing the problem. Here what I got;
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-generic
Devices
-----------------------
ASUS DRW-1612BL 1.06 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

SONY CD-ROM CDU5225 NYS4 (/dev/hdd, ) at /media/cdrom1 [CD-ROM] [CD-ROM] [None]
K3b
-----------------------
Size of filesystem calculated: 198

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-11-generic
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=48 -tao driveropts=burnfree -eject -multi -xa -tsize=198s - 

mkisofs
-----------------------
198
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Total translation table size: 0
Total rockridge attributes bytes: 256
Total directory bytes: 0
Path table size(bytes): 10

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sam/k3bIi1MBb.tmp -rational-rock -hide-list /tmp/kde-sam/k3bmaPogb.tmp -joliet -hide-joliet-list /tmp/kde-sam/k3bnoK7ic.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-sam/k3bRW1CPa.tmp

---

### Post by dstew on 2007-03-09
Here is the problem:

Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted

You cannot open the stream required by cdrecord, because only root can do that. To aquire the stream, you need to change the superuser bits on the files that make up cdrecord. This happened to me, and changing the su bits fixed it. Here are the files you need to change, and the commands to change them:

sudo chmod 4750 /usr/bin/cdrecord
sudo chmod 4750 /usr/bin/cdrecord.mmap
sudo chmod 4750 /usr/bin/X11/cdrecord.mmap
sudo chmod 4750 /usr/bin/cdrdao
sudo chmod 4750 /usr/bin/X11/cdrdao

You may not  have the same exact files, but if you locate any file with cdrecord in its name and change the permissions as shown, you should get it to go.

---

### Post by Niedzwiedz on 2007-03-09
Ha! Yea I was sitting here thinking;  Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
May be the problem and then I wonder if it may be common. Well I going to give it a try. May take a while before I can give an update, but, what siad I feel going to fix it. Thanks.

---

### Post by Niedzwiedz on 2007-03-09
OK. I did the sudo chmod 4750 on the cdrecord files and when I did it puts a red box with an X on them?  I feel this where the problem is, but, maybe I need something different from 4750

---

### Post by dstew on 2007-03-09
What does the terminal directory listing show as the permissions in the cdrecord files now? List them using ls -al.

If the SUID bit has changed successfully, there will be an s in the permissions where an x was before. And, the file owner shown in the directory listing needs to be root and not you.

---

### Post by Niedzwiedz on 2007-03-09
I must not be listing correct with my command line to get what you asking.
I did try another burn a while ago and the; Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
is gone from the debug list. So, getting closer to resolving.

---

### Post by Niedzwiedz on 2007-03-09
Oh! I should add I can cancel the operation now without everything freezing up and having to shut down and re-boot.

---

### Post by jdackle on 2007-11-08
I can't really help you with your CD burning problem.

However, there's a hint I can tell you about freezing programs in Linux: unlike Windows, you don't really have to shut down or reboot to shutdwn the problematic application - you can KILL it! ;)


There are severall "frontends" to the kill command itself:

**I.** The **kill** command itself: in a terminal type:```
kill -SIGKILL <process_id>
```Now... you'lll need to know the ID to the process you want to kill if you use this command. You can find that out by typing, in a terminal:```
ps ux
```This will give you a list of the processes the current user is running, including their name (e.g /usr/bin/gnomebaker) and their process ID (usually a 4 to 5 digit number)
So, suppose xosview happens to get frozen and I want to kill it:
1. I'll type "ps ux" in a terminal;
2. And find the line(s) referring to xosview:```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
(...)
jean      6230  1.0  0.3   4080  1860 ?        S    11:54   0:00 xosview +net
```
3. Kill the process referred by its PID:```
kill -SIGKILL 6230
```And *voila*! xosview killed and the system is clean again! :)


**II.** There is an easier command: **killall**:```
killall -SIGKILL xosview
```Please note this will kill all occurences of xosview and, assuming you had it running twice and only one of the windows was frozen, not just the problematic one...


**III.** There is also a **"graphical" tool** to kill programs: **xkill**: If installed on your system:
1. Applications menu->System tools(or is it Accessories? I usually use the terminal version...)->XKill
2. The mouse cursor will turn from your regular pointer to a skull! CAREFUL NOW!
3. Click the mouse pointer on the window you want to kill - DONE! And your cursor is back to its normal self. :)
*Note:* if you right-click instead of left-click, the operation will be aborted and none will be killed. ;)


**IV.** Or you can use a **GUI** - in Gnome, that'll be the **System Monitor** found in:
1. System->Administration->System Monitor
2. "Processes" tab;
3. There you have a list of processes much as that provided by ps in the terminal
4. You can select a process with the mouse-pointer and:
4.A. "Terminate" it using the button at the bottom. But this is NOT the same as killing the process! It's actually the graphical equivalent of giving the "-SIGTERM" option to either the kill or killall command - it is less "shutup and die!" than the -SIGKILL option... It may be enough or not... You can always start with a Terminate command and follow it with a Kill command if needed...
4.B. Right-click the process you want to kill. A menu will popup and, amongst others, you'll find an option to "Terminate and another to Kill. Choose the one you want and DONE! ;)

Hope that helped.

Cheers!

---

