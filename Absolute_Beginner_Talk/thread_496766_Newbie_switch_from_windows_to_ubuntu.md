---
title: "Newbie switch from windows to ubuntu"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Midgett on 2007-07-09
Well the time has come where windows has pissed me off for the last time, but before i dump the "OS", i would like to make sure i can get all the drivers for my hardware and the main software support i would like :)
So with no further delay my system i intend to Linufy ;)

ABS Mayhem G3

Internal:

AMD 64 Turion 2.0Ghz
ATI X700 Mobile
1 GB Ram
120 GB HD
Wireless Card
PCI Slot
Ethernet Card
4x 2.0 USB
SVI output
VGA output
Bluetooth capable

External Devices id like to work:

USB cooler pad with 4x 2.0 USB Ports available
Olympus Stylus 1000 Digital camera
USB Mouse
USB logitech webcam

I ordered The official ubuntu book off amaon along with hacks customization guide and a beginners- professional guide to ubuntu. have downloaded ubuntu feisty fawn as well.

Im also using a friends laptop that he wanted to trash (dell latitude 810) as a lab rat :) 
and i ran into my first problem.

1. how do i wipe windows xp without reinstalling it ?
2. how do i get ubuntu to install as my main / only OS without having to boot from the cd?

Thanks for your time 

The Midgett ;)

---

### Post by swoll1980 on 2007-07-09
Get the live cd. Run it see if everything works nothings permenant unless you want it to be.

---

### Post by kamakura on 2007-07-09
Is there a specific reason you don't wan't to boot from the live CD and run the install program?  That will allow you to completely remove Windows and install Ubuntu.

---

### Post by adamklempner on 2007-07-09
Boot from the live cd and click on the install icon on the desktop.  The installation program will give you the option of wiping the entire hard drive and installing ubuntu as the primary OS.

---

### Post by lenninct on 2007-07-09
hey its a nice switch i came from Vista cuz it was just too slow, even on my new laptop. Ubuntu has done a lot, and all the open source software is a +, no more pirating...arrggg..

---

### Post by Church.Cameron on 2007-07-09
Well the first thing i always do before touching anything that involves the interface to my world is [COLOR="Red"]**_BACK UP DATA_**[/COLOR], very important, once you mess up and you can't see the data anymore, go and get a external case and pray that you can see the hard drive. but when ever i am gonna nuke the windows xp, i reload the xp cd so it brings me up to my partions and delete the xp partion, then without going ahead to reinstall the windows OS i close out and restart, Ubuntu will then take over as the primary, now might still get the dual boot screen
but sometimes its there and sometimes you get lucky. now the data will be lost off the Xp OS but if you backed up your data your good.

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)
this might help you in your quest i did it on my firends computer and it worked like a charm

---

### Post by mlentink on 2007-07-09
I would advise against wiping XP permanently. Even though it may not happen very often, there are a few people that get dissapointed with Ubuntu. They expect a better Windows than Windows, and find out Ubuntu is a completely different operating system. Also, you may find that as you are learning, there are still a number of things that you can do faster in Windows, simply because you are more familiar with it. Or that there are games you cannot live without, but are simply unavailable in Linux (or don't run well under Wine or Cedega).

Me, I don't care about games, and I have found that the Linux alternatives are usually better than their proprietary counterparts. Even so, I still have XP on a partition. Granted, I use it less and less, but after a year, I still use it sometimes.

So do yourself a favor. Keep it around. After a year you can always decide to wipe it. But that&#347; your option.

Welcome to the free world!

---

### Post by Midgett on 2007-07-09
Thanks guys ill give it another shot with the test laptop

and get back to yall tommrow time to go to work ;)

The midgett

---

### Post by Church.Cameron on 2007-07-09
> **adamklempner said:**
> Boot from the live cd and click on the install icon on the desktop.  The installation program will give you the option of wiping the entire hard drive and installing ubuntu as the primary OS.

I have heard alot of ppl having problems with that option, its better to just wipe it using the windows CD or you can just zero out the harddrive, but using the ubuntu wipe option i have seen cuases problems i haven't expirienced it but have noticed ppl having problems. agian open source motto " USE AT YOUR OWN RISK" :P

so i can't say much more for that.

i also would like to say i have a good feelings that logitech cam might have some conflicts its good idea like he siad to run it from the cd and check it out. everything else seems like it would  work on my deaktop i have a ton of diff types of hardware connected and it runs beautifully, ( just my damn laptop blows). but if you run into problems there will be a solution most of the time just gotta search for it.

---

### Post by dptxp on 2007-07-09
It is time users start using Linux as stand alone OS unless they have something important to run that runs in Windows. In case of new computers, it is easier to give a good try.

After data backup, I suggest manual partitioning with 10 GB for / (root) on ext3 format, 108 GB as /home in ext3 format, and 2 GB as SWAP.

Personally I would go for 10 GB /, 98 GB /home, 10 GB as Data Partition ext3 format, and 2 GB SWAP. The data partition gives option of loading and trying other OS (not Windows, it will overwrite GRUB) later. Else it can be used just for data, or any backup.

---

### Post by adhfan75 on 2007-07-09
> **Church.Cameron said:**
> Well the first thing i always do before touching anything that involves the interface to my world is [COLOR="Red"]**_BACK UP DATA_**[/COLOR], very important, once you mess up and you can't see the data anymore, go and get a external case and pray that you can see the hard drive. but when ever i am gonna nuke the windows xp, i reload the xp cd so it brings me up to my partions and delete the xp partion, then without going ahead to reinstall the windows OS i close out and restart, Ubuntu will then take over as the primary, now might still get the dual boot screen
but sometimes its there and sometimes you get lucky. now the data will be lost off the Xp OS but if you backed up your data your good.

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)
this might help you in your quest i did it on my firends computer and it worked like a charm

All well and good, but what if you want to install ubuntu on a system that has XP home, but was infected with viruses?   I did that on a machine a few days ago, although I don't know if that was the best idea or not..:confused: #-o  (Either way that PC has ubuntu now...now I just have to learn how to use it.:p :-\")

---

### Post by anotherbigal on 2007-07-09
If it's of any help, I have just joined the freebie world. I had to keep my XP as I run an account package and can't find anything remotely comparable so went for the duel boot option. But, I did run off the CD first just to have a look around. I warn you though, it is miserably slow. But at least I found that everything worked ok.

A.

---

### Post by dptxp on 2007-07-10
LIVE CDs are slow, decompression of files takes time.
Resources needed for Ubuntu are more than XP, XP came out many years back.

---

### Post by Midgett on 2007-07-10
Thanks guys, but i dont like dual booting for an option either i use something or i dont just the way i am plus i have a test laptop so until im comfotable using linux windows will remain on the abs
:)

so i need further help i tryd searching the forums but couldnt find anything to help me unless i dowload and run beryl for my current problem

i installed ubuntu 6.06 on  a dell latitude 810 and everything seems to be running smooth. but i cant hibernate by closing the lid it shuts all the way down instead, suspend crashes and blank screen freezes on blank screen.

any suggestions are welcome

fair warning this thing only has 256 ram and a 20gig hd also still has a floppy drive :) coworker was gonna trash it but figured why not use it as a guinea pig 

The midgett

---

### Post by stchman on 2007-07-10
> **Midgett said:**
> Thanks guys, but i dont like dual booting for an option either i use something or i dont just the way i am plus i have a test laptop so until im comfotable using linux windows will remain on the abs
:)

so i need further help i tryd searching the forums but couldnt find anything to help me unless i dowload and run beryl for my current problem

i installed ubuntu 6.06 on  a dell latitude 810 and everything seems to be running smooth. but i cant hibernate by closing the lid it shuts all the way down instead, suspend crashes and blank screen freezes on blank screen.

any suggestions are welcome

fair warning this thing only has 256 ram and a 20gig hd also still has a floppy drive :) coworker was gonna trash it but figured why not use it as a guinea pig 

The midgett

Suspend and hibernate are still hit or miss with Ubuntu.  I personally don't use it so it is a non factor.

---

### Post by misfitpierce on 2007-07-10
If you run and wireless does not boot up auto and you have a broadcom wireless card update system then open terminal and type

sudo apt-get install bcm43xx-fwcutter ... Hit yes and waalaaa.. Only if you have broadcom tho

---

### Post by Midgett on 2007-07-10
im not even sure this thing has a wireless card atleast i cant find it under device manager :-/

---

### Post by misfitpierce on 2007-07-10
Well it should have a wireless button or something... It sounds pretty up to date so id assume it would... Check box or look up your model online

---

### Post by Midgett on 2007-07-10
ah i think theres a misunderstanding

im testing ubuntu on a Dell Latitude 810 which is probably atleast 3 years old

it has 256 ram
a 20 gig hd
a floppy drive 
and a dvd player no burners
has ps2 port for mouse

and this is a laptop

im not using my nice ABS Mayhem G3 as a guinea pig :)

---

### Post by dptxp on 2007-07-11
> **Midgett said:**
> ah i think theres a misunderstanding

im not using my nice ABS Mayhem G3 as a guinea pig :)

I have been using all my computers as guinea pigs till I got Linux.

---

