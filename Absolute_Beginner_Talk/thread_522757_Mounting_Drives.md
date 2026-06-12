---
title: "Mounting Drives"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by VerdantLightning on 2007-08-11
I'm starting a new thread from my old one here [http://ubuntuforums.org/showthread.php?t=522424]("http://ubuntuforums.org/showthread.php?t=522424")
because I've gotten Ubuntu installed already. I've found it to be very intuitive so far, and it even connected me to the internet as soon as I plugged the external modem in (it was a headache with windows.)

I have two questions/problems to start out though:
1.) I'm having trouble accessing my removable media (i.e. CDr's). When I switched from Windows I burned a bunch of pictures and files and etc. on CDr's. I went to places then computer and found my drives (CDR and DVD) but I can't seem to access them. When I click on them, even when there is a disk inside it says "Unable to mount media there is probably no media in the drive." The CDs also do not show up on my desktop. But, when I restart whatever CD was in when I restarted shows up but then any other CDs I put in won't work. Any ideas? Am I missing something?

2.) Ubuntu has frozen on me twice, but not in a while now. Is there any command similar to CtrlAltDel in windows when this happens? Do i really not need some sort of virus protection? I'm getting antsy being connected to the internet not having downloaded an antivirus program.

Thanks

---

### Post by DirtDawg on 2007-08-11
Hi. I may not be able to help you with your CD Rom issues, but if you enter this command into your terminal and place output here, it will be easier for us to help you.
```
 cat /etc/fstab/ 
```

Also, you do not really need to worry about viruses. Firstly, there are very few (if any) Linux viruses to speak of. In addition, for a virus to really do any damage to your system, you would need to give it your password. The only thing to look out for is installing software from sources that are not trustworthy. If you stick to the software available in the Ubuntu repositories, you have absolutely nothing to worry about. In fact, for hoots I sometimes open some of those junk emails i get just to see what's in there.

---

### Post by carloslosgrande on 2007-08-11
[FONT="Comic Sans MS"]Hi, Ctrl-Alt-Backspace is a little similar to Ctrl-Alt-Delete in windows, it will stop and restart your X server.
Another method to 'unfreeze' your desktop is Alt-f2 which will take you to a terminal command line where you can enter > /etc/init.d/gdm stop and then>  /etc/init.d/gdm start
Of course if you just have an app hanging then you can load 'force quit' into your panel and just click it and then click the app and bingo![/FONT]
[FONT="Comic Sans MS"]Apparently Alt-f2, type 'xkill', enter, and then select the app and click will do the same.[/FONT]

---

### Post by VerdantLightning on 2007-08-11
Ok, I typed the stuff into the terminal:

riley@riley-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39fc69d4-511d-4cc9-a95f-9bd7086a200a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=72f5ebb1-3a07-4a60-84f4-48bdf8b1a3d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
riley@riley-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by DirtDawg on 2007-08-11
I'm sorry but I don't see anything unusual about your /etc/fstab/ file.

If the problem persits, you could try entering this command into your terminal:
```
 sudo mount -a 
```
This command simply asks Ubuntu to mount all the devices in your fstab file. If there is an error, please post it here. In the meantime, I will keep my eyes open for similar situations and, with any luck, someone with more knowledge about these kinds of issues will stumble onto this thread.

Sorry I cannot be more help.

---

