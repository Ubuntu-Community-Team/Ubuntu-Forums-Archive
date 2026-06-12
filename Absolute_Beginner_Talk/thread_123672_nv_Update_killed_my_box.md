---
title: "nv Update killed my box"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by john131971 on 2006-01-30
Hello,

Have give up trying to configure ati 9550, so i removed card and slide in a fx5200.  Reinstalled system, updated, ran automatrix without option to install nvidia drivers.  

Picked up the nv drivers from the update manager, followed how-to,  rebooted

Here is where the fun begins!

Normal grub menu, normal splash screen 
and then

Nothing but a blinking line top left hand corner
ctrl=alt-f1,f2 or even three finger 

Nothing

hard reboot

booted into recover mode
remember seeing boot up say tainted nvidia kernel or something

tried ls- dbootstrap...
tried cd etc/x11/xorg.conf
and nano vi

and nothing
 
apt-get installs links works fine but not sure where to find the trobleshooting guide



! Could someone explain how to debug this sort of problem or please point me to the nearest how-to!
2 Is it possibly to edit x11 from a live cd --no write access only read

thanks

---

### Post by Pragmatist on 2006-02-05
I would definitely try Knoppix first: [www.knoppix.org](www.knoppix.org)  For many people, Knoppix is the litmus test for hardware problems.  If it works there, at least you know that it is unlikely that anything is wrong with the hardware itself.  There are, of course, many alternatives.

If you want a floppy-based distro, there are many to choose from such as Tom's Root/Boot (aka tomsrtbt, [http://www.toms.net/rb/](http://www.toms.net/rb/))

Let us know what happens.

---

### Post by john131971 on 2006-02-06
I have and i use knoppix -v4.o.2dvd  for the qparted tools as needed!
Since last posting I have found the online doc's saying something to the nature that before the recover mode will work,  you have to edit the grub menu and add something like bin/bash.

Was really looking for help with how to debug system!  Without having to reinstall!
But I shall keep trying!

thanks for the response

have since pulled fx5200, reinstalled ati card and xp home and in the future i will dual boot and save up for a linux friendly motherboard

---

### Post by Pragmatist on 2006-02-06
If you have Knoppix then you can look at and edit any files on your system.  What does the /boot/grub/menu.lst  file look like? How about the contents of /var/log/messages,  the output from dmesg  and definitely use fdisk to check the partition table.  That would be a good start.  If you send the contents of those files and the output of those commands, I'll be happy to try and help you get it running.

---

### Post by john131971 on 2006-02-07
I guess the learning curve is starting to get on my nerves!

For future problem solving how would I get write permission from a live cd, while using live cd i  only had read permission

thanks again

---

### Post by Pragmatist on 2006-02-07
Yeah that confused me too when I first used Knoppix.  I'm pretty sure you need to type: ```
su
```  I don't think it will ask you for a password, because you don't have one! :o

---

### Post by Pragmatist on 2006-02-07
...almost forgot...Knoppix runs off of the CD, so to see into your hard drive you need to mount it.  So type: su  to get root privileges.  You may wonder why you have to switch to root when there is no password.  That is just done for security reasons to protect you from the system and the system from you.  You should only operate as root when necessary (even in Knoppix!)  After typing "su" type:
mount /dev/hda1  /mnt/hda1 or whatever your partition is.  The cd to the /mnt/hda1 directory and you will be at /  on your system.  If you don't know your partitions, look in /dev/mnt  there should already be directories for whatever partitions you have.  They will be empty until you actually mount them with the above command.

---

