---
title: "Ubuntu on old computer? Completely wiping windows?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by rad2themax on 2005-12-18
OK so i've been playing with the live CD of Ubuntu on my decktop computer but my dad won't let me install it on this computer for now as he uses it for work etc. I know it's safe and i can dual boot so he can run windows XP but he will not be budged, atleast for now. ;) 

So he's given me all the power i like over an old computer to play around an experiment on. This computer is very old however, it has a 2Gb hard drive.

Now i was going to install Ubuntu on this but i figured the only way to have any sort of space is to completely replace the current windows 98 OS with Ubuntu, is this easy/possible? And what's more will it be worth it, as in is 2Gb enough?

My other options is to buy an external hard drive for it, the only probmel is the computer only has USB1.1 so am i right is saying Ubuntu would run very slow if coming from an external hard drive being booted like that? Could i install the OS on the 2Gb internal hard drive and then use the external one for everything else (as in programs, files etc, windows would be gone).

So what do you guys think i should do? Thanks very much for your time,

Max Quinn

---

### Post by doitashimashite on 2005-12-18
Forget about the external hd, at least for putting the O.S. on. You can use it later as an external hd though, to put your files on.

As for the installation, take a look at Xubuntu, which fits better in older hardware.
Another distro which performs very well "on almost nothing" is DSL (Damn Small Linux).

Good luck!

---

### Post by Swab on 2005-12-18
[QUOTE=rad2themax]OK so i've been playing with the live CD of Ubuntu on my decktop computer but my dad won't let me install it on this computer for now as he uses it for work etc. I know it's safe and i can dual boot so he can run windows XP but he will not be budged, atleast for now. ;) 

So he's given me all the power i like over an old computer to play around an experiment on. This computer is very old however, it has a 2Gb hard drive.

Now i was going to install Ubuntu on this but i figured the only way to have any sort of space is to completely replace the current windows 98 OS with Ubuntu, is this easy/possible? And what's more will it be worth it, as in is 2Gb enough?

My other options is to buy an external hard drive for it, the only probmel is the computer only has USB1.1 so am i right is saying Ubuntu would run very slow if coming from an external hard drive being booted like that? Could i install the OS on the 2Gb internal hard drive and then use the external one for everything else (as in programs, files etc, windows would be gone).

So what do you guys think i should do? Thanks very much for your time,

Max Quinn[/QUOTE]


Have you considered [Damn Small Linux]("http://www.damnsmalllinux.org/")? It's very small, works great on old hardware, and it's lots of fun to play around with.

---

### Post by rad2themax on 2005-12-18
Ok thanks very much i'll certianly look into that DSL. 

To doitashimashite though could i run programs from the external hard drive or is that pointless aswell? Also is it easy do completely replace windows with Ubuntu, i've never even installed Ubuntu normally so have no idea.

Thanks fopr the speedy replies, Max.

---

### Post by aysiu on 2005-12-18
If you're intent on putting Ubuntu on, you will *have* to erase Windows 98 (there isn't room for two OSes on a 2 GB hard drive!). Don't worry the Ubuntu installer will do that for you--just select the "erase the entire hard drive" option.

Make sure, though, that you do a server install. The regular install may take up more than 2 GB! Once you do the server install, uncomment the sources ```
sudo nano /etc/apt/sources.list
``` remove all the # signs from before things that look like web addresses, then save (control-x), confirm (y), and exit (Enter). Then, finally ```
sudo apt-get install xubuntu-desktop
```

---

### Post by doitashimashite on 2005-12-18
[QUOTE=rad2themax]Ok thanks very much i'll certianly look into that DSL. 

To doitashimashite though could i run programs from the external hard drive or is that pointless aswell? 
[/QUOTE]

Sure, you could run programs from external hd as well.
The only thing is that it will be slower, depending on the speed of the hd, and the connection type (usb 1.0, 2.0).

---

### Post by rad2themax on 2005-12-18
[QUOTE=doitashimashite]Sure, you could run programs from external hd as well.
The only thing is that it will be slower, depending on the speed of the hd, and the connection type (usb 1.0, 2.0).[/QUOTE]

Yeah that's what i was thinking because it's USB 1.1 (or 1.0 i'll try and find out) what kinda speed hard drive would i need to get things running ok? Also can anyone reccomend any external hard drives bearing in mind that i would like it cheap (sub £50 definately, preferably alot less) and reasonably fast. I would only need around 20Gb memory or even less.

Thanks again, Max.

---

### Post by bscbrit on 2005-12-18
Everything that you have been told so far is good and you can run ubuntu on a 2Gb drive - I do!  But I must confess that I would look for a secondhand 5 - 10 GB drive to play with.  I've managed to pick up some very cheap drives (£10 / $15) from computer shops which sell new computers and sometimes get asked to dispose of the old one.  Or perhaps look at some computer junk sales in your area - if such things exist in your part of the world.

---

### Post by Sef on 2006-01-13
>  Once you do the server install, uncomment the sources 
Code:

sudo nano /etc/apt/sources.list
remove all the # signs from before things that look like web addresses, then save (control-x), confirm (y), and exit (Enter). Then, finally 
Code:

sudo apt-get install xubuntu-desktop

If you get an error message when installing xubuntu, do this first:

```
sudo apt-get update
```

then 

```
sudo apt-get install xubuntu-desktop
```

Link: [http://ubuntuforums.org/showthread.php?t=116031"]http://ubuntuforums.org/showthread.php?t=116031"]http://ubuntuforums.org/showthread.php?t=116031]("http://ubuntuforums.org/showthread.php?t=116031")

---

### Post by AMD64_N_Linux on 2006-01-13
You didnt say what the computer specs are. A little more info might be helpful, but let me say this.

If you have a CD-Rom, you can always download various LiveCD versions of linux to check out. Then there is the aforementioned DSL, and there is Puppy Linux (my daughter loves this one) , and a couple dozen other mini or minimalist distros.

See this page

[http://www.linux.org/dist/index.html]("http://www.linux.org/dist/index.html")

Select your platform and minimalist, ( the language option very seldom matters ) for the little bitty linuxes that run really well on older computers and use little bits of hdd space. Way under 2 GB.

---

### Post by Jimmey on 2006-01-13
I had the same problem. My Dad wouldn't let me install Ubuntu on my laptop. So I sneakily set up a dual boot. Tehehehe.

Good luck with your Dad by the way...

:)

---

### Post by patrick295767 on 2006-01-13
[QUOTE=rad2themax]OK so i've been playing with the live CD of Ubuntu on my decktop computer but my dad won't let me install it on this computer for now as he uses it for work etc. I know it's safe and i can dual boot so he can run windows XP but he will not be budged, atleast for now. ;) 

So he's given me all the power i like over an old computer to play around an experiment on. This computer is very old however, it has a 2Gb hard drive.

Now i was going to install Ubuntu on this but i figured the only way to have any sort of space is to completely replace the current windows 98 OS with Ubuntu, is this easy/possible? And what's more will it be worth it, as in is 2Gb enough?

My other options is to buy an external hard drive for it, the only probmel is the computer only has USB1.1 so am i right is saying Ubuntu would run very slow if coming from an external hard drive being booted like that? Could i install the OS on the 2Gb internal hard drive and then use the external one for everything else (as in programs, files etc, windows would be gone).

So what do you guys think i should do? Thanks very much for your time,

Max Quinn[/QUOTE]
  
How much RAM do you have on this pc ?
  
Greetz'

---

