---
title: "Very slow 7.10 operation"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by anoctothorpe on 2008-03-29
To preface, I am completely new to the world of Ubuntu. I was able to install the 7.10 on an older desktop 
(alternate cd install), but I am running into some major issues with sluggish loading of various programs. I'm talking minutes to open the pull down "Applications"
For the record, I am attempting to run this on the following system:

Pentium 4 -  2.4GHz
256 mb RAM
Intel D865GLC motherboard with on-board graphics & sound

If I were to take a guess, I would say that maybe it is a graphics issue because even the mouse as I move it on screen skips as if it is struggling to keep up with the actual movements. Could this be a driver problem? The reason I am unsure is that once linux did load, it displayed the correct 1280x768 resolution of my monitor and not just vga. Is there some other obvious thing about my setup that I might be missing?

 Any advice/help on this issue would be greatly appreciated

-anoctothorpe

---

### Post by indiana_crook on 2008-03-29
I'm no genius at this either.  I've only been using ubuntu for about a month now.  I thought that 7.10 was designed for dual core processors...

---

### Post by stefangr1 on 2008-03-29
Ubuntu 7.10 is not specifically meant for dual core processors, and even though you're a little low on RAM, it should run fine on your system (I occasionally use a PIII@1000Mhz laptop with 256mb ram with it, and that also works).

Can you maybe post which processes are running, and how much percent of your system is idle (when you have no programs running)?

And maybe how much time it costs to start some programs:
You can do that in the commandline running the commands below, and then post the results:

time oowriter
time firefox

---

### Post by anoctothorpe on 2008-03-29
Here's the thing, I am not running any processes (at least not any that did not initiate during start-up). When I try to load firefox, it takes over a  couple minute to load. How would I check the actual pc usage? However since everything is so deathly slow, I fear that even simple system checks will take ages.

---

### Post by ghost_ryder35 on 2008-03-29
go to the terminal and type 
```
top
```
and post the results here

Also, if you have Desktop Effects turned on (ie. Compiz) turn it off, this will hog CPU and graphics processing.

---

### Post by stefangr1 on 2008-03-29
> **ghost_ryder35 said:**
> go to the terminal and type 
```
top
```
and post the results here

Also, if you have Desktop Effects turned on (ie. Compiz) turn it off, this will hog CPU and graphics processing.

And you can find the terminal via the menu bar under:

Applications -> Accessories -> Terminal

---

### Post by anoctothorpe on 2008-03-29
I think I know how to theoretically get to the terminal, however the time it is taking me to get there is pretty crazy. The "Applications" pull down has taken over 5 minutes to open (and I am still not there).
The only program that I have opened succesfully since install was one of the pre installed games and even that took forever to load.

Thanks for bearing with my slow computer
-anoctothorpe

---

### Post by ghost_ryder35 on 2008-03-29
i think you may have failing hardware (possibly hard drive or ram) and or a very corrupt install.

---

### Post by anoctothorpe on 2008-03-29
I had worried as much. I will attempt to install it again. I think my hardware is ok because just this morning it was running windows xp pro fine as far as I could tell. Could the reason that it is corrupt have anything to do with the way i partitioned the drive?

---

### Post by ghost_ryder35 on 2008-03-29
> **anoctothorpe said:**
> I had worried as much. I will attempt to install it again. I think my hardware is ok because just this morning it was running windows xp pro fine as far as I could tell. Could the reason that it is corrupt have anything to do with the way i partitioned the drive?yes,  depending on where your swap partition is located, that could contribute to slow performance, but not 5 minutes to open menu's bad

---

### Post by anoctothorpe on 2008-03-29
Maybe the lack of a swap partition was my issue? also, i assume that the EXT2 file format is ok

---

### Post by stefangr1 on 2008-03-29
Yes, if you really have no swap partition (but you should have one if you used the default options to install) the computer gets very very slow if the memory is full. And it gets full quickly since you have only 256mb. But it's kinda difficult to tell without further information.

Maybe doing another install (be sure to back up all important files) is the easiest way in your case.

If you decide to do that, be sure to test the cd before you start installing (one of the options in the bootup screen), and define at least 500mb or so as swap space.

EDIT: The default format that is used by Ubuntu is ext3, it's better to use that if you reinstall, but I don't think it's the cause of your problem.

---

### Post by tad1073 on 2008-03-29
I would format as ext3 which is the most common format.

---

### Post by anoctothorpe on 2008-03-29
OK i think we might me coming closer to the problem. For whatever reason there was no swap partition. I manually set-up a 10gb root partition (EXT3) and a 500mb swap partition and am in the process of installing again. I will let you all know how this goes

-anoctothorpe

---

### Post by anoctothorpe on 2008-03-29
Well that certainly helped things. That swap partition sped things up remarkably
Thank you to everyone for your advice

---

