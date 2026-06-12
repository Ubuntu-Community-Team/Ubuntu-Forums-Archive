---
title: "how to speed up the boot-progress ?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by nano -i on 2007-01-05
hi !
I'm now useing ubuntu for quite a few months, but of course I'm still a ubuntu/linux nu-bee.

Allthough I'm very glad about useing Linux there is one thing which is realy annoying.
The boot-progress takes about 2 minutes !
When Ubuntu is loading it gets stuck for a while when it says that the rootsystem is going to be mounted.

I experienced the same problem with SuSe before I changed to ubuntu.


I don't realy know, which informations are important for you to solve this problems, so please ask for the informations you need !

btw: my pc has one hard disc which is parted in a windows and a ubuntu partition.


Thanks in advance ! :)

---

### Post by jvc26 on 2007-01-05
What is your RAM and Processor speed?
Il

---

### Post by rowanparker on 2007-01-05
Look [here](https://help.ubuntu.com/community/InitNG).

---

### Post by madmetal on 2007-01-05
install bootchart and take a look at the boot up procedure..
if you are using 6.06 i think 6.10 is way faster at boot up.

---

### Post by nano -i on 2007-01-06
> **Illuvator said:**
> What is your RAM and Processor speed?
Il

1024 MB DDR Ram and AMD Athlon 64 3000+ (though I use the i368 version but this has nothing to do with the problem, because when I used SuSe i installed the 64-bit version and I had, as already mentioned, the same problem)

---

### Post by Sasa_Ivanovic on 2007-01-06
For me Ubuntu is booting twice as faster than Windows.

---

### Post by nano -i on 2007-01-06
> **Sasa_Ivanovic said:**
> For me Ubuntu is booting twice as faster than Windows.

It would be cool, If it could be like this on my pc, too. :-k

---

### Post by madmetal on 2007-01-06
some usefull (imho) links 

[http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

i hope these will help..  
like i said use bootchart to see what delays booting procedure..

---

### Post by Zdravko on 2007-01-06
> **Sasa_Ivanovic said:**
> For me Ubuntu is booting twice as faster than Windows.
For me Ubuntu us booting twice as **slower** than Windows. Dunno why :-?:-k

---

### Post by Sasa_Ivanovic on 2007-01-06
it's a relative term.
it will always remain a mistery...

---

### Post by nano -i on 2007-01-06
Allright madmetal, I will check those links.

The image which has been created by bootchart is attached.

---

### Post by madmetal on 2007-01-06
well without being an expert ,
there is a long dead period (70sec) that the hard disk is not used and the modprobe works all this time..

do you have dma on?

---

### Post by nano -i on 2007-01-06
> **madmetal said:**
> 

do you have dma on?

Huh ... I'm not quite sure about that. ](*,) 
To be honest I don't know where to look for this.
I found no information concerning this in the bios.
But in the windows systeminformations it says that the dma controler is activated.
So I guess dma is on.

---

### Post by xyz on 2007-01-06
Hi,
Check this out:
[DMA]("https://help.ubuntu.com/community/DMA")
Let us know. Good luck.

---

### Post by nano -i on 2007-01-06
dma is already enabled for the harddisk.

---

### Post by madmetal on 2007-01-06
well the problem seems to be with modprobe..
i am afraid i know nothing on this..:-k 
i have almost the same system with you and half your boot up time

---

### Post by xyz on 2007-01-06
You may want to try this but I'd be very careful if I were you. You might want to do a backup of your system beforehand.
[HowTo: Speed up ubuntu boot process]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=speed+boot")

---

