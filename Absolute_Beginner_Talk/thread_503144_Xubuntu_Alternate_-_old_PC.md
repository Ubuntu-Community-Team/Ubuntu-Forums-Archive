---
title: "Xubuntu Alternate - old PC"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Kowalski_GT-R on 2007-07-17
Hi all,

problem:  Xubuntu 7.04 Alternate CD installation on and old machine

specs:     233MMX Pentium, 64Mb RAM(all 4 slots full, unless I find me some 32Mbs sticks)

I already have Puppy running on a similar specced machine, not installed it myself, but I have an idea of the performance I can obtain from a lightweight distro.
I just want to try Xubuntu, I like most of its features.

I'd like to share some experiences of things that happened, and request some info.

I am getting GRUB error 18, I searched the forums, but its a bit of a learning curve for me now (new to Linux) so:

1) should i try to install on a (much) smaller HD (I have a 3.something Gb spare one)

2) should i try to manually configure partitions using the CD?If so, can I get some step-by-step help here?

2) i found the "noapic" and "noalpic" thingies fitting with my case but I don't know where to insert them.

3) i recall having to insert something after pressing F6.
tried the above, computer froze (??)

4) once saw the "unable to locate RDSP" thing, can't really remember at which point, I'm sorry. Does't happen anymore.



Really, should I look at Puppy as my only choice? I'm a Synaptic addict :)


Lots of questions, I am willing to iron this issues out with the help of someone with more experience.(as well as patience and spare time :) )

thanks,

Andre

---

### Post by Kowalski_GT-R on 2007-07-17
Forgot to write that i was triyng to proceed with a command line installation....

ciao,

Andre

---

### Post by wolfen69 on 2007-07-17
you may have to go a different route. those are very low specs. you will have a very difficult time getting xubuntu to run well. i suggest damn small linux, or puppy linux.

---

### Post by Rocket2DMn on 2007-07-17
It sounds to me like your computer is probably too old to handle even Xubuntu.  It is definitely short on speed and the RAM is at a bare minimum.  If puppy linux works, that is probably your best option.

For the GRUB error 18, I think this means your boot sector isn't at the beginning of the disk, you would probably have to reformat and partition manually to fix that.

---

### Post by Kowalski_GT-R on 2007-07-17
infact i am trying a command line install

I can consider Fluxbox at a later time, just I'd like to learn the "best practices" and be sure I tried out everything.

example: I still cannot figure how to manually configure my boot partition (is it possible to do that via Xubuntu Alternate CD?)


I want to check FEASIBILITY before performance.
Somebody might also be interested in the results. I am searching this forum a lot. I want to post the outcome here: [http://ubuntuforums.org/showthread.php?t=478237&highlight=crappy+old+pc](http://ubuntuforums.org/showthread.php?t=478237&highlight=crappy+old+pc) :)

ciao

---

### Post by forestpixie on 2007-07-17
> **Kowalski_GT-R said:**
> Hi all,

...all 4 slots full, unless I find me some 32Mbs sticks)



Can't help with the rest - but I was looking for some old memory sticks a while back and got some help from freecycle - there are 300 members in Rome?

[http://www.freecycle.org/groups/allothercountries/#Italy](http://www.freecycle.org/groups/allothercountries/#Italy)

---

### Post by Kowalski_GT-R on 2007-07-17
thanks Forestpixie for the link, I already found a place where I can find some much needed RAM...

---

### Post by reset3x on 2007-07-17
You could check out Minix 3 if you can't get that RAM upgreaded... It'll run on a 486 with 16 meg of ram.. 

[http://www.minix3.org/](http://www.minix3.org/)

Like the others said above Puppy and DSL are good candidates...

Good Luck!!

---

### Post by confused57 on 2007-07-17
See the "Minimal Installations" section:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Also, if you have a fast internet connection, you might want to consider Ubuntu Lite:
[http://ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntu+lite](http://ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntu+lite)

---

### Post by Kowalski_GT-R on 2007-07-17
Thanks everybody. Every opinion here counts.

I have to check everything is done properly before changing distro.

I have read about Ubuntu minimal install.

Isn't installing a command line OS from the Xubuntu CD more or less the same thing?

I saw the CD installing lots of packages, It won't be a problem uninstalling memory hungry packages at a later time and swap for lighter applications (Silpheed, XMMS, Abiword), even with apt-get/aptitude and no Synaptic management.

Fact is, at that point I am even incapable of partitioning my disk properly.
Can anybody guide me through?


p.s. Checked the cd and memory, and they are ok. Hardware is configured properly, and internet broadband works.

ciao

---

### Post by Kowalski_GT-R on 2007-07-17
thanks to Confused57 for the links


so

```
sudo aptitude install xfce4
```
and
```
sudo aptitude install xubuntu-desktop
```


are the only differences between the Xubuntu Alternate CD and an Ubuntu minimal installation wich uses XFCE?

---

### Post by confused57 on 2007-07-17
This thread explains a minimal install with xfce4:
[http://ubuntuforums.org/showthread.php?t=30896](http://ubuntuforums.org/showthread.php?t=30896)

The xubuntu-desktop has quite a few more packages that will be installed

Here a couple of links you might want to read over, as far as partitioning and creating a separate boot partition:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4)
this is mainly FYI to show how it's done in Gentoo

[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)
Although this guide is written for dual-booting with Windows, there are some excellent screenshots of installing with the alternate cd.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)
an excellent description of grub error 18 and a history of bios limitations

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
The gparted live cd is an excellent partitioning tool, it's only a 45-50 Mb download...I'm not sure if 64 Mb is enough or not to run it.

---

### Post by Kowalski_GT-R on 2007-07-18
57 may be right,

confused....not so sure :)


thank you!

ciao

Andre

---

### Post by Kowalski_GT-R on 2007-07-18
It's done!

Xubuntu 7.04 Alternate from a command line. Another Penguin has born in my house!:) 

its possible. Can't really speak about performance, as my serial port mouse isn't working.

I'm well chuffed nonetheless.

Have to work around this problem....

---

### Post by macijuana on 2007-07-19
how did you do it? did you install the command line os? and what exactly is that by the way?

---

### Post by meborc on 2007-07-19
> **macijuana said:**
> ... and what exactly is that by the way?it is UNIX in all its glory without graphical interface...

---

### Post by macijuana on 2007-07-19
> **meborc said:**
> it is UNIX in all its glory without graphical interface...

it can be installed though correct?

---

### Post by splintercellguy on 2007-07-19
It's PART of the OS. It's there if X Windows doesn't start automatically.

---

### Post by Kowalski_GT-R on 2007-07-19
a strange thing i see during boot:


i get the "unable to locate RSDP" thingy at the start, but then it loads correctly.


I need some opinions:

should i get an USB PCI card to use the mouse? (serial port mouse no workie, was ok with Win 98.checked another mouse to be sure)

I found one with 233Mhz minimum requirements.

My PC actually runs at 225Mhz. I set the jumpers correctly, but still 225 instead of 233.

Would said card drain PC resources badly?any experience here?

ciao,

Andre

---

### Post by Kowalski_GT-R on 2007-07-26
Hi all,

did it again from scratch because the entire Xubuntu desktop was unusable on those specs.

Frankly, it runs better than I expected.

question about partitioning:

/boot
/
/usr
swap

are the only partitions I need? I remember a check going wrong during boot.
It says something about not having space left on device for static data.

any tips?

thank you

---

### Post by dptxp on 2007-07-26
Essential partitions are / (root) and SWAP. Everything is stored in root. Data can be stored in other partitions if you have.
/home is strongly recommended. Data goes there by default. Keep 6 GB to 10 GB for / (min 4 GB).
Very few use others. I do not.

---

### Post by Kowalski_GT-R on 2007-07-26
> **dptxp said:**
> 
/home is strongly recommended. Data goes there by default. Keep 6 GB to 10 GB for / (min 4 GB).
Very few use others. I do not.

6 to 10 for Xubuntu, I imagine.

What's the footprint of Xubuntu's Alternate Install cd?

I don't have that much space in Ide Primary disk

What would the best setup for my configuration?

1x 3.1 Gb
1x 21 Gb

I would like to keep the second disk for personal data and Swap.....

thank you,

Andre

---

### Post by happy-and-lost on 2007-07-26
If all you're after is a lightweight apt-based distro, try Debian netinstall. Sid is *very* fast, you know.

---

### Post by Kowalski_GT-R on 2007-07-26
thank you,

all I'm after is the best partitioning setup for my two hard disks.

Xubuntu runs just fine, i will keep it. It's my dad's pc, you know...

---

### Post by dptxp on 2007-07-26
Keep swap on the same hard disk as / (root). Also  /home if you are making it on same hdd. You can keep it small, say 1 GB but this will help you in case you remove the 2nd drive. You can make data partitions on 2nd HDD. You have not posted HDD specs so this is the best I can say.

If you have problem in installing because of low RAM then make a SWAP first with GPARTED live CD (download GPARTED and make it).

Puppy too will run Live.

---

### Post by Kowalski_GT-R on 2007-07-26
> **dptxp said:**
> Keep swap on the same hard disk as / (root). Also  /home if you are making it on same hdd. You can keep it small, say 1 GB but this will help you in case you remove the 2nd drive. You can make data partitions on 2nd HDD. You have not posted HDD specs so this is the best I can say.

If you have problem in installing because of low RAM then make a SWAP first with GPARTED live CD (download GPARTED and make it).

Puppy too will run Live.

thanks for being really helpful.
Its getting confusing; what do you exactly mean by HD specs?they are both parallel ATA disks, one 3.1 Gb(Primary master) the other 21 Gb (Primary Slave)

I can make all the partition changes through the Live CD, since I am still experimenting on that machine, and don't have any data to be saved.

what should the data partition name be?

(hope this is being interesting for some other folks)
ciao,

Andre

---

### Post by Shinoda on 2007-11-02
> **Kowalski_GT-R said:**
> serial port mouse no workie, was ok with Win 98.checked another mouse to be sure
See if [this]("http://ubuntuforums.org/showthread.php?t=202972#post1176847") helps.

---

