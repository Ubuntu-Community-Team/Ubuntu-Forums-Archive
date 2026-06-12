---
title: "[SOLVED] failed installation, now 2 XPs 0 Ubuntus, help!"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-08-15
Hi,

Until now I was dual booting Ubuntu 7.04 and XP Pro SP2. Trying to test a new HD before making it my default laptop drive I thought (dumb!) to install XP on the HD connected as external USB...I booted the XP CD but the installation got stuck....so I removed the HD Usb.

Now when I boot I see TWO XP Pros, one of them fails to start and the other is this one I am using (with my files saved...ufff!! I got scared for a second!)..but No Ubuntu....

Where should I start to fix this? I want to remove the failed XP from the list and include Ubuntu...

Thanks,
D.

---

### Post by skymera on 2007-08-15
edit your boot.ini 

start>run>msconfig> there should be a BOOT.INI tab.

if not Google it.

---

### Post by jdrodrig on 2007-08-15
Thanks, but I am new to editing boot.ini could you provide me the copy of yours?

Also, is editing boot.ini a replacement of editing config files of grub?

---

### Post by skymera on 2007-08-15
ok
ermm..

there should be 2 entries.
ones a DUD.

im not an expert on this.
but you have to hash or remove one of them.

i think mine will be different.

```


[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


```

---

### Post by jdrodrig on 2007-08-15
Ok, thanks alot...I will try...but something tells me that editing GRUB configs rather than boot.ini could be a more long run solution....

Any other ideas, guys?

---

### Post by skymera on 2007-08-15
ok on grub is 2 XP's showing?

if so hash one out!
if the one left dosent boot, its the dud.

---

### Post by jdrodrig on 2007-08-15
Sorry for the confusion, I should be more explicit....GRUB does not load...but I thought that part of the solution should be to give GRUP back the role of boot ordering and then delete XP....

So, is it also possible to leave Windows the boot ordering role and just add Ubuntu to that list?

skmera? does your boot.ini takes care of everything or you load GRUB?

---

### Post by skymera on 2007-08-15
reinstall Grub.

if you have the Live CD, run it and find a guide that tells you how to reinstall grub.

that will sort out grub, then you should be able to choose

---

### Post by kayvortex on 2007-08-15
[This thread]("http://ubuntuforums.org/showthread.php?t=224351") should tell you how to reinstall grub. That should hopefully solve your problem.

---

### Post by jdrodrig on 2007-08-15
Thanks a lot to both of you guys!

I guess that would restore the list of bootable Operating Systems  I had before my fumbled additional installation of XP, right?

---

### Post by skymera on 2007-08-15
yes.

i tried to do recovery in XP disk and it got rid of my Grub :@
curse XP!

good luck and hope you get it sorted :)

---

