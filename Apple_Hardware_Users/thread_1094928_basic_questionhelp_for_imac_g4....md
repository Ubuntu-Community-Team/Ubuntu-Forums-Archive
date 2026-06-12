---
title: "basic question/help for imac g4..."
date: 2009-03-13
forum: Apple Hardware Users
---

### Post by moore.bryan on 2009-03-13
i inherited an imac g4, immediately installed ubuntu, and was quite surprised to find how slow it ran... even when i installed openbox and used that as my wm. i did a little digging and found the factory specs for memory were quite light: 128/256; 128mb "internal" memory and 256mb "user switchable" memory. i immediately began a search for the appropriate memory and a friend in a tech department found me 512/512 of the correct memory.

i installed the memory and things sped-up some, but not nearly what i expected. while checking out system usage, i noticed the cpu is almost always pinned at 100% and memory usage almost always under 15%.

now, i'm no hardware/software expert, but shouldn't there be a way for me to tell ubuntu to use more of the memory to ease the strain on the cpu?

thanks for your help, in-advance!

---

### Post by komputes on 2009-03-14
Hmmm, interesting. Can you possibly boot the computer up, open a fullscreen terminal window and upload a screenshot after running the following command:
```

$ top
```

---

### Post by karimone on 2009-03-14
Find the specifications of your iMac [here]("http://mactracker.dreamhosters.com/")
Than buy more RAM. You can take a look to [crucial]("http://www.crucial.com")

Anyway the iMac G4 is a good machine. Which version of Ubuntu PPC you have installed?

---

### Post by moore.bryan on 2009-03-16
> **komputes said:**
> Hmmm, interesting. Can you possibly boot the computer up, open a fullscreen terminal window and upload a screenshot after running the following command:
```

$ top
```
running top showed me the memory info displayed in the xfce panel was incorrect; apparently i'm using almost all my memory even though the xfce panel icons keeps it under 25% at all times. strange?

> **karimone said:**
> Find the specifications of your iMac [here]("http://mactracker.dreamhosters.com/")
Than buy more RAM. You can take a look to [crucial]("http://www.crucial.com")

Anyway the iMac G4 is a good machine. Which version of Ubuntu PPC you have installed?
i invested in more ram as soon as things were as slow as they were and am now maxed-out at 1gb. i've installed intrepid, but not so happy with the ppc processor; it doesn't seem to be "powerful" in any way.

---

### Post by karimone on 2009-03-16
> i invested in more ram as soon as things were as slow as they were and am now maxed-out at 1gb. i've installed intrepid, but not so happy with the ppc processor; it doesn't seem to be "powerful" in any way.

Could you post the specifications of your computer?

---

### Post by moore.bryan on 2009-03-16
> **karimone said:**
> Could you post the specifications of your computer?
[http://lowendmac.com/imacs/15in-imac-g4-700-800-mhz.html](http://lowendmac.com/imacs/15in-imac-g4-700-800-mhz.html)

---

### Post by karimone on 2009-03-16
> **moore.bryan said:**
> [http://lowendmac.com/imacs/15in-imac-g4-700-800-mhz.html](http://lowendmac.com/imacs/15in-imac-g4-700-800-mhz.html)

Did you try xubuntu? Maybe is better that you try also Tiger osx to see if the problem is the software or the hardware..

---

### Post by moore.bryan on 2009-03-16
> **karimone said:**
> Did you try xubuntu?
yeah, as soon as ubuntu ran as slow as it did i tried-out xfce, flux, openbox with very little change.
> **karimone said:**
> Maybe is better that you try also Tiger osx to see if the problem is the software or the hardware..
i went back into osx as well and there was no real speed difference.

---

### Post by karimone on 2009-03-16
Really strange. Did you try something like "puppy linux"?
[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by moore.bryan on 2009-03-16
unfortunately, puppy doesn't have a ppc version. :-(

---

### Post by karimone on 2009-03-16
> **moore.bryan said:**
> unfortunately, puppy doesn't have a ppc version. :-(

The causes of the low speediness of your computer could be various. Try to recompile the kernel optimized of your hardware.

I have a MacMini 1.42 PPC with 512MB of ram and I use just with bash and no gui.

---

### Post by mkvnmtr on 2009-03-16
I have a G4 Ibook. I seldom use more than 512Mb of ram. In fact I find that is enough on most older systems to run Ubuntu with very little swap usage. The high cpu usage makes me think you have a problem with software. You need to find what is using your cpu and deal with that. You can do it with top but I like to install Htop. I have found that Firefox can use a lot of resources if you don't have ad blocker and no script installed. I have also found some kind or root audit process that was using a lot of cpu. That problem seems to have passed and I don't see it now. Maybe updates fixed it.
One thing I do when I install is remove everything I don't use like Evolution, Ekiga and compiz. I found a lot of compiz features work on my ppc but it was resource intensive and not something that mattered to me.
You really should not have a slow machine with Ubuntu but it might take a little work to find the problem.

---

### Post by karimone on 2009-03-16
CPU[||                        2.6%]     Tasks: 67 total, 1 running
  Mem[|||||||||||||||||||||150/502MB]     Load average: 0.03 0.07 0.03 
  Swp[|                     2/1470MB]     Uptime: 18 days, 02:20:18

On MacMini G4@1.42Ghz 512ram

---

### Post by PhirePhly on 2009-03-16
> **moore.bryan said:**
> running top showed me the memory info displayed in the xfce panel was incorrect; apparently i'm using almost all my memory even though the xfce panel icons keeps it under 25% at all times. strange?

Not at all. 25% of it is used for real data, where the rest of it is used for caching stuff from the hard drive (it's called cached in top).  As soon as the RAM is needed, the cached data is dropped, so it's not real usage.  

What we're more interested in is the load averages and what process is eating the lion share's of it. Thus asking for the screen shot of it.

---

### Post by jamesey on 2009-03-17
is compiz off?

---

### Post by moore.bryan on 2009-03-17
first-off, thanks to everyone for the help!

> **karimone said:**
> The causes of the low speediness of your computer could be various. Try to recompile the kernel optimized of your hardware.
i've considered doing this, but don't have the time right now. i do believe this might be my best/only option.

> **mkvnmtr said:**
> The high cpu usage makes me think you have a problem with software.
software where?
> **mkvnmtr said:**
> You need to find what is using your cpu and deal with that. You can do it with top but I like to install Htop. I have found that Firefox can use a lot of resources if you don't have ad blocker and no script installed. I have also found some kind or root audit process that was using a lot of cpu. That problem seems to have passed and I don't see it now. Maybe updates fixed it.
One thing I do when I install is remove everything I don't use like Evolution, Ekiga and compiz. I found a lot of compiz features work on my ppc but it was resource intensive and not something that mattered to me.
i find if i have just two programs open, things stick to a crawl at best. i've already uninstalled almost everything but the most basic of things...
> **PhirePhly said:**
> Not at all. 25% of it is used for real data, where the rest of it is used for caching stuff from the hard drive (it's called cached in top).  As soon as the RAM is needed, the cached data is dropped, so it's not real usage.
even though it shows cached as one number and ram as another and ram is spiked? 
> **PhirePhly said:**
> What we're more interested in is the load averages and what process is eating the lion share's of it. Thus asking for the screen shot of it.
got it... i'll get that up as soon as i can.
> **jamesey said:**
> is compiz off?
compiz is not even installed.

i think i may settle-on installing the debian base system and building off that. i've also grabbed an arch disk to try-out and see if it's any speedier. i found it very strange how drastically slow the machine was.

once again, thanks for all the input!

---

### Post by moore.bryan on 2009-03-18
htop screenshot...

---

### Post by tiresia on 2009-03-18
It looks like X is thanking a lot of power. Most probably you need to reconfigure it.
The easiest solution would be to install an earlier version of X (I would go with Debian Etch - 4), get a configured xorg.conf, back up it, and then install whatever you like using that file xorg.conf as starting point.

It would interesting installing Debian Etch with xfce
[http://wiki.debian.org/Xfce](http://wiki.debian.org/Xfce)

---

### Post by moore.bryan on 2009-03-18
i found that strange, too... i'm, hopefully, going to have a chance to play a little tonight. damn work keeps getting in the way.
:-)

---

### Post by karimone on 2009-03-18
Try to use only the shell and take a look at htop.

---

### Post by moore.bryan on 2009-03-19
alright, here's an "official" update...

i attempted to install debian's base (lenny), everything seemed to progress fine; that is, until i tried to boot the system and was greeted by a message gdm/xserver received signal 11 and couldn't load. reconfiguring the xserver didn't help and so i think i'm going to have to try the debian's "expert" install and specifically change certain things.

---

### Post by moore.bryan on 2009-03-21
i finally found success, through many xorg issues, by installing debian lenny base and adding-on xfce. i must say, it is surprisingly fast... incredibly faster than before. thanks for all of you for your contributions!

---

