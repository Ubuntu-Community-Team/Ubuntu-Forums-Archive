---
title: "Do I need GRUB"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by billbog on 2007-05-07
Hello - i am a newbie.
I have a second hard drive on which i want to install Linux. Do I have to install GRUB or can I access it from Windows. Dual Boot seems to cause problems and I am in no hurry. :confused:

---

### Post by John.Michael.Kane on 2007-05-07
Yes you need grub. Windows will not dectect your linux install, however ubuntu should detect your windows inatall, and ask if you want to add it to the grub menu.

---

### Post by mejy on 2007-05-07
> **billbog said:**
> Hello - i am a newbie.
I have a second hard drive on which i want to install Linux. Do I have to install GRUB or can I access it from Windows. Dual Boot seems to cause problems and I am in no hurry. :confused:

GRUB is basically the tiny app that runs on startup to allow you to chose operating systems, and then launches the appropriate one.  Dual booting doesn't cause problems with a modern linux setup, and will cause even less if you have a seperate harddisk for Linux.

First, you'll need to make sure the second drive is empty of anything you'll be needing.  Then, download or order an Ubuntu CD, put it in the computer and run through the installation process.  When it comes to partioning, you'll want to tell it to use your second hard drive - which should be called sdb (or concievably hdb).  You'll then want to allow the installer to install GRUB on that harddrive.  It should add Windows as an option in the GRUB menu automatically.

You've then got two options - chose which harddrive to boot from each time in the BIOS, or boot from the Ubuntu drive and select XP from the menu when you wish to boot it.

Seeing as this looks to be your first time installing Linux, its advisable to back up everything important on your computer in case you make a mistake somewhere down the line (its not unkown for people to rush and wipe the wrong partion or harddrive).

---

### Post by rich.bradshaw on 2007-05-07
Don't be scared of GRUB I have never had to manually set anything up for it to work. It just works. It's just  a menu to choose Windows or Linux. Windows appears in it automagically.

---

### Post by gigaferz on 2007-05-07
hello, 
I went trough something like that.

I unplugged the windows drive, and put it as slave but with the cable select configuration.

I plugged the empty hard drive on the master connector
I installed ubuntu on the  hard drive, with windows disconnected.

Once the installation was done, i connected back windows , but still on the slave connector.

When I booted up windows it reported a problem, and restarted normally, after this you just need to edit the grub. to appear longer if you wish, like 10 seconds or something

It worked twice for me, its been 8 months already, no problems at all.

---

### Post by billbog on 2007-05-07
Many thanks for the fantastic response . I need GRUB !.:) 
Can you resolve these issues for me :confused: 

1 ..My "Boot.ini" file is simply a backup file ,found under Windows/pss. Is this right? or should there be another copy .

2.. My" Boot.ini " file reads like this : 
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

As you see it offers 2 options . Should I edit and then delete one of these options ?

---

### Post by billbog on 2007-05-07
I did not mention that _both of these options w_ork when I am asked to select one at login.

---

### Post by Mr.Beast on 2007-05-07
> **billbog said:**
> Many thanks for the fantastic response . I need GRUB !.:) 
Can you resolve these issues for me :confused: 

1 ..My "Boot.ini" file is simply a backup file ,found under Windows/pss. Is this right? or should there be another copy .

2.. My" Boot.ini " file reads like this : 
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

As you see it offers 2 options . Should I edit and then delete one of these options ?

Hi, 
You can leave your boot.ini alone, grub will install "beneath" that layer if you will.
Lets just say you have hard disk1, and hard disk 2.  windows is on hard disk 1 and hard disk 2 is blank.
when you install ubuntu, it will detect windows on hard disk1 and it will put GRUB, a boot load manager onto hard disk 1 to fool windows into waiting until grub has passed control to windows (if thats what you want to do, or boot into ubuntu. )
you just need to be careful and make sure that you tell ubuntu install that it's going to install on drive 2. so, if I were you, I would go into windows with both disks visible, and then using the XP disk management, I would remove the partitions from the second disk so that it is bare.  this may make it easier for you to identify the correct disk.

hope this helps.

---

### Post by louieb on 2007-05-07
Here a description of how I did it. Leaves the Windows drive untouched.
[fedorajim - Dual Boot Linux & XP the Safe way with 2 Hard Drives...]("http://fedorajim.googlepages.com/dualbootlinux%26xpthesafeway...")

---

### Post by billbog on 2007-05-20
Thanks everyone - I've had no problems since manually partitioning the disk using G-parted:D

---

