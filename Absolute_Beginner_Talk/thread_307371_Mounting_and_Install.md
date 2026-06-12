---
title: "Mounting and Install"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by dmb83fan41 on 2006-11-26
[FONT="Arial"][COLOR="Green"]I have two questions.

(1) What does it mean to "mount" something?  And how do I mount?  For example my CD-RW/DVD-R drive.  I tried to insert a CD and DVD and told me it could not be opened until it was mounted.

(2) I found a legacy version of Doom. I am still very new to linux and have know idea on how to open this file "legacy_142_linux.tar.gz" and install it on Ubuntu 6.06.  

Any help would be great.  I love using Ubuntu and I recently installed Kubuntu last night.  It's great stumbling along and learning new things for a Linux newbie! :mrgreen: 

Thanks![/COLOR][/FONT]

---

### Post by LLRNR on 2006-11-26
Hi there!

For your first question, I'm not really sure, usually CDs get mounted automatically, as well as flash drives (memory sticks). Anyway, to see how to mount stuff in Ubuntu you could read [psychocats.net/ubuntu/mountlinux](psychocats.net/ubuntu/mountlinux).

For your second question, what you downloaded is a .tar.gz archive (it uses gzip compression) and you could extract it by simply double-clicking on it. Every such archive should have a "README" or "INSTALL" file, read it throughly and follow the instructions to install the game. You can un-tar an archive through the terminal/konsole too, like this:
```
tar xzfv *name*.tar.gz
```

This will extract the archive called *name* to the current directory.

I hope this helps, 

LLRNR.

---

### Post by catlett on 2006-11-26
Your cd drive should be set up to mount a disc as soon as it is put in, but there may be a problem. Open up a terminal (go to the top panel and enter into Applications>Accessories>Terminal) and enter this command
```
sudo cat /etc/fstab
```Then copy/paste the output into a reply.

The second part, a tar file is a compressed file, like a zip file in windows. You can enter a command like the previous poster said or you can right click on the file and choose "extract here". After it decompresses, there willl be a folder. Inside the folder will have a read me or an install file with instructions. If you want, copy/paste the instructions. If it is simple, I'll just give you the commands.

---

### Post by dmb83fan41 on 2006-11-26
[COLOR="DarkGreen"][FONT="Arial"]Part One: My read back:

@Laptop:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Part Two: From the readme file: (Is this a good version for Ubuntu?)

Linux Doom Legacy 1.41
======================

This is the public release of the binary Linux version
of Doom Legacy.

It has been compiled with GCC 3.2.2 and may not work on
old distribution. If llxdoom doesn't work on your system,
we suggest you to download the source code on our CVS 
server at sourceforge.net (or get the source tar ball)
and compile it like that:
make LINUX=1

Thanks for the help!![/FONT][/COLOR]

---

### Post by catlett on 2006-11-26
Try this for mounting. Put the cd in the drive. Then open a terminal and enter 
```
sudo mount /dev/hdc
```
Another thing that I use is the "disk mounter" applet in the panel. To use it, right click on the top panel and select "add to panel" then scroll down until you find "disk mounter". Highlight it and select "add". This puts icons for your drives and partitions on the panel. If you put a cd in and it doesn't mount, you can click on the cd icon and select "mount".
Try the mount /dev/hdc first. The only other thing would be if hdc wasn't the correct label for your cd drive.
I'll post in a minute about doom.



P.S. I couldn't get doom to work from that file. You may want to browse and/or post in this section for further help with gaming [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)
If the cd has an error again, post and we'll try to troubleshoot.

---

### Post by dmb83fan41 on 2006-11-26
Ok, it looks like it will mount whenever I put a CD-R/RW into the computer, but it still does not recognize DVD-R and I i'm pretty sure DVD's altogether.  I tried a few DVD-R I had burned, but with no luck yet.  Any ideas?

---

### Post by catlett on 2006-11-26
I don't know if this has anything to do with it but there are libraries in synaptic package manager for dvd. Open Synaptic Package Manager (In the top panel under System>Adminitsration>Synaptic Package Mnager) and select the 'search' button on the task bar. Then enter "dvd". Try installing things like 
libdvdread3
libdvdnav4
libdvdcss2
dvd+rw-tools
Maybe they will help. I have 2 dc/dvd drives and they both recognise dvds. I didn't install anything specifically for the drives but I did install applications for dvd playback.
Worth a shot at least

---

### Post by dmb83fan41 on 2006-11-26
I did try what you said and it looks like everything is installed already.  I even went on Automatix and installed everything related to playing and writing DVD's.  Any other thoughts?

---

