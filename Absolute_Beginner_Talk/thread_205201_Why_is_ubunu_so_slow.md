---
title: "Why is ubunu so slow??"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-28
why is ubuntu so slow on y computer

2.26 Ghz processor. 
256 Mb of Ram 
Intel x86 Motherboard.

It shouldn't be so slow.

Is it due to swap.

My swap is only 8 Mb
and the / (root) is 5 GB.

---

### Post by bluenova on 2006-06-28
Swap should be double the amount of RAM, especially as you don't have much RAM in the system.

---

### Post by frodon on 2006-06-28
Does your proscessor support hyperthreading ?

256Mb of RAM for a 2.2Ghz prosc is not enough IMO (i use 2Gb of RAM for my AMD64 2.2GHz)

---

### Post by aysiu on 2006-06-28
Your swap partition should be about 512 MB, not 8 MB. Even so, Ubuntu shouldn't be *that* slow.

I have Ubuntu on a computer with a 766 MHz processor and 128 MB of RAM, and it's not that slow (unless I have more than two applications open at once).

---

### Post by araz on 2006-06-28
What is slow at ubuntu?
[QUOTE=hardfire_avk]
Is it due to swap.

My swap is only 8 Mb[/QUOTE]
try Increase your swap to 512 MB, check if you have the video drivers installed.

---

### Post by superm1 on 2006-06-28
I don't know that I follow the whole "swap should be double the RAM" thing that gets passed around.  I have a box with 768, and another with a gig and its just silly to make such a big swap.  The swap is only ever "touched" when I'm doing some big movie transcoding or something of that nature, so in my opinion the rule should be that swap should be at least 256, but only as neede for more beyond that.

---

### Post by tommcd on 2006-06-28
The more RAM you have the less important the swap file becomes. The OP has only 256mb, so he will likely use his swap file for multitasking, RAM intensive apps, etc.
For anybody with enough RAM (as you have), a large swap is likely a waste IMO.

---

### Post by bluenova on 2006-06-28
[QUOTE=superm1]I don't know that I follow the whole "swap should be double the RAM" thing that gets passed around.  I have a box with 768, and another with a gig and its just silly to make such a big swap.  The swap is only ever "touched" when I'm doing some big movie transcoding or something of that nature, so in my opinion the rule should be that swap should be at least 256, but only as neede for more beyond that.[/QUOTE]
Agreed, for a large amount of RAM it's not so important, but if you don't have much RAM i.e. less than 512Mb then it should be double. I have a laptop with 192Mb RAM it runs fine but uses a lot of swap space.

---

### Post by nalmeth on 2006-06-28
Yeah, I agree to a point superm1

Even with my 512 RAM swap isn't really being used much. Come to think of it my laptop with 128 megs doesn't see full swap usage even when running a few apps.

It is constantly used though, and very valuable. You can tweak how much swap is used as opposed to RAM for a short-term-type speed boost, because RAM is *much* faster than your HD, but in the long-run swap is important.

To OP 8 megs wouldn't be near enough.

What make of processor do you have? There might be a better kernel for you to use. Installing a new kernel is easy, and you can easily revert to the old one.

---

### Post by _simon_ on 2006-06-28
whilst we're on the subject of swap

I have 1Gig ram

Currently Dapper is using:

160.9 MiB RAM

and

115.8 MiB swap

Why would it be using that much swap when so little ram is in use?

---

### Post by frodon on 2006-06-28
[QUOTE=_simon_]whilst we're on the subject of swap

I have 1Gig ram

Currently Dapper is using:

160.9 MiB RAM

and

115.8 MiB swap

Why would it be using that much swap when so little ram is in use?[/QUOTE]Adjust swapping level with the command below. Lower the value for less swapping, raise it for more swapping. Default is 60, The more RAM your computer have the lower you can go. 

```
sudo sysctl -w vm.swappiness=30
```

More on the topic in this article : [http://www.linuxjournal.com/article/8308](http://www.linuxjournal.com/article/8308)

IMO with 1Go of RAM you don't even need swap.

---

### Post by _simon_ on 2006-06-28
thank you!

---

### Post by hardfire_avk on 2006-06-28
What is not slow. Everything is slow. The Loading... The Mouse cursor.....

I run gedit and it open after some time...
All programmes are slow..

---

### Post by frodon on 2006-06-28
Well, i can understand that you're disapointed and have really annoying speed problems but you asked for some help and people here are trying to provide you some.
Almost all have a solution trust me, but if you don't even answer the questions that the users asked you to provide you a good support you will not solve your problem.

Did you try to change your swap size ?
Could you provide the exact name of your prosc ?
What kernel do you use ?
What graphic card do you have ?
Did you install the drivers for your graphic card ?

Please provide some more informations if you wish some help.

---

### Post by hardfire_avk on 2006-06-28
> 
Did you try to change your swap size ?


nah!! Not yet. However how do i do that. Do i have to reinstall it again/

> 
Could you provide the exact name of your prosc ?


What is a prosc??

> 
What kernel do you use ?


I think it is linux-386.. The first one during 5.10 installation.

> 
What graphic card do you have ?

God. Knows.. how do i get to know that..

> 
Did you install the drivers for your graphic card ?

No.  i havenot done that.

---

### Post by frodon on 2006-06-28
For your swap partition you could use gparted (the gnome partition tool) to increase the swap size.

Sorry, i mean processor, i'm trying to know if you have a pentium 4 proscessor which support hyperthreading because the default ubuntu kernel (i386) don't support hyperthreading therefore swiching to the suitable kernel would really improve the performance for this kind of proscessor.

Hum, for your graphic card there's a tool in the gnome menu which list all the peripherals of your system, i think the name of your video card is written there.
Is you computer a laptop ? if yes could tell us its exact name.

Once we have the name we will see the driver part.

---

### Post by hardfire_avk on 2006-06-28
How do i get the Gparted. i meanwhere is it. i didn't get it.

I have a celeron 2.26 Ghz Processor till i know.

what does hyperthreading mean and how do i know it is supported or not?

And ya! I will get name of my graphic card from windows in 5 mins. Will just reset and get it.

And ya.. My PC is not a laptop.

---

### Post by frodon on 2006-06-28
About hyperthreading : 
[http://en.wikipedia.org/wiki/Hyperthreading](http://en.wikipedia.org/wiki/Hyperthreading)

Unfortunatly celeron processors don't have hyperthreading technology.

The suitable kernel for your processor is the i686, you can install it with this command line (you will have to reboot after that) :  ```
sudo apt-get install linux-686
```

Gparted should be in System > Administration but you can launch it just typing "gparted" in a terminal.

---

### Post by hardfire_avk on 2006-06-28
I have a Intel(R) Celeron processor. I got this information from my Device Manager.

And ya.. the graphic thing u had asked for is.

**Intel(R) 82865G graphics Controller**

This is what i got after typing gparted.

```

avinash@avinash:~$ gparted
bash: gparted: command not found

```

---

### Post by frodon on 2006-06-28
I guess it isn't installed yet, you can install it using this command line : ```
sudo apt-get install gparted 
```If you get an error using this command that would mean that you don't have all the repositories enabled.
In this case open you sources.list file : ```
sudo gedit /etc/apt/sources.list 
```Then check that you have something like that : ```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```Replace dapper by breezy if you run breezy.
Update the package list : ```
sudo apt-get update
```and retry the command

For your graphic card drivers check your xorg.conf file, backup it first : ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo gedit /etc/X11/xorg.conf
```Scroll down until you get to the Section Device and replace the Driver to i810..., it would look like that : ```
Section "Device"
Identifier "Intel Corporation 82865G Integrated Graphics Device"
Driver "**i810**"
BusID "PCI:0:2:0"
EndSection
```

---

### Post by njzillest on 2006-06-28
is it ok my swap is 100 mb, i have 512 mb ram 1.8 ghz processor 

toshiba R10  satellite laptop

---

### Post by wpshooter on 2006-06-28
Does Hardfire still have an older version of Ubuntu (not Dapper Drake) ?

If so, and if they do not have any vital information on this install, would they not be better just to get a good download of the Dapper Drake Desktop CD and re-install from scratch and have someone give them the correct partitioning information for their hard drive before they begin the re-installation ?

Thanks.

---

### Post by Breezy Badger on 2006-06-28
I have 1 GB of ram and i made my swap 1 GB.  is this ok?  should I change it?

---

### Post by hardfire_avk on 2006-06-29
Ya!! I will get my ubuntu 6.06 Drapper Drake CD's in 3 or 4 weeks. then i will ask for help about the right partioning.

However i have a 40 GB hardisk.

3 Partitions are Fat 32 (~13 GB, 13BG and 5GB)
1 is swap (~8 Mb)

and the last one is root.(~8 GB)

---

### Post by _simon_ on 2006-06-29
[QUOTE=Breezy Badger]I have 1 GB of ram and i made my swap 1 GB.  is this ok?  should I change it?[/QUOTE]

I have 1 GB ram and I've turned my swap off altogether and so far no ill effects of any kind.

---

### Post by drtvasudevan on 2006-06-29
[QUOTE=frodon]
The suitable kernel for your processor is the i686, you can install it with this command line (you will have to reboot after that) :  ```
sudo apt-get install linux-686
```

[/QUOTE]
it is only of late- last two days- that i feel my system has slowed down.
i run on P3 800mhz so i guess the linux suitable for me is i686.
is it worth upgrading this?

how big a download?

tv

---

### Post by frodon on 2006-06-29
Yes the i686 kernel is appropiate for a P3 800MHz.
It's a big download but not huge (something like 30Mb maybe).
It's worth upgrading but you will not see a huge difference however.

Good luck ;)

---

### Post by hardfire_avk on 2006-06-29
[QUOTE=drtvasudevan]it is only of late- last two days- that i feel my system has slowed down.
i run on P3 800mhz so i guess the linux suitable for me is i686.
is it worth upgrading this?

how big a download?

tv[/QUOTE]

I downloaded i686 and during installation it got a page full of error.

I think that my computer may be slow because ubuntu is not using any part of my RAM. How do i get to know howmuch RAM is being used by ubuntu on my system.

---

### Post by frodon on 2006-06-29
There's a system monitor somewhere in the gnome menu (it looks like the one in windows) which show you the RAM usage, i believe the command line to start it is something like "gnome-system-monitor".

---

### Post by hardfire_avk on 2006-06-29
Hey!! I installed i686 kernel but got something wrong due to which now my grub is full of kernels. 2 of i686 and 2 of i386.

How do i remove the i686 one??

please help!!

---

### Post by frodon on 2006-06-29
Don't worry, it's normal that GRUB list all the kernels you installed (including the kernel with recovery mode), to remove the i686 kernel : ```
sudo apt-get remove linux-686
```

---

### Post by drtvasudevan on 2006-06-29
[QUOTE=frodon]Yes the i686 kernel is appropiate for a P3 800MHz.
It's a big download but not huge (something like 30Mb maybe).
It's worth upgrading but you will not see a huge difference however.

Good luck ;)[/QUOTE]

upgraded.

many a Q arise.
1. it also downloaded some 386 files -restricted modules. why?
2. i seem to be in 386 still. i have restarted twice.
dont see a 686 option in grub. should i refresh grub? it is not done automatically?

<<edit: oh sorry. that grub is from another installation. this one is in the partition itself and not the one presently working.>>

3. i saw a line lilo recommanded. that was also included in the download. does grub not work with it? i want to be sure before in reinstall grub.

4.can i delete the 386 image? i am running out of disk space.

incidentally if i remove more programs that i dont use like multimedia does it make the system faster?
what really determines how a system will run fast. why it differs from distro to distro?

lot of Q sorry!

tv

---

