---
title: "[SOLVED] ISO image burn in Linux"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by CyberDean on 2008-03-03
I have no problem burning an ISO within windows using InfraRecorder and/orImgBurn.  But now I'm in Ubuntu Linux 7.10 on a PC and server.  I have read some older threads that mention Brasero, K3b, Nautilus and GnomeBaker.  

What does 7.10 have for both PC and server, and if more than one, which is considered the better?

I am creating at this moment, a remastersys of my PC's OS.  Will remastersy also create the md5sum, or will I need to create it?

Thanks in advance for any help.

---

### Post by jpeddicord on 2008-03-03
Any of the applications you mentioned will burn an ISO image, however the easiest way to do it is to right-click it and select "Write to Disc." 2 clicks and 5 minutes later, out pops a CD. :KS

---

### Post by jcwmoore on 2008-03-03
with a default install you don't need any extra software, download your .iso and right click on the file and select write to disk.

---

### Post by iSplicer on 2008-03-03
> **jcwmoore said:**
> with a default install you don't need any extra software, download your .iso and right click on the file and select write to disk.

Ahh, the ease of Ubuntu. You can't do that in Windows can you?

---

### Post by CyberDean on 2008-03-03
Thanks to all three of you.  Your answer sounds great for a PC OS, but how do I burn on a server using CLI?  And what about the md5sum?

Thanks again.

---

### Post by jpeddicord on 2008-03-03
The "burn" package & utility should do the trick:

```
sudo apt-get install burn
```

I'm not sure how to invoke it right now, as the package of it is broken in Hardy (the development version), but it does burn ISOs.

As for MD5:

```
openssl dgst -md5 filename
```

---

### Post by logos34 on 2008-03-03
> **iSplicer said:**
> Ahh, the ease of Ubuntu. You can't do that in Windows can you?

Not natively you can't.  Well, there is something called 'cdburn.exe' that you can download from Microsucks --it's in some tool package or other, can't remember the name now.  But what do you expect? XP didn't even come with dvd burning software or add that capability later--you need 3rd party apps for everything it seems.  None of that, or even a word processor.  What a rip off.  It's like instead of buying an 'OS' you buy a 'house' and you think 'Wee!' until you dind out you just get the foundation, frame and windows, and have to add everything else--walls, doors, roof...

---

### Post by jcwmoore on 2008-03-03
ok, the md5sum is a file that you can use to verify that your download is not corrupt, I have never had a corrupt download so I really don't think you need to worry about the md5sum,

burning from a command line, 
[https://help.ubuntu.com/community/CdDvdBurning]("https://help.ubuntu.com/community/CdDvdBurning")

here is the details on burning from command line

---

### Post by logos34 on 2008-03-03
> **CyberDean said:**
> Thanks to all three of you.  Your answer sounds great for a PC OS, but how do I burn on a server using CLI?  And what about the md5sum?

[https://help.ubuntu.com/community/CdDvdBurning#head-c448095898e6c5c2443974bc3f1120aaa8948f7d](https://help.ubuntu.com/community/CdDvdBurning#head-c448095898e6c5c2443974bc3f1120aaa8948f7d)

$ **md5sum** filename.iso

---

### Post by jpeddicord on 2008-03-03
> **logos34 said:**
> [https://help.ubuntu.com/community/CdDvdBurning#head-c448095898e6c5c2443974bc3f1120aaa8948f7d](https://help.ubuntu.com/community/CdDvdBurning#head-c448095898e6c5c2443974bc3f1120aaa8948f7d)

$ **md5sum** filename.iso

Wow, I'm a failure. I never noticed that command.

:lolflag:

---

### Post by CyberDean on 2008-03-03
Thanks, this info appears to solve my problem.  And Thanks for the quick responses.

---

