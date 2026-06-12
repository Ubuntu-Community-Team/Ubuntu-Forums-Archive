---
title: "mouse frozen"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-03-29
hi i did some updates via synaptic or the terminal i don't remember. just the usual ones not third party and now when the system boots into the desktop the mouse is frozen and i can't do a thing. that machine(my primary machine) has a dual boot situation and i am able to still boot into my windoze drive with no problems and can navigate freely with the mouse. there is also something else. i observed that the sound icon is muted. the sound is working when i boot into windoze but not with edgy.

---

### Post by devnulljp on 2007-03-29
Is your mouse something unusual?
Anyway, here's an overkill suggestion that involves re-setting  your whole X settings and hopefully fixing the mouse issue without too much fiddling.

Drop to a terminal (control-alt-F1), and log in there.
Make a backup of your current X configuration just in case
```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf-`date +"%d-%m-%Y"`.bak
```
Then re-set X like this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then try changing back to your X terminal and restarting X (Control-Alt-Backspace should do it)

You can always undo it all by logging in and copying your backed up xorg.conf over the new one.

---

### Post by rapattack1 on 2007-03-29
Thanks a friend came round that knows linux and he tried what you suggested but we got nowhere. Apparently the fault of this and a few other things that have been troubling the system is that I have an AMD machine. So when I installed Ubuntu he said it defaults to the lowest version which is for the Intel machines. I had been having quite a few issues so this may have been the last straw for the system. All I am concerned with before I have to reinstall an AMD version is how to get my files that I may want off the drive. I have a dual boot thing on this AMD machine and am on my windoze drive right now. My friend suggested that when I have a network happening I can retieve my files that way. We are going to put Debian on another AMD machine that I have. Do you know of any other way? I have a usb flash drive. Can I use that from the command line?

---

### Post by devnulljp on 2007-03-29
I wouldn't have thought that would make any difference - I've run x86 versions on AMD64 with no problems, but you're certainly better off with 64 bit version though. 
Lots of different ways to access your files for backup before you reinstall:
1. Mount your Linux partition under windows and just copy the files somewhere/burn to DVD. Look here for info about mounting: [http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)
I dual boot and access my Linux files in Windows no problem with ext2fs
2. Boot from ubuntu boot cd, mount your Linux partition(s) and copy/burn the files.
3.USB drive is easy. Insert the drive, run dmesg (or do tail messages) to see what device id it's been given, then mount it using something like  
sudo mkdir /media/usbdrive
mount -t vfat /dev/sda1 /media/usbdrive
4. You could just burn straight to CD/DVD from the command line too:  
[http://tldp.org/HOWTO/CD-Writing-HOWTO.html](http://tldp.org/HOWTO/CD-Writing-HOWTO.html)

---

### Post by rapattack1 on 2007-03-30
I like the last option!!! I can't really understand that page as to how to do it from the command line. Can you tell me step by step with a cd burner? And would I have to use a cdr or can I use a rewritable? I was going to put in another drive with Edgy even if it wasn't the right version and then transfer the files from one drive to another. So have two edgy drives. But burning form the command line sounds much quicker.
Btw my amd machine is not 64bit. I have been having problems from the start of the installation and it seems that the version issue is the only possible answer. Mind you it was way better than the crap I have had to deal with on Windoze.

---

