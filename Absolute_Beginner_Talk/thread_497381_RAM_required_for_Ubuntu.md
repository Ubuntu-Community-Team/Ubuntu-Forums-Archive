---
title: "RAM required for Ubuntu?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-07-10
Right, here we go.

I'm trying to boot ubuntu 7.07 (feisty fawn) into the live CD on my old Toshiba Tecra Laptop (recently the Hard Drive cable got iself torn in two so I just removed the whole hard drive (and remaining bits of the cable) completely)

However I keep getting a few rather annoying error messages.


```

[      0.000000]  ACPI: Unable to Locate RSDP
Loading, please wait...

[[Ubuntu Splash Screen here with loading bar]]

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: Can't access tty; job control turned off
(inittramfs)  _


```

I then get this kind of recovery console or something, and I don't know what I can do with it to make it work. 

It used to give me loads of garble about "I/O error on device fd0 on block 0" (or something similar...I can't REALLY remember exactly) over and over and over, but it didn't turn up again for some reason.  

And I'm wondering, seeing as it says it requires 128 mb of RAM, and I only have 48 mb RAM, would that be why this is happening?  I don't know what it has to do with the Floppy Disk (fd0) but I'm somewhat lost for ideas now.


Any help?   :popcorn:

---

### Post by buuntuu! on 2007-07-10
hi neon_knight!
with only 48MB RAM you won't go anywhere with *ubuntu, i'm afraid.
check out [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/") for your good old rosinante!

---

### Post by scragar on 2007-07-10
alternativly if you can get your hands on a copy of partition magic you can use it to give yourself a swap partition, linux will be able to use this as if it was ram(although access is slower since it is stored on your hard-drive).

---

### Post by AlexenderReez on 2007-07-10
> [http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution](http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution))

you need atlease 256mb of ram...ram is cheap nowdays ....right?but there is distro that required below that.....

---

### Post by Outrunner on 2007-07-10
I recommend [Damn Small Linux]("http://www.damnsmalllinux.org/"), Ubuntu is too heavy for your laptop.

> you need atlease 256mb of ram...ram is cheap nowdays ....right?but there is distro that required below that.....

Whether RAM is cheap or not doesn't matter, because he has an old  laptop, so even if he manages to find RAM for it(which will *not* be cheap), he might have a hard time putting it in, that is if the laptop has enough slots for more RAM.

---

### Post by Neon_Knight on 2007-07-10
Yeah, it only has one slot, and that't taken up by the 48mb chip.

And you're right that it would be exceedingly expeisive.. the replacement flex cable for my hard drive which I broke (a tiny plastic fragment of ribbon wire) would cost $110. 

Anyway, I'll try that out, thanks. 

And scragar, I have no Hard Drive, I broke my HD flex cable (as outlined in first post) :D

Oh, and on that DSL webste, it says 

```

can run on as little as 128 mb

```

I have less than half of that, you think it'd work?



thanks.

---

### Post by AlexenderReez on 2007-07-10
> **Outrunner said:**
> I recommend [Damn Small Linux]("http://www.damnsmalllinux.org/"), Ubuntu is too heavy for your laptop.



Whether RAM is cheap or not doesn't matter, because he has an old  laptop, so even if he manages to find RAM for it(which will *not* be cheap), he might have a hard time putting it in, that is if the laptop has enough slots for more RAM.

so in that case ,just buy new laptop....lol...just joking.....ok2....other distro like damnsmalllinux may suite it....

---

### Post by Hallvor on 2007-07-10
DSL will probably run just fine with those specs. It can run on as little as a 486 with 16 mb ram.

I would not install Ubuntu on a computer with less than 384 mb ram.

---

### Post by Neon_Knight on 2007-07-10
Oh, okay.

Thank you very much! 

I'll get to downloading that right now!

---

### Post by hyper_ch on 2007-07-10
I hade DSL once on a 10 year old notebook (well, it was 7 or 8 years old) with 64 MB ram and it run fine... xubuntu did install there but it was sloooooooooooooooooooow

---

### Post by Neon_Knight on 2007-07-10
Oh, a question:

I know it says it can be used as a live CD, does that mean if I were to just download a copy from the "download" link, and burn it to a CD, that would give me the live CD? Or just an install CD, seeing as I am without Hard Drive, I can't use an install CD...

---

### Post by buuntuu! on 2007-07-10
it's a live cd alright, actually it is not meant to be installed... you can install, but ut's optimized to be a live-os...
you can take it with you and use it on any box that can boot from cd :)

EDIT:
it may be a bit heavier than damn small, but if you prefer a more polished distro, try [http://www.slax.org/]("http://www.slax.org/") as well!!

---

### Post by d_yat on 2007-07-10
if you wanna try another small distro, you could try puppy linux.
I got bored one day and tried it on an old pc lying around the house with 96MB ram and 333MHz pentium II.
I found it easier to use than DSL.

---

### Post by buuntuu! on 2007-07-10
> **d_yat said:**
> if you wanna try another small distro, you could try puppy linux.
I got bored one day and tried it on an old pc lying around the house with 96MB ram and 333MHz pentium II.
I found it easier to use than DSL.

puppy won't run on 48 MB RAM though!
EDIT: and neither will slax (at least if you want to use a graphical user interface... it seems that dams small is the only way to go!)

---

### Post by d_yat on 2007-07-10
> **buuntuu! said:**
> puppy won't run on 48 MB RAM though!
EDIT: and neither will slax (at least if you want to use a graphical user interface... it seems that dams small is the only way to go!)

oh. i did not know that. It's just that from the documentation i've read it says puppy does.
[http://puppylinux.org/wikka/AboutPuppy](http://puppylinux.org/wikka/AboutPuppy)
->under "advantages of puppy"
and
[http://tmxxine.com/pm/p1.html#__AbiTOC0__](http://tmxxine.com/pm/p1.html#__AbiTOC0__)
->under "Not enough RAM / NTFS solutions"
it says
> Puppy will run well with as little as 48MB RAM and no swap file; with 48-96MB of RAM programs are loaded from the CD when needed

anyway. maybe DSL will be better with that little amount of RAM, wouldn't know. I'll let someone else who can try judge.

---

### Post by dgbraun on 2007-07-10
You might also try the live CD of Anti-X Mepis 6.5 which runs on as little as 64 megs of RAM and as slow as a P-II chip.

---

### Post by maestrobwh1 on 2007-07-12
Ditto with the last post.  I have a fujitsu 200 Mhz topped out at 96 MB.  I ran damn small linux (DSL) as a "fugal install" and it worked pretty well.  I later decided that I wanted something that was more like ubuntu, so I installed xubuntu (you have to use the alternate cd, as the live/graphical installer won't run with this small amount of RAM).  It ran quite a bit slower than DSL.  Still, I was able to keep up to date programs, and it ran Opera and Epiphany pretty well.  Firefox... seemed VERY slow.  Abiword was usable.  I didn't try Open Office, that seemed to be a bad idea.

I keep the laptop as a novelty/backup.

DSL is a great project.  It does require a new knowledge base as far as having to load extensions and such.  It runs off of the knoppix concept.

---

