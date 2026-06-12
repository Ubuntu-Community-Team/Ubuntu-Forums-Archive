---
title: "Burning CDs (HOW? please help)"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2006-01-05
Ok, I got nerolinux installed (full).
I try to write to the CD but there are a couple errors I am getting and then it will not let me burn.

As soon as it goes into the 'Write lead-in lead-out' state that is when I get the errors.
It says 'Invalid write state LG CD-RW CED-8080\H0 T0' rite after the lead-in lead-out thing starts

Here are the 3 basic errors I am getting when trying to burn.
1. Could not perform EndTrack
2. Could not Perform Fixation
3. Burn process failed at 8x

I am thinking it is just a permissions thing and that is why it won't let me write to CDs (current permissions is drwx-rwx, 707)
----

I also try to use the Automated window that pops up when I insert a CD-R into the tray. It asks if i want to burn audio,photo, or data. I click data, drag what I want onto the CD and click 'write to Disc' but I get this error 'Please put a CD-R/CD-RW, with at least 98 MiB free, into the drive.' I am using a 700mb CD (esa brand).
----

If it is a permissions thing how do I change the permission so that Owner,Group, & other can all Read,write,and Execute from the CD?

If anything. I am willing to give up Nerolinux for any other suggested CD-Burning apps that might be in the Synaptic. I just need them to burn DATA,PhoTos,& MuSiC.

---

### Post by Omnios on 2006-01-05
Not shure but burning at 4X or even 2X has solved a lot of peoples burn problems. Though it may be something more. Personaly I use a larg cdrw and just burn images onto it and errase it when something new comes out.

---

### Post by etc on 2006-01-05
Some recommended apps are:
-K3b
-Gnome Baker
-Graveman

Nautilus can also handling burning stuff too.

---

### Post by Omnios on 2006-01-05
```
-K3b
```

 Worked right out of the box for me just installed and it worked straight off

---

### Post by tim15856 on 2006-01-05
It looks like Nerolinux has problems.
[http://applications.linux.com/article.pl?sid=05/03/31/2136203](http://applications.linux.com/article.pl?sid=05/03/31/2136203)
[http://club.cdfreaks.com/showthread.php?t=158936](http://club.cdfreaks.com/showthread.php?t=158936)

---

### Post by nitricacid on 2006-01-06
Yea, I am really starting to think that neroLinux was a bad idea.
I am currently on GNOME GUI so I will be testing some of the recommended above.
Thanks guys\Gals :D

---

### Post by richard willacy on 2006-01-06
where to go for these k3b/ gnome baker software so i can put onto my linux, and another thing is when i download this software how to install

---

### Post by Kapre on 2006-01-06
[QUOTE=richard willacy]where to go for these k3b/ gnome baker software so i can put onto my linux, and another thing is when i download this software how to install[/QUOTE]

richard - you can get this apps from Synaptic or got to a terminal and type sudo apt-get gnomebaker or sudo apt-get k3b. You can try graveman too - sudo apt-get graveman

K

---

### Post by nitricacid on 2006-01-06
FOLLOWUP:

I just burnt what I needed on to a CD, GnomeBaker works GREAT!
Thanks Again :D

---

