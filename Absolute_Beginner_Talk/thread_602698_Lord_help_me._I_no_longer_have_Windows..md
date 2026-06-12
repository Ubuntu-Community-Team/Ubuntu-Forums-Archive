---
title: "Lord help me. I no longer have Windows."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by SomeGuyDude on 2007-11-04
Welp, it's been done.

I had Gutsy on dual-boot with Vista, and then decided to play with GParted and resize my partitions. I initially had 10G for Linux (I only planned on puttering around with it), and then the remaining ~90-ish for Vista and 7 for recovery (HP).

Well, I totally borked everything and had that Error 17 thing going, and since I had everything backed up, I decided to say hell with it and just formatted my HD and put Ubuntu on as my only OS. I'll tell ya, this is a big step for me. I haven't had a machine without Windows on it since... about... 1995.

One thing though. I have a 120GB HD. For some reason I only have 105 actually showing up. Allowing the 1000/1024 thing, that's 111. I couldn't have a six gig swap could I? When I installed, I just let it run with the "use entire disk" thing.

---

### Post by Pumalite on 2007-11-04
Hello:
How are you doing with your new installation? Welcome.

---

### Post by Rinzwind on 2007-11-04
Well SGD you'll be fine. Perfectly fine.

If you really need it install VirtualBox and install Windows inside that :)

---

### Post by Fred_E _krugar on 2007-11-04
Well I have 6 40gigs and each one say that they are only 35gig each , so that sounds about par for yours.

---

### Post by carlosjuero on 2007-11-04
> **SomeGuyDude said:**
> Welp, it's been done.

I had Gutsy on dual-boot with Vista, and then decided to play with GParted and resize my partitions. I initially had 10G for Linux (I only planned on puttering around with it), and then the remaining ~90-ish for Vista and 7 for recovery (HP).

Well, I totally borked everything and had that Error 17 thing going, and since I had everything backed up, I decided to say hell with it and just formatted my HD and put Ubuntu on as my only OS. I'll tell ya, this is a big step for me. I haven't had a machine without Windows on it since... about... 1995.

One thing though. I have a 120GB HD. For some reason I only have 105 actually showing up. Allowing the 1000/1024 thing, that's 111. I couldn't have a six gig swap could I? When I installed, I just let it run with the "use entire disk" thing.
How much main memory do you have? it is possible you have a 6GB swap, I have 3GB RAM and I have a 2GB swap that Ubuntu chose by itself, it bases it on the amount of ram in the system if I recall rightly.

---

### Post by Glowing Fish on 2007-11-04
About the harddrive, what tool are you using to find out usage?

Some of the space could be used by filesystems other than the main one. Along with Swap,Ubuntu keeps a couple other harddrives for different purposes. I believed that the directory with bootable kernels was a separate filesystem, but looking at my system now,I can't tell if that is still the case.

---

### Post by Cool Surfer on 2007-11-04
Welcome to the gang friend :)
We all love windows, but love free licensed to you products like ubuntu more.

I think you will do fine if you have your backups. I feel the need for windows sometimes, when I look for advanced effects of MS office power point

---

### Post by SomeGuyDude on 2007-11-04
Thanks for the warm welcome! I've been messing around with Linux on the side for a few years now, but never as my main OS. Mostly since I couldn't configure it to work with my graphics card or wireless. I tried the Gutsy live CD and bam. Perfection. For the past week I've been workin' with it, and now when my HD dies, I put that on instead of Windows. Huzzah!

Rinz, I have Wine at the moment. Everyone mentions VirtualBox, though, is there a reason that seems to be preferred over Wine?

Carlos, just 2GB of RAM. It's an HP laptop, nothing amazing. I guess it seems to add up around right when you factor in the 1000 or 1024 thingy.

Fish, I'm just using the System -> computer, and then clicking on properties for filesystem. Says 105.something GB total.

What's hilarious is that I never complained about Vista while I had it. No it wasn't lightning but it was great to me, and then I worked with Gutsy for a week. Aside from just ADORING the compiz/AWN eye candy it gives me, I was AMAZED at how much slower Vista seemed when I switched back after not using it for a few days.

I still like Vista, but I can't imagine I'll go back to it unless something very, very specific comes up. I don't edit video or graphics to that level, GIMP is plenty.

---

### Post by floke on 2007-11-04
sudo fdisk -l 

will list your partitions

---

### Post by HermanAB on 2007-11-04
BTW, make yourself a BartPE disk for debugging Windoze issues when you don't have Windoze:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by SomeGuyDude on 2007-11-04
> **floke said:**
> sudo fdisk -l 

will list your partitions

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6125db67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

```

What's this tellin' me?

---

### Post by mdpalow on 2007-11-04
Wine is pretty limited and when you can get something to work in it, it looks like crap and is a little buggy. When you install VMware - you're essentially installing your Win XP or Vista into your Ubuntu and running Windows in a Virtual Terminal when you want/need it. Since the full OS is installed, everything works like it should; unlike with Wine.

I use VMware to run a few programs that aren't yet matched with Linux software (i.e. Photoshop and Dreamweaver. Anyone else reading this please don't reply with Gimp and Kompozer comments.

There's a great 'howto' on installing VMware; just do a search for it or look for it in the Tutorial section...

Good luck..

---

### Post by Casual Fan on 2007-11-04
I became a Linux user the same way--screwed up my Vista install trying to dual boot on my laptop. No regrets. It's great being able to set up my system *my* way.

Still have XP on the desktop, though.:)

---

### Post by SomeGuyDude on 2007-11-04
> **Casual Fan said:**
> I became a Linux user the same way--screwed up my Vista install trying to dual boot on my laptop. No regrets. It's great being able to set up my system *my* way.

Still have XP on the desktop, though.:)

Hah, fun ain't it? I don't have a second computer, though, so this is a whole pile of "I hope this works!"

Although like I said, I haven't really needed Windows at all. I suppose since people live without Windows pretty much in perpetuity then why in the world do I think I'm gonna be the one guy who literally "needs" Windows installed somewhere? :rolleyes:

mdpalow, sounds good. I'll take a look. Wine just seemed easier thanks to not actually being an emulator (isn't the point to not have Windows any more? Kidding!), but then I may want to use Word 2007 or something like that.

---

### Post by Stikky on 2007-11-04
> **Casual Fan said:**
> I became a Linux user the same way--screwed up my Vista install trying to dual boot on my laptop. No regrets. It's great being able to set up my system *my* way.

Still have XP on the desktop, though.:)

Haha, this was pretty much my situation exactly, as well, I kind of had Ubuntu thrust on me when my lappie spazzed out and the Ubuntu install wiped my HD without me asking it to, which annoyed me. I had backed up most of my stuff but after it happened, I realized I had lost a load of videos which is disappointing but I'll survive, I guess.

I still have XP on my desktop but, for some reason, XP freezes sometimes on my desktop and just will not respond, I have to hit the reset button and it takes ages to boot so I am using that one less and less.. I still have XP on my work computer (obviously, cuz I can't change the OS of my work comp, plus I use a lot of windows based simulation programs at work as I am an undergraduate process engineer.. Also I use XP computers at uni for that kind of stuff) so most of my computing life is still Windows based but I am getting used to Linux, slowly :p

---

### Post by SomeGuyDude on 2007-11-05
> **Stikky said:**
> I still have XP on my desktop but, for some reason, XP freezes sometimes on my desktop and just will not respond, I have to hit the reset button and it takes ages to boot so I am using that one less and less.. 

It's funny, my family is pretty tech-ish. Everyone has a notebook of their own, when I visit the fam there's always a lovely clusterbomb with all of us fighting for outlets to plug in.

So naturally we're always mucking around with our computers and whatnot, and since I made this switch, I keep wanting to answer every issue with "Y'know I don't have that problem at all." I went from being the guy that went "shut up, Linux isn't compatible with anything and it's a pain in the ***" to "if you'd convert to Linux you wouldn't have that problem."

---

### Post by Can+~ on 2007-11-05
Welcome to the penguin side :KS.

Is it a notebook? Maybe it has some pre-made partitions on it.

An alternative title for this post would have been: "LOOK MA, NO WINDOWS!"

---

### Post by jaybombalous on 2007-11-05
I haven't had windows for over a year. You will do just fine!

---

### Post by SomeGuyDude on 2007-11-05
> **Can+~ said:**
> Welcome to the penguin side :KS.

Is it a notebook? Maybe it has some pre-made partitions on it.

An alternative title for this post would have been: "LOOK MA, NO WINDOWS!"

Yep, it's a notebook. An HP, so it came with that cute little "recovery partition" on it. I erased it with GParted earlier and the ensuing attempt at simply cutting the HD half and half is what ended with me starting from scratch. :mad:

I posted the fdisk thing up earlier, is there another way for me to see where all my disk space is? I'd hate to think I've got ~5GB or so just sitting in the aether where I can't touch it.

---

### Post by jaybombalous on 2007-11-05
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6125db67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
```


it means there is a 112 gigs on the main sda1 linux partition...
there is also a 4 gig extended partition, u need this by default...
there is also a 4 gig linux swap partition, this is need by default.

112 + 4 + 4 = **120 gig.**

```
Disk /dev/sda: **120.0 GB**, 120034123776 bytes
```

looks good to me...

---

### Post by jaybombalous on 2007-11-05
```
Disk /dev/sda: 80 GB, 80056650240 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        9358    75168103   83  Linux
/dev/sda2            9359        9733     3004155    5  Extended
/dev/sda5            9359        9733     3004155   82  Linux swap
```

here is mine, default install. Looks exactly the same. U probable have 4 gig ext/swap because u have 25% more total HD space then I have. :)

---

### Post by SomeGuyDude on 2007-11-05
[QUOTE=jaybombalous;3708590
it means there is a 112 gigs on the main sda1 linux partition...
there is also a 4 gig extended partition, u need this by default...
there is also a 4 gig linux swap partition, this is need by default.

112 + 4 + 4 = **120 gig.**

```
Disk /dev/sda: **120.0 GB**, 120034123776 bytes
```

looks good to me...[/QUOTE]

Here's the problem, though. When I right-click "filesystem" I get 105.5 gigs, as seen in the picture, not 112.

Unless that 112 is using the 1000B=1KB system and my 105.5 is the 1024. The math on that (112000000000/(1024^3)) gives me 104.3, so something's off. Or am I an idiot somehow?

---

### Post by jaybombalous on 2007-11-05
> **SomeGuyDude said:**
> Here's the problem, though. When I right-click "filesystem" I get 105.5 gigs, as seen in the picture, not 112.

Unless that 112 is using the 1000B=1KB system and my 105.5 is the 1024. The math on that (112000000000/(1024^3)) gives me 104.3, so something's off. Or am I an idiot somehow?

Not sure, I don't really know that program u are using. I don't know how they mathematically produced the results. Hard to say where the discrepancies are...

---

### Post by jaybombalous on 2007-11-05
I already posted my fdisk stats, but here is an screen cap of the 'disk usage analyzer' in the gnome application drop down menu.


Notice how my sda1 partition is formatted for 75 gigs yet ubuntu disk usage analyzer only sees it as 71.2 gigs. Same as you and I have no explanation.

---

### Post by TeaSwigger on 2007-11-05
A late-ish welcome :) Your computer is now really yours; you're now really allowed to peek under the hood ;) 

Ubuntu has done incredible work in making a sophisticated linux OS easier than might have been imagined a short time ago. It must fly on your system - it does quite nicely on my old 384mb ram 933mhz PIII box where Vista wouldn't begin to install let alone run tolerably. No matter as it turns out; I've found everything I need one way or another in linux. Nowdays I only keep 2kPro around because of the only beef I have with linux: less than comprehensive scanner support. To be fair that's more to do with the manufacturers not releasing driver support for linux to develop with, due to their proprietary-oriented "partnerships" and all that sorta thing.

Personally I don't miss the MS Office Suites at all, but I guess its down to what you need from it. Between OpenOffice Suite, gnumeric speadsheet, AbiWord, Scribus and others, I'm set for my needs, and it all works nicer too. You may find everything you need natively with enough looking around, unless you do a lot of gaming. If you do want to use any windows programs, when you're ready you can see about WINE vs Virtual. WINE is getting better with age (of course right? ;) ) and the virtual options are really coming into their own too. They can be tricky to learn at first, but then they're pulling off quite an act. 

A lot happening with loads of wonderful apps around; it's a great time to be coming into it. Post and ask any questions, and above all enjoy!

---

### Post by floke on 2007-11-05
An easier one is

df -h

This will list all mounted partitions with easier-to-read data

My 80G HD is listed as 75G - so I wouldn't worry about a 112G from 120G scenario
Your 4G swap can be reduced though - (a) you won't need it; (b) If you do start to use more than eg 1/2G then your system will slow to silly levels anyway.

I currently have an 800MB swap (with 1G RAM) - I rarely ever creep into it.

But resize this later - there's no rush.

** EDIT - you can also use 'free -m' (as well as 'top') to see your memory use - the figure without the cache is the 'real' use **

---

### Post by SomeGuyDude on 2007-11-05
You're right on that, **Tea**. 2GB of RAM and an Intel Dual-Core make this thing run like butter. I've gotten spoiled to the point where if there's any delay with doing anything, I'm annoyed. I remember the old Windows convention of "after it boots up, just wait a few moments before doing anything or you'll confuse it". No problem at all with this, as soon as I see my desktop I open up my standard slew of programs and there's hardly a wait.

I haven't mucked with my printer/scanner yet, though I probably should sometime soon. Haven't needed them in a while. OpenOffice is great, I just got to like Word 2007. Something about the interface just rubs me the right way, though I've no doubts OO can do all the same things.

**floke**, doing that I get this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  2.4G   98G   3% /
varrun               1009M   96K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   88K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb2             5.0M  1.7M  3.3M  35% /media/YP-T9
/dev/sdb1             3.8G     0  3.8G   0% /media/YP-T9_
```

I know losing a few gigs to discrepant math isn't a big deal, now I'm just curious because I want to know. Side-effect of converting, I suppose, I feel like I "need" to know every little thing that happens.

And yes, I have a Samsung player plugged in at the moment. Upgraded my firmware a little bit ago so I could use it. That was a relief.

---

### Post by stchman on 2007-11-05
> **SomeGuyDude said:**
> Welp, it's been done.

I had Gutsy on dual-boot with Vista, and then decided to play with GParted and resize my partitions. I initially had 10G for Linux (I only planned on puttering around with it), and then the remaining ~90-ish for Vista and 7 for recovery (HP).

Well, I totally borked everything and had that Error 17 thing going, and since I had everything backed up, I decided to say hell with it and just formatted my HD and put Ubuntu on as my only OS. I'll tell ya, this is a big step for me. I haven't had a machine without Windows on it since... about... 1995.

One thing though. I have a 120GB HD. For some reason I only have 105 actually showing up. Allowing the 1000/1024 thing, that's 111. I couldn't have a six gig swap could I? When I installed, I just let it run with the "use entire disk" thing.

I have not needed Windows since I switched.  I find the only use for Windows is games.

---

### Post by jaybombalous on 2007-11-05
Microsoft already has a xbox 360 in release if all u wanna do is play games. No need for a 'windows' OS just to play games. Use that disk space for better purposes.

---

### Post by floke on 2007-11-05
> **SomeGuyDude said:**
> You're right on that, **Tea**. 2GB of RAM and an Intel Dual-Core make this thing run like butter. I've gotten spoiled to the point where if there's any delay with doing anything, I'm annoyed. I remember the old Windows convention of "after it boots up, just wait a few moments before doing anything or you'll confuse it". No problem at all with this, as soon as I see my desktop I open up my standard slew of programs and there's hardly a wait.

I haven't mucked with my printer/scanner yet, though I probably should sometime soon. Haven't needed them in a while. OpenOffice is great, I just got to like Word 2007. Something about the interface just rubs me the right way, though I've no doubts OO can do all the same things.

**floke**, doing that I get this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  2.4G   98G   3% /
varrun               1009M   96K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   88K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb2             5.0M  1.7M  3.3M  35% /media/YP-T9
/dev/sdb1             3.8G     0  3.8G   0% /media/YP-T9_
```

I know losing a few gigs to discrepant math isn't a big deal, now I'm just curious because I want to know. Side-effect of converting, I suppose, I feel like I "need" to know every little thing that happens.

And yes, I have a Samsung player plugged in at the moment. Upgraded my firmware a little bit ago so I could use it. That was a relief.

This just tells you how much space is being used by various partitions. The main ones are the sda (your HD partitions) and sdb (any external drives connected). Not sure about the others but I think they are part of the boot files. So here you have used 2.8G of sda1 and have 98G left.

To see usage of RAM etc try the top and free -m commands.

---

### Post by SomeGuyDude on 2007-11-05
> **jaybombalous said:**
> Microsoft already has a xbox 360 in release if all u wanna do is play games. No need for a 'windows' OS just to play games. Use that disk space for better purposes.

Funny story. A few months ago, I had my Zune hooked up to my notebook, using Windows Vista to make it communicate with my 360. I was Microsoft's bitch.

Now it's a Samsung YP-T9 connected to Gutsy. Still have a 360, though.

---

