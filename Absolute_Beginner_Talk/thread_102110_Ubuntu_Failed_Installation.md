---
title: "Ubuntu Failed Installation"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by savje on 2005-12-11
Hi everyone!

I'm an absolute novice in the linux world but I'm eager to learn. Therefore I decided to try to install Ubuntu on my old computer (An compaq presario 400 mHz, 128 mb RAM and 8 gb hard disk). The installation goes just fine up to when the "guide" installs "remaining packages"... I then (about at 64%) get this error message:

"Copying packages to the hard disk failed. You may have run out of disk space in the target /var filesystem, or your CD drive may be having problems reading packages from the CD. Cleaning the CD drive or burning the CD at a lower speed may help.

Check /var/log/syslog or see virtual console 4 for the details."

I've tried installing it about ten times and I get the same error message each time (and a similar error message when I try to install the server "mod"). I've burned several installations cd disks (at the lowest speed on the burner), md5 checked the ISO file and so on. I don't think it's a problem with the space on the hard disk since I use all standard (with partitioning and so on). All the information in the forum, on ubuntu wiki and on the webb don't make me any wiser, so I hope that you guys could help me out since I really want to try out Ubuntu!

(btw it's a fresh installation, no other OS is or will be installed on the system)

edit: Ubuntu with live-cd runs just fine

edit #2: adding "solved" to title...

---

### Post by hod139 on 2005-12-11
Can you paste the error message from  /var/log/syslog.

---

### Post by savje on 2005-12-11
[QUOTE=hod139]Can you paste the error message from  /var/log/syslog.[/QUOTE]

How do I do that, since I don't have any OS on the computer? with a bootdisk?:???:

---

### Post by hod139 on 2005-12-11
During the install, you said you got this error message:
> Check /var/log/syslog or see virtual console 4 for the details.
By this point, the base system is installed enough to see what is going on.  The easiest thing may be to look at console 4, though the error message may have scolled by.  To look at the various virtual consoles, you can hold down the alt key, and press the corresponding function key.  So, to view virtual console 4, type:
 ```
alt-F4
```

Otherwise, you can find another console to login to, and then you can:
```
cat /var/log/syslog
```

---

### Post by savje on 2005-12-11
pressing alt + F4 I come to an console, last entry in the console seems interesting...

```
Dec 11 15:21:54 main-menu[3357]: DEBUG: virtual package mounted-partitions
Dec 11 15:21:58 archive-copier: languages: sv en
Dec 11 15:23:32 archive-copier: error: 'cp -a "/cdrom/pool/main/d/dhcp3/dhcp3-server_3.0.2-1ubuntu6_i386.deb" "/target/var/cache/archive-copier/ship/dhcp3-server_3.0.2-1ubuntu_i386.deb"' failed with code 1
```

by going to console on alt + F2, and running command "cat /var/log/syslog" I got a very long log ending with the same message as above but with the addition of (at the end):

```
Dec 11 16:14:38 init: ^MStarting pid 3298, console /dev/vc/2: '/bin/sh'
```

any help?

---

### Post by Rackerz on 2005-12-11
By any chance did you burn the installtion ISO to a dvd disk?

---

### Post by savje on 2005-12-11
No, ordinary CD-R disk...

Could it be a hardware error? I had a working win 98 installation on the computer just a couple a days ago (which I installed about 2 years ago. I could remember incorrectly, but I think I had some problems with the first installation too but the second one went just fine...)

---

### Post by savje on 2005-12-11
Would it help if I tried to install with another media, like usb installation or network-installation? And how do I do it? :)

---

### Post by hod139 on 2005-12-11
[QUOTE=savje]
```
Dec 11 15:21:54 main-menu[3357]: DEBUG: virtual package mounted-partitions
Dec 11 15:21:58 archive-copier: languages: sv en
Dec 11 15:23:32 archive-copier: error: 'cp -a "/cdrom/pool/main/d/dhcp3/dhcp3-server_3.0.2-1ubuntu6_i386.deb" "/target/var/cache/archive-copier/ship/dhcp3-server_3.0.2-1ubuntu_i386.deb"' failed with code 1
```
[/QUOTE]

Does anyone know what error code 1 means?  I did some quick searching on google and found nothing.  Also, how large is the root partition?  I think it needs to be at least 2GB for all the archive files to copy over and install.  Did you use the auto-partition tool during installation to partition the drive?  Maybe error code 1 is not enough disk space; which could easily be solved by making sure the root (/) partition has at least 2GB.

---

### Post by Gray. on 2005-12-11
Maybe try setting up the partitions manually and make them 

SIze: 7GB
Mount point: /
Type: ext3

Size: 1GB
Type: swap

That way you know it isn't due to space.

---

### Post by hod139 on 2005-12-11
On your next install, you can try passing the following argument:
```
archive-copier/copy=false
```
This argument tells the archive-copier to not copy all the packages onto the hard-drive.
The install will take longer since it will be constantly reading the cd, but it won't copy all the packages onto your hard-drive saving disk space.

---

### Post by Gray. on 2005-12-11
On your system, I think it would be better if you did the server install, then edit your sources.list to enable all the repos then ```
sudo apt-get install build-essential xubuntu-desktop
``` xubuntu-desktop will install xfce4 which is a lightweight window manager that still looks nice.

---

### Post by savje on 2005-12-11
Thx for the help!

I'll try an installation with manually partitions managing (tomorrow). (however I don't think that disk space is the problem :) )...

Since I'm totally novice I don't quite get what you mean in the last two posts... should I pass "archive-copier/copy=false" in one of the console (Alt + F2/F4 ) during the installation? and "sudo apt-get install build-essential xubuntu-desktop" when the server installation is complete (just so you know the server installation don't work neither)...

Maybe I should add that the main cd drive have had problems in the past, for exemple windows lost it sometimes , and sometimes the bios didn't find the drive neither. But since I've tried other cd drive then the ordinary (and the same problem occurs)... You guys think I should try a network installation?

edit: some spelling

---

### Post by Estariel on 2005-12-11
[QUOTE=savje]
Since I'm totally novice I don't quite get what you mean in the last two posts... should I pass "archive-copier/copy=false" in one of the console (Alt + F2/F4 ) during the installation? [/QUOTE]

no, right in the beginning a ubuntu logo will be displayed, with a text that tells you to press enter to start the installation.
There is a prompt there that reads
```
boot: 
```
enter your options here and then press enter to start the installation with these options.

---

### Post by savje on 2005-12-11
ohh I see... then with that flag (they are called flags, or?) it runs an ordinary installation but without copying the installation files to the hard disk before installing them...

---

### Post by hod139 on 2005-12-11
Thanks Estariel for making my post clearer.  The installation argument (not sure if flag is correct name but the idea is the same) I mentioned simple tells the installer not to copy the packages to a local disk.  So, as Estariel stated, when at the install prompt, you will write:
```
boot:archive-copier/copy=false linux  
```
to try reinstalling the ubuntu system without copying the packages to the local disk.  Or you could try Gray.'s suggestion, which would be to do a base install to minimize the total size
```
boot: server  
```
and then install the desktop environments afterwords.
> 
```

sudo apt-get install build-essential xubuntu-desktop

```


Lastly, you could combine the suggestions and do something like:
```
boot: archive-copier/copy=false server  
```

which should put as little as possible onto the hard drive and produce a working system.

Hopefully this works out for you.

---

### Post by BatsotO on 2005-12-11
8 GB disk supposed to be an old one. I've installed on old drives before, well just one drive, I ghost the rest. Those drives which didn't pass the ghost process tend to produce similiar error when i tried to manually install the system. I try several method i.e zero filling the drive, some time it works, some time it doesn't, so i think the drives was just too old :p

---

### Post by savje on 2005-12-12
What is ghost, and how do I do it? :S

---

### Post by BatsotO on 2005-12-12
[QUOTE=savje]What is ghost, and how do I do it? :S[/QUOTE]

Instead of installing a system on each of the drive, ghost anable to just copy one source disk containing a fully configured system to onother disk. Very usefull if you do mass instalation on computers with same basic specs.
Actually tha name refers to norton aplication (norton ghost) for backing up a system, but since norton ghost somehow didn't do linux partition, (newer version maybe able to do this) you can use g4l, which is ghost for linux, to do this. 
G4L basicly do dd if=/dev/hda of=/dev/hdb command (or something like that, i didn't quite remember). This copy the whole contain of hda to hdb, including empty block.

---

### Post by savje on 2005-12-12
Here we go again :D...

I tried out installing with typing:

```
boot: archive-copier/copy=false linux
``` and
```
boot: archive-copier/copy=false server
```

in the "installation-welcome-screen" (actually I of course just wrote "archive-copier/copy=false linux" since "boot:" allready is there).

Neither works, I get the same error message: "Could not find kernel image: archive-copier/copy=false"

I tried typing "linux archive-copier/copy=false" (since linux is a kernel, right?)and that installation is on it's way, but is it any different from the installation where I just press enter?

---

### Post by hod139 on 2005-12-12
I'm not sure why neither of those work.  If you read 
section 6.3.3.2 of this [link]("http://ports.ubuntu.com/ubuntu-ports/dists/breezy/main/installer-ia64/current/doc/manual/en/ch06s03.html"), 
you can see where I got this idea.  Looks like the other option is the expert mode install.

---

### Post by savje on 2005-12-12
by posting "linux archive-copier/copy=false" (as I said I did in my last post) get the the base system to install (just the base system...), the installation guide tells me to remove the the cd in order for the system to reboot and install packages... I remove the cd and reboot. The computer seems to start up just fine. GRUB loading etc... A screen with the ubuntu logo then is showed with some kind of log with "Loading modules                       ok" and so on... When that is finished a text (translated from swedish) say "Configuring the base system"... Then the basic installation view is shown and say (again translated) "Installing packages              Preparing for installation". a progress bar is showed which stands on 0%. and nothing else happens...

I then press alt + F4, to go to the console and there I find this text (translated):

```
Reading packages list...
Building dependens tree
Recommended package:
   laptop-detect
Following NEW packages will be installed:
xresprobe
/usr/bin/tail: var/log/base-config-pkgsel.log: file truncated
Reading packages list...
Building dependens tree
Recommended package:
   laptop-detect
Following NEW packages will be installed:
xresprobe
```

And the "_" stands blickning after the text. The console "answer" and I can write stuff in the console (notice the "laptop-detect", my computer isen't a laptop).

On alr +F2/F3 I come to a login screen which states:
```
Ubuntu 5.10 "Breezy Badger" ubuntu tty2

ubuntu login:
```

I've test to login and it works...

And if I reboot the computer the exact same thing as above (all of it) happens...

What should I do/try? plz help me :(

---

### Post by boomerian on 2005-12-12
savje,
Please know that, although I cannot help with answers since I, too, am very much new to Linux, I'm going through almost the same process-facing the same challenges! 
Still trying to install on a 400MHZ Celeron machine, 192MB RAM 6.4GB HDD, and partition error about disk space! (maybe bad CD image??)
You are not alone, and with the help of these patient and knowledgable people, we will get Ubuntu up and running. Do not get discouraged.
Cheers, from a part of the U.S. with many Scandinavians! I follow your progress with great interest, hoping to learn also.

---

### Post by savje on 2005-12-12
Thx, for your support! But I'm getting quite discourage, I see myself as an experienced computer user (however in windows and mac) but nevertheless I for example know how to program... But I could in my life never imagine that linux would be this hard to install (and ubuntu is supposed to be the most simpel os all linux dists... :S )...

Edit: I got an idea! from the console (alt + F2) I access something that resembles DOS very much, I played around a bit there and work my way to the "/" directory (root?)... Could I install all the required packages manullay from here?

Edit #2: should my "/" ext3 partition have a "Bootable flag"?

---

### Post by savje on 2005-12-12
After reading the installation guide (provided by hod139) I've made some heavy progress!

I runned the installation by using following boot parameter

```
boot: linux debconf/priority=low
```

same as *expert* I think...

in the meny I chosed "Check the CD-ROM(s) integrity"

on both my first (those I tried the installation with before, which past the ISO MD5 checksum) I got the following error message:

```
Integrity test failed
The ./filepath/filename file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted.
```

I burnt a new ubuntu installation cd (from the ISO) and tested it's integrity (the same way as above) and it got through, the cd is valid!

Just for the sake of it, I tested to install the ordinary installation (pressing enter when the ubuntu logo is showed and "boot: " is posted) but with manually configured partitions (1 gb swap, 7,4 gb ext3, root, bootable flag: on). The base system was installed just fine, and now the real test came... The copying of the remaining packages to hard disk (where the installation failed before)... and it worked! the installation continued... the guide told me to take out the cd for reboot, the computer rebooted GRUB started just fine, followed by the initializing of ubuntu "Loading modules" etc... followed by the installation of additional packages (newer got this far before :D)... the installation finished and I could not belive my eyes! IT ALL WORKED and it was probably my cd-writer that messed it up... 

Thanks for all the help! I really mean it! I promise I'll be back for more help :P

P.s. someone (me? :) ) should really make a down to the mud, basic walk-through /guide for installations of ubuntu, so my old grandmother could install without help. With does and don't and help when it don't working (like how to do the md5 checksum from the installation guide on the installation cd and so on) D.s.

Edit: spelling

---

### Post by hod139 on 2005-12-13
I'm glad to see that it was only bad cd burns.  Seems strange though that Ubuntu didn't make that obvious.

As for install guides, there are a bunch here: [https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

In fact, all of the ubuntu wiki is really good:  [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by GQed76 on 2005-12-13
Im getting the EXACT same thing.  Im redownloading the iso from a  different Mirror and re burning

Is there a way to verify the file in Windows XP

---

