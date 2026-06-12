---
title: "Ubuntu on a laptop"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by StephanGFX on 2007-08-16
I want to dual boot Ubuntu 7.04 on my laptop with vista basic. But I have some questions that I need cleared up before I start.

1. How much space do I need to install Ubuntu?
2. I use a touchpad, so will Ubuntu automatically detect that and let me use it? Or do I have to install separate software for that?
3. Will it show me how much battery I have left? Vista does that for me in my bottom right toolbar. 
4. Whats the difference between Kubuntu, Xubuntu, and Ubuntu? Which one is more laptop friendly? 
5. Is Ubuntu more friendly on my battery then Vista?  
6. My main partition(C:/) is almost full. Can I use my (D:/) partition to install Ubuntu? 
7. I have a recovery console on a "hidden" partition. How can I make sure that I don't lose that when I install ubuntu? 

I'm on an Acer Aspire 3680 Notebook pc. I have 512Mb or RAM. And 2 HDD (C:/ and D:/) that both hold 30 gigs each. 

Thanks to anyone who answers all these questions for me XD

:lolflag:

---

### Post by Hobo Joe on 2007-08-16
> **StephanGFX said:**
> I want to dual boot Ubuntu 7.04 on my laptop with vista basic. But I have some questions that I need cleared up before I start.

1. How much space do I need to install Ubuntu?
2. I use a touchpad, so will Ubuntu automatically detect that and let me use it? Or do I have to install separate software for that?
3. Will it show me how much battery I have left? Vista does that for me in my bottom right toolbar. 
4. Whats the difference between Kubuntu, Xubuntu, and Ubuntu? Which one is more laptop friendly? 
5. Is Ubuntu more friendly on my battery then Vista?  
6. My main partition(C:/) is almost full. Can I use my (D:/) partition to install Ubuntu? 
7. I have a recovery console on a "hidden" partition. How can I make sure that I don't lose that when I install ubuntu? 

I'm on an Acer Aspire 3680 Notebook pc. I have 512Mb or RAM. And 2 HDD (C:/ and D:/) that both hold 30 gigs each. 

Thanks to anyone who answers all these questions for me XD

:lolflag:

1. I'd say somewhere between 3 and 4 GB, but that's with pretty much no data on it, if you want to put a lot of data on there, increase accordingly.

2. Yes, it will detect you touchpad.

3. Yes, it will show you the battery life.

4. Ubuntu is the main one, Kubuntu is just a version of Ubuntu with a different set of apps and a different look.

5. I don't really know, I've had little experience with Ubuntu on laptops. I assume it's about the same, depending on what you are doing. If you have have nothing big running, it will be about the same, maybe less, but if you run something like Beryl(desktop effects) then it will suck battery really fast.

6. Yes, how big is it though, and what is on it?

7. Yes.

Hope that answers you questions. :)

---

### Post by amazingtaters on 2007-08-16
1. I'd give Ubuntu at least 8 or 10 gigs.
2. Touchpad will be auto detected and work fine.
3. Yessir, it does with my Acer
4. Kubuntu is ubuntu with the KDE deskop, Ubuntu uses GNOME, and Xubuntu uses XFCE. Basically, different GUI's same OS.
5. In my experience yes (vista is a resource hog, ubuntu less so)
6. You will need to do some repartitioning as you cannot install Ubuntu on an NTFS partition.
7. What do you mean by a hidden partition? Like, it's not mounted in windows? If so, then it will still be detected when you are creating a partition for ubuntu. Perhaps you can elaborate on this point.

---

### Post by hyper_ch on 2007-08-16
1.) Well, an Ubuntu install will you at least 2 GB.... about 1.5 GB for the system and for you another 512mb as swap... but more would be definitively better...

2.) Download the Desktop-CD and test it out what works and what doesn't... you will need to set your bios to boot from the cd as first boot device... when the ubuntu startup screen comes it says "start or install ubuntu" --> nothing will be installed if you select that... it will just load ubuntu totally from cd and will give you a look what ubuntu is like... if you like it, you can then install it from the gui.

3.) There are desklets that show you your battery status

4.) They feature different Desktops... generally Kubuntu (KDE) is considered the most windows-like but also heaviest... Ubuntu (Gnome) is lighter (but not much) and Xfce is, compared to the other two, very light.... for your specs I'd go either for Ubuntu or xubuntu but you can install each desktop afterwards... that's nor problem....

5.) no clue

6.) well, you will need to unpartition space first ;) either shrink you d: drive partition and leave some of it unpartitioned or delete it completely... ubuntu has no problems with that... it will overwrite your masterboot sector and install grub there... grub will enable you to select at startup to run windows or linux but it will not damage the system... however before shrinking or deleting partitons MAKE A BACKUP!!!! Just to be on the safe side!

7.) It's only hidden in windows. The ubuntu installer should see it... so either select as option "use largest continuous free space" or go for the manual partition (which I recommend) and just make sure you select the right unpartitioned space.... the hidden partition should be labelled as partition ;)

---

### Post by Lord Illidan on 2007-08-16
> 1. How much space do I need to install Ubuntu?

It's all relative. You might want to devote the entire D: disk to Ubuntu, or else resize it. 2-10 gigs seems ok, but a bit short.

>  2. I use a touchpad, so will Ubuntu automatically detect that and let me use it? Or do I have to install separate software for that? 

If it is compatible, yes it should work out of the box..

>  3. Will it show me how much battery I have left? Vista does that for me in my bottom right toolbar. 

Yes it will. Sometimes it can give strange displays though..my dad's laptop (Sony) does that sometimes.

>  4. Whats the difference between Kubuntu, Xubuntu, and Ubuntu? Which one is more laptop friendly?

I'd use Ubuntu...Xubuntu is faster...but Ubuntu has more power saving apps, I think..not so sure about Kubuntu.

 
>  5. Is Ubuntu more friendly on my battery then Vista?  

Not sure how to answer that. Power management and all that stuff. Personally, I didn't use Vista on this laptop for more than 1 hr (pre-installed with it, and wiped it for Ubuntu).


>  6. My main partition(C:/) is almost full. Can I use my (D:/) partition to install Ubuntu? 

Yes of course. Keep in mind that Linux does not recognise harddrives or any kind of devices as C:/ or D:/

>  7. I have a recovery console on a "hidden" partition. How can I make sure that I don't lose that when I install ubuntu? 

The partition will show up in the installation screen. Make sure you don't format it by accident..but then it is pretty hard to do so, unless you're a right down n00b :lolflag: or doing it deliberately. In any case, you can use the live-cd, and send us a screenshot when you arrive at that stage.

---

### Post by StephanGFX on 2007-08-16
i have 30 gigs left on my other partition(D:/) 

so will it let me select that partition to install to when I install ubuntu?

And my recovery partition is called a hidden partition from what I've read. most computers have them.

Oh and what do you mean by:

```
6. You will need to do some repartitioning as you cannot install Ubuntu on an NTFS partition.
```

---

### Post by hyper_ch on 2007-08-16
Have a read here:  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Lord Illidan on 2007-08-16
I'd also use Vista to resize Vista made partitions..I heard somewhere that doing it with Linux can crap it up, and indeed, when I resized Vista's partition on this laptop, it refused to boot anymore..so just keep that in mind. It can handle XP made partitions no problem though.

---

### Post by StephanGFX on 2007-08-16
ok i'm going to load it up and make some screens.

---

### Post by sarabulho on 2007-11-13
I finally was able to install Xubuntu on Vaio, after trying several different distros. Vaio's are usually unfriendly to non-shiped OS's, mainly due to graphic issues. But the latest Xubuntu (7.10) was a breeze and to my awe even detected and installed wi-fi, which is really something, isn't it?.
I'm  still  looking for a battery life meter(desklet, they call it?) and yes, it drains my battery faster than any Vista version with all its sucking power on. Also the fan is on all over linux sessions, so I suspect that there is no CPU trothling, so it works at full processing power even when idle, which is not a good thing from a laptop viewpoint. So I would like to ask if there is, and how to implement, a power-saving scheme o Xubuntu ?
I love the XFCE gui and i need to run gcc to do my homework.
Thank you all. :confused:

---

