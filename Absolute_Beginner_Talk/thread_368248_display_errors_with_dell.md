---
title: "display errors with dell"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Kurupte on 2007-02-23
I came across and old laptop a dell inspiron 2600 soi decided to try and install linux on it. Icame across ubuntu and decided to give it a try. Whenever i try to install i get an error pertaining to x window or something and the graphics get all screwy. I looked up this error and found its a problem with the chipset so i downgraded my bios to a version that was supposed to work. It didnt. Can anyone tell me a simple way to work around this as i have no clue whatim doing  with linux yet. Also i have checked the md5 checksum so i dont think its an issue with the cd im using.

---

### Post by ed-j on 2007-02-23
I'll give it a try.

Which version of Linux are you using, and what make are your graphics drivers?

---

### Post by Kurupte on 2007-02-23
Ubuntu 6.10 and intel 830m graphics controller

also does anyone know of a good program to burn isos in windows i think the one i am using keeps screwing up the dvds im making.

---

### Post by Jussi01 on 2007-02-23
try doing 

```
sudo dpkg-reconfigure xserver-xorg
```

in terminal.

For windows ISO recording software...

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

### Post by dude420 on 2007-03-03
I ran into this exact same problem with my inspiron 2600 with the same hardware.  ](*,)   No matter what I did I could not get it to work properly.  Here are two of the post's I made on the subject and no one came up with a working solution for me - [http://ubuntuforums.org/showthread.php?t=309716](http://ubuntuforums.org/showthread.php?t=309716)  &  [http://ubuntuforums.org/showthread.php?t=309716](http://ubuntuforums.org/showthread.php?t=309716).  I saw a post once in a different forum that a guy got this to successfully work and he said to pm him for help if needed, but he never responded.  I will keep an eye on this post just in case anyone comes up with some other ideas.  On my desktop I am loving Ubuntu and have pretty much quit using winblows.  I hope someday I can get this to work on my laptop.   :-D

---

### Post by forkart on 2007-03-10
> **Kurupte said:**
> Ubuntu 6.10 and intel 830m graphics controller

also does anyone know of a good program to burn isos in windows i think the one i am using keeps screwing up the dvds im making.

I use magiciso to burn iso file to cd and dvd. it works very well.
[http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)

---

### Post by novosirj on 2007-03-30
The solution to this problem is that this machine requires BIOS version A08 in order to have Linux work properly. I upgraded a machine last night from A05 to A11 and it went from only displaying in 640x480 to not working at all. I just did the update back to A08 due to some recommendations I found elsewhere on the 'net, and lo and behold, it is working beautifully at 1024x768 in full color.

If you need a link to download the BIOS, it is currently available at [this location]("ftp://ftp.dell.com/bios/I2600A08.exe") on the Dell FTP site. You will need floppies, but it's a SMALL price to pay!

---

