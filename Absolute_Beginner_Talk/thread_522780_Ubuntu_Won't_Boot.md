---
title: "Ubuntu Won't Boot"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Gorillagram on 2007-08-11
I tried booting up ubuntu today, and got a lovely error called "can't access tty job control turned off". After doing some research I found [this]("http://ubuntuforums.org/showthread.php?t=292533") thread, which seemed to imply the problem was a bad UUID. So I startup the grub editor by hitting escape on boot, and try to get rid of the UUID and replace it with /dev/hda1, but the change won't stick! Every time I type it in it gets replaced when I exit out and go back to check on it. I'm a complete Linux noob, and couldn't find anything else to help me on the web. Any help would be greatly appreciated.

---

### Post by soslug on 2007-08-11
You will as you already found the grub editor that you access from boot is only ever temporary this allows you to test new revisions of grub code without causing any damage to the grub boot loader itself. If you wish to make the change permanent you will need to edit the file located at the following location "/boot/grub/menu.lst". The entry you nned to edit is near the bottom of this file.

---

### Post by Gorillagram on 2007-08-11
> **soslug said:**
> You will as you already found the grub editor that you access from boot is only ever temporary this allows you to test new revisions of grub code without causing any damage to the grub boot loader itself. If you wish to make the change permanent you will need to edit the file located at the following location "/boot/grub/menu.lst". The entry you nned to edit is near the bottom of this file.

I checked that, it wasn't the problem. [This]("http://ubuntuforums.org/showthread.php?t=295508") thread looked like it may have had a solution that would have worked, but when I boot up my live cd it won't let me use the chroot command! It says "permission denied", even when I'm logged in as root.

---

### Post by Gorillagram on 2007-08-11
When I go into runtime 1, I get the error "Target filesystem doesn't have sbin/init". Anyone know how I can fix it?

---

### Post by Herman on 2007-08-11
Hello Gorillagram,
The most  common reason for having this type of error message is that your file system has been changed somehow since you installed GRUB.

Sometimes that can happen if you used (or even looked with), a non-Linux compatible hard disk partitioning utility. Only use a good 'Parted based partitioner like LibParted, Partman, GParted, QTParted, or Gnome Partition Editor, which are compatible with both Windows and Linux.

All filesystems have their own UUID number and you can easily find out what UUID numbers your own file systems have by typing the command 'blkid' into a terminal when a hard disk installed operating system is running,
```
blkid
```The UUID numbers you will see from the output from that command must match the UUID number in your /boot/grub/menu.lst file and also /etc/fstab file, or your operating system won't work very well or maybe not at all.

If you can boot into Ubuntu you can edit your boot/grub/menu.lst file by getting it with the following command, sudo gedit /boot/grub/menu.lst,
> sudo gedit /boot/grub/menu.lst Then when you have your /boot/grub/menu.lst file open you need to scroll down around the bottom of the file and look for where the UUID number is and if it doesn't match the one from the blkid output, copy the one from the blkid output and paste it over the one that's wrong in your /boot/grub/menu.lst entry.

You should also check your /etc/fstab file and make sure that has the correct filesystem UUIDs in it too.
```
sudo gedit /etc/fstab
```Once again it's a simple copy and paste operation to correct any wrong UUID numbers in /etc/fstab. 



If you can't even boot Ubuntu, you can still edit your /boot/grub/menu.lst and /etc/fstab files, you can use your Ubuntu LiveCD and boot with that instead. The blkid command didn't work from a LiveCD last time I tried it, so I use this command instead, [COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh [/FONT][/COLOR]that command works from either a live CD or hard disk installed system.
```
ls /dev/disk/by-uuid/ -alh
``` The following link will explain how you can mount your hard disk installed Ubuntu from the LiveCD and gain access to some of the vital files that sometimes people need to edit to get Ubuntu to boot up, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") [COLOR=Red]rescue your Linux system with a Live CD

[/COLOR] Here is another link about your error message, which links on to further reading. 
[busybox or tty error]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#busybox")        [COLOR=Red]/bin/sh: can't access tty; job control turned off

[/COLOR] There are other problems that can give you  error messages that look almost the same as the one you described, and they seem to be able to come from a variety of other causes, sometimes it can be hard to determine just what the problem is and therefore can be a hard one to solve. but try the above suggestion first and seem how you go. Most of the time that works. If not, work through sub-links from that last link I just gave you, it leads to a few more obscure remedies you might want to try that  have reportedly worked for others.

I can explain more if there is anything here that isn't clear and easy to understand, just ask.

Regards, Herman :)

---

### Post by Gorillagram on 2007-08-11
Thanks for the reply, Herman! I mounted the drive that has all the system files on it (sda1) while running live cd, and everything looks to be intact. I checked the uuids in grub and fstab and they all matched up the the correct one, so that's not the problem. I ran a fsck and it didn't report any problems on the drive. I read online that reinstalling udev or even doing a ubuntu minimal reinstall might help, but I can't perform a chroot command (I get the error "permission denied", even when using sudo), not to mention I'm having trouble accessing the internet through live cd. Keeps the replies coming!

---

### Post by Gorillagram on 2007-08-11
I read that the reason I may not be able to chroot the mount is because it has noexec on. Does anyone know how I can turn this off?

---

### Post by Herman on 2007-08-12
Sometimes I enjoy the challenge of trying to solve a problem so I can learn something new and maybe use what I learn to help others. Sometimes once a problem is understood, it turns out to be something really simple too.

Other times it might be quicker and better to install again and transfer files to a new installation. Ubuntu only takes around half an hour to install, and it's pretty darn quick to get back to the way it was before if you are good at it.
Try my [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm") Page if you think you might be interested in doing that. 

...or wait and maybe someone will come along who can help you with chrooting. I don't know much about that.

Regards, Herman  :)

---

### Post by ozPATT on 2007-08-12
Hi Herman, 

I am having similar troubles to the first post... I am trying to install 7.04 on my dads laptop, which currently has Vista on it. It is a 64 bit processor. 

I put the live cd in, and I get the tty error. 

I have used ```
ls /dev/disk/by-uuid/
``` as mentioned above to find the UUID, which I have got an alphanumeric string, so assuming thats the thing i am looking for. 

I cant edit anything though. It wont recognise sudo, or gedit, or nano, or anything like that. 

Do you know how I can edit the menu.lst and fstab files? 

Many Thanks! 

Patrick

---

### Post by Herman on 2007-08-12
Hello ozPATT,
I don't know about solving the tty error in the Live CD, the tty errors I was thinking of is when you get a tty error when you are trying to boot Ubuntu when it's already installed to hard disk.
It seems like there are lots of reasons why these tty errors come up then. The one I know how to try to fix is when the bootloader can't find the ramdisk initrd, which is kind of a miniature model or map of the file system that the kernel uses to help get it started. I hope I am making sense here. Or the initrd.img is faulty or corrupt, I'm only trying to guess about this.

About all I can suggest for a Live CD would be to make sure you ran the md5sum check on the .iso file you downloaded, Here's a web page that explains a bit about md5sum testing, [Pre-install Page]("http://www.users.bigpond.net.au/hermanzone/p17.htm"). 

If it passes the md5sum test on the .iso file you used to make the CD from and then when you put in the CD and it passes it's 'check CD for defects' test that you see there before you boot the live CD then it probably isn't the CD's fault.

There is only one more thing I know of that can go wrong.and that's if you have dust in your CD or DVD drive. Where I live there is always dust in the air, it's just part of the climate. I had trouble once with installing Ubuntu and it turned out to be from a dusty DVD drive but it would still play music and vivdeos and do everything else okay, but for installing software, we need a clean CD or DVD drive. 
EDIT: In my laptop, the lens in the CD/DVD drive slides out with the tray, so it's easy to clean with a Qtip (cotton bud) and some metholated spirits (be careful not to scratch it, use a clean Qtip only). For a desktop it is a lot harder. I had to take one apart to clean it and put it back together again, but I don't recommend that unless you have to.

Those are all the ideas I can think of for now. I have an AMD64 computer too and I installed Ubuntu for i386 in it okay and now I have the AMD64 version, so it's not that, I don't think. I hope you can solve it. 
So basically, all I can suggest is to try the CD in a different computer and try the computer with a different CD or try a different CD drive.

I hope it helps, 
Regards, Herman :)

---

### Post by ozPATT on 2007-08-12
Hi Herman, 

Thanks for taking the time to answer. Its a shame it seems like the problem isnt too simple... I will run the checks on the CD. My dad reckons its os it has vista on it, but I'm pretty sure that it wouldnt matter what operating system was on it, and is more likely the laptop? 

Thanks anyway, hopefully I can get something working :) 

Patrick

---

### Post by Gorillagram on 2007-08-12
In case anyone was wondering, I ended up just reinstalling, so far so good. Thanks for the help :)

---

