---
title: "Installation Breaks!!!"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by download17 on 2006-10-13
I Have tried to install both Live CD (6.10) and Alternated Cd (6.06) with crazy installation problems for both attempts.
Live CD:
I get the error message: "Fatal Server Error: No screens found"
and it fails to load the xserver.  I've been through all of the forums and have found lots on this problem but none of it seems to work.  I've reconfigured Xserver and tried to restart it to no avail.  One thing I haven't been able to do is edit the xorg.conf file as every time I use nano it opens a new file.
HELP!

Alternated CD:
Everything seems to be all peachy until it goes to install the software packages.  The loading bar freezes @ 1% when it's installing the language package thingies.

In conclusion... I don't think Ubuntu likes my computer...
If you can be of any assistance at all, I would be indebted to you forever (yeah right!!!)
Luke D.      ](*,)

Ooo.... here's my system specs...:

DFI Lanpartu UT nf4 Ultra-D
AMD Athlon 64 3200+
1GB Dual Channel OCZ RAM
200GB Maxtor
80GB Maxtor
Sapphire Radeon X800GTO 256MB

---

### Post by d3v1ant_0n3 on 2006-10-13
Try the 6.06 LTS(dapper) x86 live cd...Seems like lots of people have had troubles with the x64 version for various reasons. I had trouble setting up edgy (6.10) on our AMD64, but dapper went fine.

---

### Post by download17 on 2006-10-13
Hmmmmm... I'll go and give that a try...although I'm in school right now... Da da da da!!! Thanks... I'll let you know IF it works... (fingers crossed)
Thanks
Luke D.:-k

---

### Post by diepruis on 2006-10-13
What command did you use for Nano? What video card are you using? If you have an ATI card it's probably your xorg.conf. Try this command (if you haven't already):

```

sudo nano /etc/X11/xorg.conf

```

---

### Post by download17 on 2006-10-13
Hey... yeah... I've already tried 'sudo nano /etc/X11/xorg.conf'... and when I do that it opens up nano with a blank screen with the words "new file" at the bottom... so it's like the file doesn't even exist or something...??? So I'm really confused cause after I reconfigure xserver there's a line that mentions that exact file (and location) being ouput (or written to..).  Anyways... and if I use dir I can see the folder X11 but I can't access it... I get this directory doesn't exist or something... am I typing it wrong... I can't see it but whatever... thanks... let me know what you think...
Luke D.

---

### Post by download17 on 2006-10-13
> **d3v1ant_0n3 said:**
> Try the 6.06 LTS(dapper) x86 live cd...Seems like lots of people have had troubles with the x64 version for various reasons. I had trouble setting up edgy (6.10) on our AMD64, but dapper went fine.

Hey... It Worked!!!... I had to change the graphics driver from ATI to FGLRX but it ended up working... I'm actaully running Ubuntu now...
Thanks Alot for your help...:) :) :)

---

