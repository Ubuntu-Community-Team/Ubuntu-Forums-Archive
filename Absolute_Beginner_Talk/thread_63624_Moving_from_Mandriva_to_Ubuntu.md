---
title: "Moving from Mandriva to Ubuntu"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by xavierh on 2005-09-08
I have been using Mandriva snce version 9.x for one of my computers at home. A coworker showed a couple of days ago the distro that he is using and now that I have tested it in a VMware virtual machine, I'm hooked.

I currently have installed in my computer Mandriva LE 2005 on an AMD Athlon 1.2 GHz with 512Megs of ram. I have a 160GB disk partitioned as fallows:

21 GB - Root (/)
1.7 GB - Swap
137 GB - Home (/home)

From previous experiences installing mandrake (no mandriva), the installer allows you to just delete the contents of  the root partition, leaving the "home" partition untouched.

Since I have 120 GB of files (movies, music, etc.) in that home partition, I would like to keep that data instact during the installation process. Is there a way to do that without repartitioning and /or reformatting the whole drive?

Thanks in advance for the help....

---

### Post by macgyver2 on 2005-09-08
[QUOTE=xavierh] Since I have 120 GB of files (movies, music, etc.) in that home partition, I would like to keep that data instact during the installation process. Is there a way to do that without repartitioning and /or reformatting the whole drive?[/QUOTE]
The Ubuntu installation won't require you to format your /home partition...just your / partition.

---

### Post by xavierh on 2005-09-08
[QUOTE=macgyver2]The Ubuntu installation won't require you to format your /home partition...just your / partition.[/QUOTE]

Thanks man but that does not seem so obvious to me.

The installer gives me 2 options, one to delete everything in my 160 GB Hard drive, and the other option is to manually partition the the drive. This is the part that has me confused, since I do not want to re-partition the drive.

which option shold I choose. On the manual partition option it dos sees my 3 partitions and I think I can choose the one that formats the only the root partition and mounts it as root (/)

am I on the right track here?

---

### Post by macgyver2 on 2005-09-08
[QUOTE=xavierh]Thanks man but that does not seem so obvious to me.

The installer gives me 2 options, one to delete everything in my 160 GB Hard drive, and the other option is to manually partition the the drive. This is the part that has me confused, since I do not want to re-partition the drive.

which option shold I choose. On the manual partition option it dos sees my 3 partitions and I think I can choose the one that formats the only the root partition and mounts it as root (/)

am I on the right track here?[/QUOTE]
Yes...choose the manual option and mount your old root partition under /.  The installer will want to format that.  Then you should be able to add your old home partition under /home without formatting it...or, if you're still wary you can just not mount your old home partition at all and once the system is installed you can go back and manually edit your /etc/fstab to include the home partition.  There isn't really any reason to worry, though.  When I did an install, keeping my /home and /usr/local intact the installer didn't mess with them at all.

Also note that once the system is installed and all that...if your new Ubuntu uid/gid information doesn't match the uid/gid info on your files on the home partition from Mandriva you'll have to fix that.

---

### Post by xavierh on 2005-09-08
[QUOTE=macgyver2]Yes...choose the manual option and mount your old root partition under /.  The installer will want to format that.  Then you should be able to add your old home partition under /home without formatting it...or, if you're still wary you can just not mount your old home partition at all and once the system is installed you can go back and manually edit your /etc/fstab to include the home partition.  There isn't really any reason to worry, though.  When I did an install, keeping my /home and /usr/local intact the installer didn't mess with them at all.

Also note that once the system is installed and all that...if your new Ubuntu uid/gid information doesn't match the uid/gid info on your files on the home partition from Mandriva you'll have to fix that.[/QUOTE]


Thanks macgyver, so I was ont he right track then.... well I don;t think I''ll be doing this today chances are it will be a wekeend job  :smile: ....Usually when I do this on mandriva... I rename my user's hme directory from /home/user to /home/user_old. That way, after the install is done I can create my user and then via root, assign read/write permissions to those files in the /home/user_old directory, and then move them at my convenience.

thanks again for your help...

---

### Post by Vulpus on 2005-09-08
I am a former Mandriva user and personally think Ubuntu is sooo much better.  I also think the forum members are a much more friendly bunch and more tolerant of newbies.

However, I do think the partitioning section of the Ubuntu install process needs some serious work.  It has to be far more automated and intelligent for those out there who don't even know what a partition is.

---

### Post by jobezone on 2005-09-08
[QUOTE=Vulpus]I am a former Mandriva user and personally think Ubuntu is sooo much better.  I also think the forum members are a much more friendly bunch and more tolerant of newbies.

However, I do think the partitioning section of the Ubuntu install process needs some serious work.  It has to be far more automated and intelligent for those out there who don't even know what a partition is.[/QUOTE]
 I agree in terms of the "hidden" ability to resize partitions. I say hidden because it's not that clear from the manual partition options (You choose the size of the partition, but I allways thought this was informational and couldn't be changed). I only learned about it from reading a website.

---

### Post by xavierh on 2005-09-09
I could not wait until the weekend......I jumped int he unbutu waters yesterday, and proceeded to install it. Afgter a couple fo hours of following this guide:

[http://ubuntuguide.org/](http://ubuntuguide.org/) 

I have an operational ubuntu system with all the apps and functionality that I need..... and I also managed to keep al my 120 GB of data intact.!!!. I'm liking this distro, altough I agree that the installer needs more help to make the choice more clear, specially when you are trying to install on top of an existing system.

I got a question though: in mandrake there is a option, to change the kernel that you can boot. So my question is, what is the latest kernel for ubuntu and if ubuntu has the same functionality or do you manually have to make the change?

Thanks

---

### Post by codejunkie on 2005-09-09
[QUOTE=xavierh]I could not wait until the weekend......I jumped int he unbutu waters yesterday, and proceeded to install it. Afgter a couple fo hours of following this guide:

[http://ubuntuguide.org/](http://ubuntuguide.org/) 

I have an operational ubuntu system with all the apps and functionality that I need..... and I also managed to keep al my 120 GB of data intact.!!!. I'm liking this distro, altough I agree that the installer needs more help to make the choice more clear, specially when you are trying to install on top of an existing system.

I got a question though: in mandrake there is a option, to change the kernel that you can boot. So my question is, what is the latest kernel for ubuntu and if ubuntu has the same functionality or do you manually have to make the change?

Thanks[/QUOTE]
2.6.11 is the latest in hoary you just need to install the linux-image package for your kernel through synaptic and just incase you didn't know because i didn't know switching from mandrake where it makes all the choices for you the -386 kernel image has a ram limitation that only recognizes up to 900 mb of ram so if you have a gig or more you need the -686 kernel image for intel processors the -k7 kernel image for an amd cpu and if you have dual proccesors you need the -smp image.

---

### Post by xavierh on 2005-09-09
[QUOTE=codejunkie]2.6.11 is the latest in hoary you just need to install the linux-image package for your kernel through synaptic and just incase you didn't know because i didn't know switching from mandrake where it makes all the choices for you the -386 kernel image has a ram limitation that only recognizes up to 900 mb of ram so if you have a gig or more you need the -686 kernel image for intel processors the -k7 kernel image for an amd cpu and if you have dual proccesors you need the -smp image.[/QUOTE]


Thanks amigo. I'm testing your recommendation in one of my vmware sessions. I'll try that at home after work. I also noticed the differet versions available in synaptics so I'll give that a try also..

---

### Post by xavierh on 2005-09-09
Interesting on vmware, after I selected the new kernel (2.6.11) the systems does not finishes loading. I'm able to put my username and password but then it just stays there....

I'm thinking it could be vmware but then again I don't know...

---

### Post by codejunkie on 2005-09-09
[QUOTE=xavierh]Interesting on vmware, after I selected the new kernel (2.6.11) the systems does not finishes loading. I'm able to put my username and password but then it just stays there....

I'm thinking it could be vmware but then again I don't know...[/QUOTE]
no it's mot vmware sorry i forgot the 2.6.11 kernel has a bug with inotify so you have to edit the /boot/grub/menu.lst file and add the noinotify option to grub theres instructions on the forum how to fix just search for disable inotify hope this helps.
just incase this helps a little more here's how i added that option to my /boot/grub/menu.lst file
```

title		Ubuntu, kernel 2.6.11-5-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.11-5-k7 root=/dev/hda1 ro quiet splash noinotify
initrd		/boot/initrd.img-2.6.11-5-k7
savedefault
boot

```
again hope this helps.

---

### Post by xavierh on 2005-09-09
[QUOTE=codejunkie]no it's mot vmware sorry i forgot the 2.6.11 kernel has a bug with inotify so you have to edit the /boot/grub/menu.lst file and add the noinotify option to grub theres instructions on the forum how to fix just search for disable inotify hope this helps.
just incase this helps a little more here's how i added that option to my /boot/grub/menu.lst file
```

title		Ubuntu, kernel 2.6.11-5-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.11-5-k7 root=/dev/hda1 ro quiet splash noinotify
initrd		/boot/initrd.img-2.6.11-5-k7
savedefault
boot

```
again hope this helps.[/QUOTE]

Excelent tip.... I tried it and it worked. Question: I made the change right at boot time. Changing it in the menu.lst file makes it permanent right?

---

### Post by codejunkie on 2005-09-09
[QUOTE=xavierh]Excelent tip.... I tried it and it worked. Question: I made the change right at boot time. Changing it in the menu.lst file makes it permanent right?[/QUOTE]
yep it makes it permanent glad you got it going.

---

