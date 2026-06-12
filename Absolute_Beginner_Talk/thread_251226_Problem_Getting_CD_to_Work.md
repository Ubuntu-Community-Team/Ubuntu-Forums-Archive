---
title: "Problem Getting CD to Work"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Legend_of_Emus on 2006-09-05
Right, so I've been looking into Linux and things look interesting. I mainly just want to play around and see what it's like, and if I like it, I may use it as my main OS on my secondary PC. Having a look about and studying it for about a day, give or take, Ubuntu seems rather stable, supportive, easy, etc. So I download a LiveCD and try burning it. First I accidently burn the ISO itself (simple goof up). I tried again and burned right and it's still a no-go. So I try a third time. Instead of using Nero, I used the program the instructions used and followed it exactly. Still, it doesn't work. Thinking the ISO was corrupt or something, I download it again and try what I previously did to have no fix. Maybe this is a simple thing but I did search and found nothing (that worked, that is). The CD can be seen and works in Windows and so forth, but past BIOS, it just boots into Windows. Yes, I have it set in BIOS to boot from the CD-Rom drive and there is a pause and it reads the CD. It just never boots it up.

In case it matters, the hardware in question is a Dell Optiplex GX270.

Pentium4 2.8GHz
1GB of Ram
GeForce 4 Ti4200 with AGP8X

If you need any more info, let me know. Thanks in advance.

---

### Post by xyz on 2006-09-05
Hi-
Did you by any chance MD5 checksum your file? Aims at detecting,for sure, corrupted files:
How to generate MD5 checksum files

```
md5sum file.iso > file.iso.md5
```

How to check MD5 checksum of files
e.g. Assumed that file.iso and file.iso.md5 are in the same folder
```
md5sum -c file.iso.md5

```
Who knows (I hope not), you may have a whole batch of bad CD's!
From the UbuntuGuide Dapper.

---

### Post by Legend_of_Emus on 2006-09-05
Sorry if I sound clueless, but how do I check that? I didn't rule out bad copies, but after 4 of them, I'm thinking it might be my machine.

---

### Post by wpshooter on 2006-09-05
You say "First I accidently burn the ISO itself (simple goof up)."

As far as I know this is exactly what you are **SUPPOSED** to do.

You burn the ISO image onto your CD, you do NOT copy it to the CD.

I have never used NERO, but you need to point your program to the ISO image you downloaded and the use NERO's CD burning function to burn the ISO images onto the CD.

Then when you boot up your computer make sure that the very first thing you do is to run the CD integrity sumcheck function from the initial Ubuntu screen menu.

P.S. - I assume you are downloading either the DESKTOP or the ALTERNATE version of DAPPER DRAKE 6.06.1.

Good luck.

---

### Post by xyz on 2006-09-05
How fast did you burn it? Sometimes using the fastest speed won't do the job; 4x is often recommended!
Are you Gnome or KDE? If KDE, you have "k3b" which among other things runs a md5sum prior to beginning to burn the image. If you're in a hurry and/or new at this, this may be the simplest way to go. Even if you use Gnome, "k3b" can be downloaded via Synaptic (it will come with KDE-related dependencies which you would not need under Gnome but it would not hurt your system...just take up space)
Also, if you have one, think of using a CD-RW which you'll be able to erase in case the CD won't run for some reason.

I'll get back to you on how to md5sum in a console as soon as I have a minute.
Hang in there!

OOPS! Sorry..the above is valid under Ubuntu, didn't quite realize you're under Windows.

---

### Post by xyz on 2006-09-05
Under Windowns, you'll first need to download free md5sum.exe here:
[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)
Follow the instructions! Hope it works. Let us know.
Still it's a good idea tu burn slow and to use a CD-RW unless you work for a CD factory! See you.

---

