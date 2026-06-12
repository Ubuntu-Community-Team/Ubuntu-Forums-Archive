---
title: "My first ubuntu install"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by bonecone on 2007-11-08
Hey there,

I'm trying to install Ubuntu-7.10-desktop-amd64.  I've managed to get to the first install screen where I'm presented with several options and the 30 second count down. I press Enter on the first option and then I get the following screen:

*Starting deferred execution scheduler atd                     [OK]
*Starting periodic command scheduler crond                    [OK]
*Checking battery state...                                                [OK]
*Running local boot scripts (/etc/rc.local)                         [OK]

The CD spins for a little while and then stops and nothing else happens. Why am I not getting the graphical setup that I see in the install tutorials?

---

### Post by Dr Small on 2007-11-08
How much ram do you have on your system, and also, what is your video card ?

---

### Post by bonecone on 2007-11-08
I have a gigabyte of RAM and an ATI Radeon Video card

---

### Post by Dr Small on 2007-11-08
is your processor a 64bit ?
Have you checked the md5sums to see if the download was correct ?
Have you checked the cd for errors ?

---

### Post by bonecone on 2007-11-08
Yes to all three.

I also tested the other install options. The one containing the acronym 'OEM' presented a different screen where I was able to enter commands (like help and dir) but still had no idea how to start up the install

---

### Post by Dr Small on 2007-11-08
Hmm. I am stumped.
My other system has a gig of ram, uses ATI card, but isn't a 64bit, and worked fine. Then again, it runs Dapper Drake.

This system here runs 512 of Ram, 64bit CPU, nVidia graphics, and Feisty fawn, and works great...

Maybe you could try an older version, or wait for someone with more knowledge than me :D

Dr Small

---

### Post by bonecone on 2007-11-08
ok, thx

---

### Post by Paul820 on 2007-11-08
Try the alternate cd.

---

### Post by bonecone on 2007-11-09
Alternate CD? What do you mean? I've tested all the different install options and none of them work. They stall.

---

### Post by hyper_ch on 2007-11-09
the Alternate CD is a different install cd :)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

On the bottom you have a checkbox for the alternate cd

---

### Post by thenailedone on 2007-11-09
> **hyper_ch said:**
> the Alternate CD is a different install cd :)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

On the bottom you have a checkbox for the alternate cd

...sorry for thread jack... whats the difference between the two?

---

### Post by Dr Small on 2007-11-09
> **thenailedone said:**
> ...sorry for thread jack... whats the difference between the two?
The alternate cd is a text-based installer only, whereas the regular download is a livecd GUI installer.

Dr Small

---

### Post by xpod on 2007-11-09
The alternate cd is just a text based installer kinda so you dont get the luxury of any live environment to try first.

Much better for installing on less worthy machines although they can also help avoid many initial problems during installation,especially those of a graphical nature.

You can also use them as repositries too.

EDIT:tch...tooo slow xpod

---

### Post by Marc Hoffman on 2007-11-09
The 'normal' cd is a live disk that lets you try out the OS first, whereas the Alternative is used only for installing the OS - but has more options to do so and requires less RAM to run.

I think the original poster is using the alternative disk as he mentioned the option of installing in OEM mode.

---

### Post by Marc Hoffman on 2007-11-09
Have you checked the cd for scratches and smears. Sounds silly but I had a disk that would hang on the installer due to a grubby finger print!

---

### Post by hyper_ch on 2007-11-09
and also the alternate cd is less prone to failures on installation... it's just not as pretty as the desktop one but if you can read and know what "partitions" are then you should be fine.

---

### Post by bithkits on 2007-11-09
Yeah, a bad burn could also cause this. Try burning the install disk again

---

### Post by meindian523 on 2007-11-09
at low speed,preferably,something like 4x should do.....

---

### Post by hyper_ch on 2007-11-09
and you a CD-RW so you don't waste a cd everytime ;)

---

### Post by bonecone on 2007-11-09
I tried the alternate disc and was able to complete the installation. But when the system booted up for the first time and I entered my username and password I was simply taken to a command prompt. How do I get the the GUI?

---

### Post by LowSky on 2007-11-09
type startx

---

### Post by wariola on 2007-11-09
Alternate CD sometime works better than the Live CD. I suggest you give a try. In short alternate CD dont boot into liveCD mode but will automatically run the text installer.

---

