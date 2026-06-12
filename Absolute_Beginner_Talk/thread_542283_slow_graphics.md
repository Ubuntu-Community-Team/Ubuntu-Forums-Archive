---
title: "slow graphics"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by pooper on 2007-09-03
hi all, just wondering graphics are a bit glitchy, like some complex webpages and opening and closing windows etc, why would this be? I can play DVDs and videos from HD fine no problems,  just seems graphics are a bit slow?

---

### Post by skymera on 2007-09-03
mine are like that.
ive ignored it most times.
maybe someone with more knowledge cab be  helpful :D

---

### Post by FuturePilot on 2007-09-03
What's your graphics card? Did you install the 3D accelerated driver?

---

### Post by pooper on 2007-09-03
my graphics card is an ebay job = inno3D Tornado Geforce4 MX agp8x nVidia TV DDR 64MB (ive not tried using the tv out) 
I have tried the 3d graphics driver, restricted driver right ? caused problems, sometimes no graphics at all.

---

### Post by dougfractal on 2007-09-03
was that 
**sudo apt-get install nvidia-glx-legacy**

---

### Post by pooper on 2007-09-10
i dont know, i didnt use terminal it popped up when i installed ubuntu and went desktop effects then asked me to install nvidia restricted driver.... i installed it and restarted but had problems with no display. 

what does that terminal command do then ?

---

### Post by dougfractal on 2007-09-11
the nvidia package is split into 3 groups depend on the age of the card.

 nvidia-glx-legacy   963*
 nvidia-glx        975*
 nvidia-glx-new    104**

I think your card is in the older group.

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by pooper on 2007-09-11
ok i went on the link and found my card > GeForce4 MX 440 with AGP8X 	0x0181   under the 1.0-96xx driver supports list.

what does this mean, sorry im a little confused, what do i type in terminal to install the correct driver, or is it what you have already typed ?

---

### Post by mysticmatrix on 2007-09-11
> **pooper said:**
> ok i went on the link and found my card    under the 1.0-96xx driver supports list.

what does this mean, sorry im a little confused, what do i type in terminal to install the correct driver, or is it what you have already typed ?

You already have correct drivers installed. Ubuntu has done the job!!!. Please don't mess with it. Your problem would be lying somewhere else. One more question,

you are able to run HD on geforce 4 series???:confused:

---

### Post by dougfractal on 2007-09-12
Now I'm confused. Have you typed (copied to) in terminal

> sudo apt-get install nvidia-glx-legacy
If ubuntu has done it's job then this will do no change. 

I have a script that tells me a lot about your system. run it and post the xinfo.tar.gz
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by pooper on 2007-09-12
yeh i ran that terminal command you posted, it did some stuff but i dont know what..
i then saw your next post and went on the link you posted and found my card in that legacy list.

 GeForce4 MX 440 with AGP8X 0x0181
under the 1.0-96xx driver supports list.

I ran the commands you just posted and it made new directory Xinfo with file xinfo.sh inside. I've attatched the file. Sorry I dont know much about terminal and the commands, im learning though :)

---

### Post by skymera on 2007-09-12
> **pooper said:**
> my graphics card is an ebay job = inno3D Tornado Geforce4 MX agp8x nVidia TV DDR 64MB (ive not tried using the tv out) 
I have tried the 3d graphics driver, restricted driver right ? caused problems, sometimes no graphics at all.

that is an old card, very old ram type, ddr, and low RAM.

perhaps upgrade? then wont be sluiggish

---

### Post by pooper on 2007-09-12
yeh but im not doing anything fancy with it. just opening and closing windows can be glitchy ??
I hate to say it but it did work ok in win.xp. Still I'd rather buy a new graphics card when i have the money, rather  than run windows.

---

### Post by skymera on 2007-09-12
i had a crap card that worked fine in XP and not in ubuntu.
slow grpahics, freeezing, couldnt even run beryl.

but i upgraded, nvidia, and worked BETTER trhan XP.

some 128mb nvidia cards are dirt cheap now!

trey..
[www.ebuyer.com](www.ebuyer.com)

if you want a decent card.
go for a 512mb GDDR3 card :D DX9 £150+

if you want ultra good: 768mb GDDR3 :D DX10/OpenGL2.1 £240+

if you want unbelievable prices: ATI 2GB!! GDDR4 DX10/OpenGL2.1 £?? 
OR a OpenGL 3.0 card,nvidia got one for $18,000 lol

few optuons

---

### Post by pooper on 2007-09-12
yeh i see what your saying, i had to change my old old graphics card to this one to stop ubuntu from freezing. That one was some thing like 8mb ram 4x. I've not even tried beryl as ubuntu alone is glitchy graphics atm.. I'll consider buying one when student loan comes \\:D/

---

### Post by skymera on 2007-09-12
i upgraded, only to a 512mb 7900GS, 512mb, i made sure it was DDR3 :D

and i can run fusion with everything and run games :D

i would consider it

---

### Post by dougfractal on 2007-09-12
> **pooper said:**
> yeh i ran that terminal command you posted, it did some stuff but i dont know what..
i then saw your next post and went on the link you posted and found my card in that legacy list.

 GeForce4 MX 440 with AGP8X 0x0181
under the 1.0-96xx driver supports list.

I ran the commands you just posted and it made new directory Xinfo with file xinfo.sh inside. I've attatched the file. Sorry I dont know much about terminal and the commands, im learning though :)


xinfo.sh  is a script like a windows .bat (batch) file

run it again.
```
cd ~/Xinfo
./xinfo.sh

```
and post the xxxxxinfo.tar.gz  file (like a zip) that it makes
[I]
some guy once asked "how do i run a linux .exe file?   A. linux uses permissions to allow a file to 'run', ie chmod +x <name of file>". The extension .sh isn't for linux, it's for the user to easily see that it's a shell script[/I]  

I've used a nvidia 440mx 64mb and not had your issues.

---

### Post by pooper on 2007-09-12
ok hows this, it came up with some errors in terminal though.

---

### Post by dougfractal on 2007-09-13
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nv
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

[ctrl+alt+backspace]   restartX

**notes:**
Ubuntu legacy is for "old legacy"  geforce 2
your xorg.conf driver is "nv" rather than "nvidia"

the above script  should sort you out ;-)


**If it goes wrong**(blue screen)
[I][ctrl+alt+F1]
login
sudo cp /etc/X11/xorg.conf.nv /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart[/I]

---

### Post by pooper on 2007-09-24
sorry for being so long with a reply, but it didn't work :confused:
I've just got ubuntu back up and running.

---

### Post by dougfractal on 2007-09-24
> sudo apt-get upgrade
sudo synaptic 

use synaptic to seach for nvidia
select **nvidia-glx-legacy**
also check for restricted modules

> sudo sed -i -e 's/"nv"/"nvidia/" /etc/X11/xorg.conf

restartx



Your card is geforce 4  from lspci   but  "geforce2 Ti" from Xorg.0.log  

This is posible to fix and run well ;-)  (ish)

---

### Post by pooper on 2007-10-02
):P me again. Just to let you know, followed the instructions and having no problems, although i dont think its made much difference performance wise so maybe a new card is in order. I.ve also been fiddling about with kubuntu, it seems to run a bit better, unless im just fooled by its good looks !

anyway thanks all

---

