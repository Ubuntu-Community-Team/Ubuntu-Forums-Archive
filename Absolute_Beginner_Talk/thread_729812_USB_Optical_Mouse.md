---
title: "USB Optical Mouse"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Reteric on 2008-03-20
Hi, I am absolutely new to Ubuntu. I had been having an issue getting my computer to boot back up from a crash while using Windows XP and got lucky and was able to bring it back online using linux. After a couple hours I figured out a few things, mainly how to run wine and what not, but the problem I am finding is not getting my usb mouse to reconize. Is there something special I need to do to make it reconize?

My mouse is a logitech mouse, usb, m/n: M-UV55a. Any help would be greatly appreciated. Also, if somone happens to know a decent place to start so I have a basic understanding of what some of the commands are an such. I am used to windows simply plug and play, so this is a lot to take on all at once.

Also, is it possible to make a dual boot once ubuntu has formatted the entire hd? Basically, my MBR was seriously messed up, and windows didn't want anything to do with my computer. I sorta want to run a dual boot so I can run my windows applications. I've noticed many guides talking about putting ubuntu on a system that windows is currently installed on in another partition, but is there a way to put windows on a ubuntu system?

---

### Post by The Cog on 2008-03-20
I can't help you with the mouse I'm afraid. But I guess any non-logitech one should work straight away.

Googling for "Ubuntu beginners guide" turns up lots of useful references.

Once Ubuntu has formatted the entire disk, you need to repartition to make space for Windows again. You can't do that from a live system that's running from the HD, so you will need to fire up the live CD and run the partition editor from there. After that, teh Windows installer will overwrite the bootloader that Ubuntu put on there, so you will need to replace the bootloader again: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Reteric on 2008-03-20
Thanks much. =)

---

### Post by Sef on 2008-03-20
> I am finding is not getting my usb mouse to reconize. Is there something special I need to do to make it reconize?

Have you tried another usb port?  Sometimes one can go bad.   

Your mouse should be recognized automatically.

---

### Post by Reteric on 2008-03-20
The USB mouse I've switched out, tried every port and also tried another mouse. No luck. This is however a laptop, so I don't know if that matters.

As for the solution to the windows install; I gave it a try and it still wouldn't install. So I now believe my computer simply has a hatred for windows on a personal level.

---

### Post by The Cog on 2008-03-21
I wonder if Ubuntu has an issue with the USB controller chip used then. Can it see a USB memory stick?

---

### Post by Reteric on 2008-03-21
Just gave it a try, no it cannot. Anything I can do to fix this error? Everything I plug into my USB ports simply blinks multiple times.

---

