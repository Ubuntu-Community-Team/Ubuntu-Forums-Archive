---
title: "Boot hangs with GRUB Loading, please wait"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by martinwessel on 2006-08-28
I know I'm in the right place because I am an absolute Linux newby.  Despite this, I got ambitious and decided to install Ubuntu 6 Server on an older Dell server.  The server is a Pentium 3 with 512 MB RAM and two hard drives: a 9 GB SCSI and a 250 GB IDE.  Since I want to use the server as a Web site test environment, I'm not overly concerned with speed or capacity although I would like it to run reasonably well.

During the partitioning phase of the installation the partition manager showed both drives and seemed to indicate that the SCSI drive was the boot drive (BTW, I couldn't find a clear explanation of all the options available for the partition manager.  Someone might want to look into creating some kind of guide.) and that both drives had a number of partitions.  Because I wasn't sure about all the options and I didn't care about the data on the drives I went ahead and repartitioned both drives, setting the entire 250GB IDE drive as "/" and setting it as Boot while putting the swap space on the SCSI drive.  

The installation went well, but the system failed to boot since the BIOS couldn't find an OS.  Sure enough, the BIOS was set to look at the CD and then the SCSI drive for the MBR.  I changed the BIOS to use the IDE drive and it looked like it worked.  However, the boot process stopped with the message "GRUB Loading stage 1.5.  GRUB Loading, please wait."  

Thinking that whatever GRUB was it was dealing with a 250 GB boot drive and a 9 GB swap drive I let it wait... and wait... and wait...  In fact, I let it go overnight.  No luck.  I rebooting, watching for any messages, and the boot hung at the same place.  This time I noticed that the system was booting from the SLAVE IDE hard drive.  Thinking this was the problem, I checked the drive and moved the jumper to set it to Master.  But after powering the system up again it is still hanging in the same place.  

I've tried searching the forums but everything I've seen is in response to a GRUB error.  I don't have any errors, it's just hanging there saying "GRUB Loading, please wait..."  Since it's a new installation I don't mind reinstalling, but I'd like to understand what's going on so I don't waste my time.  Thanks for the help!

Martin Wessel

---

### Post by zxee on 2006-08-28
There are some pretty good install guides here at the ubuntu site, but for some reason they're not indexed well.
Check the many install methods/options here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

It sounds to me like grub can't find the correct partition, and if you change boot order after an install you will almost surely confuse grub.
See if you can open a shell (Alt+Ctrl+F1) and then type grub.
If you get a grub prompt (grub>) then type grub find /boot/grub/stage1
Note: you may need to use sudo before those commands.
If you get a response to the find command you can type setup hdX,X (the x's will of course be replaced by what the grub find command provides. You can also just try the live/install cd and try grub-install. Hope that helps.

---

### Post by jerry_c on 2006-08-28
I suspect you need to boot from the CD and edit > /boot/grub/menu.lst Here's a thread [http://ubuntuforums.org/showthread.php?p=1431609]("http://ubuntuforums.org/showthread.php?p=1431609") that mmight give you way more info than you need.

---

### Post by martinwessel on 2006-08-28
Thanks for the quick response!  Unfortunately...

zxee, I tried ALT-CTRL-F1 but got no response.  I did try booting from the install disk (I don't have a live disk, I have an Ubuntu Server disk) and was able to find the rescue mode.  I was given two options: > /dev/disks/disk0/part1
/dev/disks/disk1/part1 I chose the first option. From there I found the Install GRUB Boot loader option.  I then tried using > (hd0) and then > /dev/hda and then > (hd0,0) for the parameters and all three times I got an error: > The rescue operation 'grub-reinstall' failed with exit code 20
I looked on the install disks and found a shell option, but whenever I try to run grub I get an error about b-term.  So I'm still stuck.

jerry_c, while I appreciate the quick response, that whooshing sound you hear is the instructions you linked to going right over my head. ;)

I hope I'm giving enough information to accurately diagnose what's going on.  Let me know if anyone needs more detail!

Martin Wessel

---

### Post by jerry_c on 2006-08-28
Dear Martin,

Catlett, on the other thread, is really the expert on this, not me. The live CD and the install CD are the same. You can either run from the CD without installing, or install from it. Since you've already installed, you just want to run from it so you can snoop and fix things.

I've never used rescue mode. If you use regular mode, use the partition editor to view your partitions, mount them, then browse them, it will tell you a LOT. I believe rescue mode is all command line. Regular mode is gui and more user friendly. 

Starting your own thread in the hope somebody who knows anything is not as likely to get you the help you want as finding an active thread that is in the zone of your problem. Somebody on that thread will also be more likely to direct you to a more precise thread if that isn't your exact one.

I know you're a newbie, and, even though I've been using linux for about 4 years now, I'm not that advanced. It can be a steep learning curve, but it's worth is. nix based os's are real operating systems, not hobby os's like Windows is built on. They have been around since the 70's, and will probably be around for a long time. They are powerful and they work well. It's worth learning the basics like mounting file systems and how things all connect together. 

Everything in linux is a file, your drives, your cards, etc, but they need to be mounted to access them. When you boot from the hard drive, most of what you'd use is mounted normally. When you boot from the CD, you need to mount your partitions to browse and edit them.

Good luck.

---

### Post by xpod on 2006-08-28
As i have just recently discovered the "/" sometimes needs to be on something a little smaller.
The part that "boots" does at least.
That was just "part" of my recent install problems it seems.
Just a "thought" for you to consider mabey?????mabey not????

---

### Post by martinwessel on 2006-08-29
Thanks for the words of encouragement, Jerry!  I created a new thread because all the other threads looked like they were dealing with GRUB errors, which I didn't have, or were difficult for a newby like me to figure out.  No complaints, by the way, I fully expect more advanced users to get technical when speaking with people who understand what they're saying.  Goodness knows I do it when I talk to my peers.  That being said, I'm taking another look at the thread you recommended and I'll try to parse it out to see how it might help me.  If nothing else, I'm sure I'll learn more about Ubuntu and Linux!

I'd just like to clear up what may be a misunderstanding about what CD I'm using.  When I boot from the CD, I get a menu like this:
> Install to the hard drive
Install a LAMP server (which is what I'm trying to do)
Check the CD for defects (I tried this but no defects were found)
Rescue a broken system (how I got into Rescue Mode)
Memory test
Boot from the first hard drive
Every option gets me into some kind of text or pseudo-GUI mode, not a true GUI.  It occurs to me that might be why I'm having trouble following some of the instructions.  If anyone knows how to boot into a live server please let me know.  The thing is, I want to install the LAMP server because I want to use this box as a Web server although it will only be seen internally and not visible to the Web at large.  Being a newb, I also think that I want to use the server Linux kernel vs. the desktop kernel.

Getting back to reading threads, xpod, I've seen some threads that indicate the same thing you suggested.  To be honest, I've going to try Jerry's thread first but if that fails I'm going to do a reinstall and partition the IDE hard drive into smaller chunks.  Does anyone have an idea how best to partition 120 GB?  Keeping in mind that I'll be using the box as a LAMP web server?  Thanks again for the help and advice!

---

### Post by jerry_c on 2006-08-29
Oh, the server CD doesn't have the ability to run from the CD, I guess, except in rescue mode. The regular CD will. I do think you have a grub problem, and I think the folks on catlett's thread can help you, or at least point you to the right place. 

As far as partitioning goes, I'd suggest the way my expert did mine.

1 - windows boot sector FAT32
2 - windows, windows likes to be first
3 - linux swap - the reason for placing this here is that windows has been known to write beyond its partition limits and you don't want it writing on your linux distro.
4- expanded partion pointers
5+, in any order - linux root, 
alternate linux root for trying new distros, 
/boot, which gets mounted at your /boot directory of your / partitions
/home, to keep your data when you install new distros
some people like to keep /var separate as well but I don't need it, myself

Good luck.

---

