---
title: "Installing Unbuntu"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by additional on 2006-05-02
How may I install? I downloaded the ubuntu-5.10-install-i386.iso file which was 617 MB. How do I install it now?

Thanks.

---

### Post by Jagot on 2006-05-02
You will need to burn the .iso file as an image to a CD.  Then, providing your BIOS is set to allow you to boot from your CD drive, just pop the CD in, restart the computer and just go from there.  If you're thinking about dual-booting, and even if you're not, this is a nice guide as it gives screenshots of the process of installation as it progresses:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by christhemonkey on 2006-05-02
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

And then if it still isnt working

[https://wiki.ubuntu.com/CommonProblemsInstall](https://wiki.ubuntu.com/CommonProblemsInstall)

---

### Post by additional on 2006-05-02
thanks for the help. I thought that was the way to do it, just wanted to be sure.

---

### Post by romeozor on 2006-05-02
simple, burn the iso to a cd, put it in the drive, restart the system and there you have the installer
but you might wanna make a partition for it if you want multiple operating systems on the same pc, if not, just follow the steps in the installer

hmm i wasnt fast enough

---

### Post by additional on 2006-05-02
I have burnt it to a CD. Put the CD in my cd drive, restarted it and nothing happens.

What am I doing wrong?

---

### Post by Jagot on 2006-05-02
[QUOTE=additional]I have burnt it to a CD. Put the CD in my cd drive, restarted it and nothing happens.

What am I doing wrong?[/QUOTE]

Your BIOS may not be set to allow you to boot from CD.  You will need to have a look at the boot order in the BIOS and change it accordingly.

---

### Post by additional on 2006-05-02
have done so. Still dosn't work.

---

### Post by Phasmagon on 2006-05-02
You probobly have to set your bios to boot from CD.
Enter your bios utility by pressing one of the following F2, F10, DEL.
These are the most common triggers (your bios might have something else though). And change the boot order of your computer.
Some motherboards let you choose where to boot from, without entering the bios, by pressing Esc, or some other trigger.

---

### Post by Jagot on 2006-05-02
[QUOTE=additional]have done so. Still dosn't work.[/QUOTE]

You did burn the disk as an image and not as a data CD right?

---

### Post by halfvolle melk on 2006-05-02
What program did you use to burn it? Some require you to explicitly set it as either a data CD or a bootabl one.

---

### Post by additional on 2006-05-02
arghh dropped into the cd file and copied to CD. that wrong? if so how do I do it the proper way?

---

### Post by BarFly on 2006-05-02
I hate to say this, but it still sounds like you did not set up BIOS to boot from CD first.  The only other thing that is likely is that you have a bad ISO.  If that is the case, start over with a new download.  Did you do a checksum on it?

---

### Post by additional on 2006-05-02
I have set the BIOS correctly.

---

### Post by Jagot on 2006-05-02
[QUOTE=additional]arghh dropped into the cd file and copied to CD. that wrong? if so how do I do it the proper way?[/QUOTE]

[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by dmuha on 2006-05-02
im having some problems installing ubuntu as well. i've tried twice, and the installation freezes about 10-15 minutes into it.

---

### Post by halfvolle melk on 2006-05-02
You may want to check if the downloaded iso is ok:
[https://wiki.ubuntu.com/HowToMD5SUM](https://wiki.ubuntu.com/HowToMD5SUM)

If so, try burning it again at the lowest possible speed.

---

### Post by dmuha on 2006-05-02
the part it froze on is partitioning. the screen was going from black, to gray, to a strip of gray at the bottom of the screen. and then the screen got stuck. i left it overnight so i know that it really was froze.. i tried burning another copy, no luck

---

### Post by Raavea on 2006-05-02
Try this, it's pretty much what I did.

   1.      Use this guide - [Here](https://wiki.ubuntu.com/GettingUbuntu)
   2.      Use the wiki guide to verify and burn your disk - [Here](https://wiki.ubuntu.com/BurningIsoHowto)
   3.      Use one of the install guides (depending on your system, it says most users should follow the intel based one, and I did.) - [Here](https://wiki.ubuntu.com/Installation)

 That should sort you out... If it's freezing, all I can think of is it being a bad disc. Let's hope someone more experienced can help, if this doesn't.

---

### Post by dmuha on 2006-05-02
can you install ubuntu while running the live-cd?

---

