---
title: "64 vs 32 bit Kubuntu"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by wasing on 2008-01-01
kk i have a AMD 64 X2 Proccesor and am currently using the Kubuntu 64 bit version but it seems that the 64 bit version requires allot of work to get a majority of my things to work and still not have gotten to work...

so my question is should i switch back to 32 bit. and if so how much will it effect my performance or environment.. 

btw im a complete noob to linux still but im still presistant in learning 

thx for the help ubuntu community (again):KS

---

### Post by PmDematagoda on 2008-01-01
What problems are you having with Kubuntu X64?

---

### Post by wasing on 2008-01-01
- Sound Driver for Realtec A66
- Beta driver for HVR-1600
- Adobe flash pluggin

- also havin a hard to with konole comands but that more of a personal error thing i believe

also for the Realtec driver it only comes in 32 bit i belive and for the adobe i went to add or remove programs and installed the macromedia flash pluggin for firefox but still no flash playing. no flash in konqoeror either. 

im not really good at all at using the terminal or changing script to make things work. cause im a noob

---

### Post by wasing on 2008-01-01
kk i really wanted to know this before i wasted a Cd and installed kubuntu 32 bit but i think that what i may have to do to get the beta driver to work

if anyone else can help me decide im gonna burn the disc for 32 bit in about 10 mins but i truely think it wont effect preformance that much unless i loose the abilty to use my second core but i dont think that will happen but again i have no idea.. 

thx again

---

### Post by Pethegreat on 2008-01-01
I managed to get flash working in 64 bit Ubuntu. I used a program called quickstart. I simply had to remove all my previous flash and gnash files using synaptic before running it. 

Quickstart can be found here:
[http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart](http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart)

Now you will need to get some files so that you can run 32 bit software. In the terminal enter 
```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
```
since you are using a sudo(super user do) command, it will ask for your password. Once you entered your password it will download and install the files automatically. 

64 bit operating systems can address several petabytes of ram(?). They also do a faster job with ripping/converting media.

---

### Post by wasing on 2008-01-01
kk thank you for the post i have booked marked that site  in case i wish to visit that in the future version of kubuntu 8.04.. i think i am going to switch over to 32 bit in order to get these drivers working properly.. thanks for the post.

---

### Post by radi0j0hn on 2008-01-01
"Now you will need to get some files so that you can run 32 bit software. In the terminal enter
Code:

sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0"

What are these packages and what do they do?


Once they are loaded, what else do I have to do to run 32 bit packages on my 64 bit system?

Thanks!  John

PS:

If I do wish to revert back to THE 32 BIT SYSTEM, and I am sharing the drive with VISTA, what must I do?

Thanks again!

John

---

### Post by Pethegreat on 2008-01-01
> What are these packages and what do they do?


Once they are loaded, what else do I have to do to run 32 bit packages on my 64 bit system?
Packages are bundles of files that allow you to do certain things. I may be off, so ask someone who knows Linux better. 

As far as I know, flash is the only thing you would need the package for. Everything else I have done to date has a 64bit version of the files. 

I want to know if anyone else has tried the method I listed to get flash working. Certain things work for some people, and they don't work for other people.

---

### Post by g2g591 on 2008-01-01
java is another thing not available for 64 bit, as far as I could tell, when I ran 64 bit debian, there was no noticable performance gain or loss. (athlon 64, x1)

---

