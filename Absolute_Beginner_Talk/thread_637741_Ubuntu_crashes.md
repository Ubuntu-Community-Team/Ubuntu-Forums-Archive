---
title: "Ubuntu crashes"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by ChrisB1 on 2007-12-11
Hi,

First, I want to say "Thank You". I'm sure in a forum like this all these noobs, like me, show up and want to know why their system or install is having problems. It looks like a big job. When I get some more experience I will return the favor and help where I can. Right now I have literally zero experience with Linux.

I have just tried out Ubuntu 6.06 on CD. I'm installing it on an older PIII machine.
It needed more memory and I now have 650 megs of ram. Ubuntu is now booting off of CD and loading up fine at first.
After a little while though it will crash, everything just freezes up. It seems to happen when I am moving the mouse pointer or "a deck of cards" or browsing a menu. It also happened when the screen saver tried to load.
Since I don't have it actually installed on my hard drive should I be worrying about this now?

TIA,
CB1

---

### Post by srinv9 on 2007-12-11
I am having something very similar, I could install ubuntu 7.10 fine, but after reboot it doesnt work. I am totally new to linux and hence ubuntu. I get error 16 most of the time while rebooting. anyone help pls

---

### Post by ChrisB1 on 2007-12-11
Good to know I'm not alone.

I should give some background to my problem and machine:

My computer is a 650mhz P111, 650 meg ram, 30 gb hard drive,  Elsa Erasure X (Nvidia) video card and MS USB Optical mouse.

The purpose of the computer is to use as a machine controller while running EMC2. I obtained the Ubuntu 6.06 rel and EMC2 here: [http://www.linuxcnc.org/](http://www.linuxcnc.org/)
I believe that Ubuntu has  Real Time patch applied so as to enable the machine control.

Does that complicate things? :)

CB

---

### Post by ChrisB1 on 2007-12-11
Alright, I guess this is a self service gas station.:) 
Please yell at me if you see me doing something wrong.

Here's the first few steps I am going to take to fix this problem:

1. Do a memory check in GRUB. Since I just installed new memory.
2. Complete the installation from the live CD to my hard drive.
3 Check the video card driver.
4. Create an error log as I saw in another thread. (dmesg> errors.log)

I'm open to other ideas of where to look or what to do.

Thanks,
CB

---

### Post by MONODA on 2007-12-12
how about you try 7.04 or 7.10

---

### Post by rax_m on 2007-12-12
I personally found two things that were causing instability for me on Gutsy: 

1. Compiz-fusion
2. Firefox

so I'm now running metacity (no candy :( ) and swiftfox.. and so far my desktop hasn't crashed in the last 3 days (whereas it was crashing about 2 times a day before that). 

I'm not saying this is necessarily what's causing your issues, but I think a lot of people are having issues with firefox esp. 
Either way, it's worth a try i say ;)

---

### Post by gaelfx on 2007-12-12
My most unprofessional reply is that if you are booting off of the CD, it is likely that this is the problem. Is there anything preventing you from actually installing it on the computer? At least to have a try and see if it is better? It's possible that after installing it and updating the OS (I'm pretty sure that none of the LiveCD versions run the most current updates for any of the distros) that things will run smoothly. But like I said, I'm not a pro, so I have no real reason to believe this other than my own experiences with things like Knoppix not running very well in LiveCD version, though that is largely due to the fact that that harddrive was mangled in one sector where system information was written.

---

### Post by Moop on 2007-12-12
> **ChrisB1 said:**
> Alright, I guess this is a self service gas station.:) 
Please yell at me if you see me doing something wrong.

Here's the first few steps I am going to take to fix this problem:

1. Do a memory check in GRUB. Since I just installed new memory.
2. Complete the installation from the live CD to my hard drive.
3 Check the video card driver.
4. Create an error log as I saw in another thread. (dmesg> errors.log)

I'm open to other ideas of where to look or what to do.

Thanks,
CB

I think you're on the right track in suspecting your memory is causing a problem. You didn't say how many sticks of memory you're using and if it's all the same type and speed. 

Run memtest for a couple passes. If it fails try using  just 2 matching sticks of memory and see what happens.

---

### Post by ChrisB1 on 2007-12-17
Hi All,

Thank you for all of your hints. Here is an update of where I stand:
I have installed Ubuntu on my hard disk. The install went fine. Worked really well. Grub resized my Windows partition and now I have a dual boot machine.
My memory checks out OK. I have a 128 mb stick and 2 - 256 mb sticks; both PC-66 as recommended for my machine.
I still have a problem with the screen locking up. It seems to happen when the screen saver kicks in and also when I have been browsing in Firefox. 
Somehow I need to see what is happening when it crashes. I don't know how to do that yet.
This newbee just learned about Cntrl/Alt/F1.
I got a book on Ubuntu at the library this weekend. Beginning Ubuntu Linux, Keir Thomas, 2006.

Chris

---

### Post by DrMega on 2007-12-17
I've seen this happen, but it was to do with a bug in the drivers for my graphics card. It won't be exactly the same issue for you as my card was a radeon 7000 (Ati).

When you say it freezes, does it freeze forever? Applogies if it sounds silly, but when using the live CD you do get intermittent freeze ups of a few seconds at a time while the CD has to spin up again to be read. I'm guessing that's not it though.

You could try making sure it uses the generic video driver (MESA). Have a look at this thread....

[http://ubuntuforums.org/showthread.php?t=641489]("http://ubuntuforums.org/showthread.php?t=641489")

The only thing is though, as you are running off the LiveCD, obviously you'll have to restart X without fully rebooting (as your xorg.conf is actually in memory rather than on disk).

I would only bother with the above if I had a good reason to stick with 6.06 (Dapper). Gutsy looks nicer and seems to have better hardware detection so my first plan would be try that instead.

---

### Post by ChrisB1 on 2007-12-18
DrMega,

Thank you for the link to your thread on changing video drivers. I didn't know how to do that.
In my case I changed the driver to "vesa" from "nv" (the open source NVidia driver).
That leads me to think that there are errors with the origional driver and my card.
The "vesa" driver has solved the crashing problem though at the expense of some screen resolution.
That's alright since this machine is meant to be a machine controller running a 'real time' patch to the linux kernal and the driver is recommended as not causing problems in the RT processing.
To read more look at [http://www.linuxcnc.org/](http://www.linuxcnc.org/)

Chris

---

