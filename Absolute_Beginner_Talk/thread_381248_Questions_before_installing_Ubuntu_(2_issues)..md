---
title: "Questions before installing Ubuntu (2 issues)."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Bensky on 2007-03-10
Well, I've decided to use ubuntu after running it on a 450 mhz test PC w/ a live CD. :P Anyway, here are my 2 issues.

First, my current computer can definately run Ubuntu, but it has limited hard drive space (only 2 hds, 30 gig and 20 gig). I'm thinking that I will need to clear up about 15 gigs of space on my master hd which only has like 6 gigs free. Would I really need to clear up 15 gigs more or can I make do with less? I won't be installing much on Ubuntu, and will just be using it for word processing, internet, music, etc. Windows would be for games only.

Secondly, My dad told me that most linux distros include dual boot software built in, so that I can run windows and linux on the same PC. However, I'm wondering if this is only possible with a partitioned hd, since what I want to do is keep windows and linux on the same hard drive without one erasing the other. :$ I do have partitionmagic, but I'm kind of afraid to use it since I don't want to corrupt any of my data (I have heard that this can occur).

Thanks,
Bensky :guitar:

---

### Post by halitech on 2007-03-10
I'm running similiar hard drives (30 and a 40). I would almost recommend using the 30 gig for windows and installing ubuntu on the 20 and making sure you have at least 10 gig on the bigger drive that is fat32 that both OSes will be able to read.

when you start the install, you will be able to partition there but I would recommend doing a complete defrag on both drives before you start.

---

### Post by mozkaynak on 2007-03-10
> Would I really need to clear up 15 gigs more or can I make do with less?
6 Gig might be enough if you dont stack much.
However 15 gig more would be nice for many stuff in Ubuntu

for second question:
theoretically you should not lose any data but ask people who used partition magic before.

---

### Post by overdrank on 2007-03-10
> **Bensky said:**
> Well, I've decided to use ubuntu after running it on a 450 mhz test PC w/ a live CD. :P Anyway, here are my 2 issues.

First, my current computer can definately run Ubuntu, but it has limited hard drive space (only 2 hds, 30 gig and 20 gig). I'm thinking that I will need to clear up about 15 gigs of space on my master hd which only has like 6 gigs free. Would I really need to clear up 15 gigs more or can I make do with less? I won't be installing much on Ubuntu, and will just be using it for word processing, internet, music, etc. Windows would be for games only.

Secondly, My dad told me that most linux distros include dual boot software built in, so that I can run windows and linux on the same PC. However, I'm wondering if this is only possible with a partitioned hd, since what I want to do is keep windows and linux on the same hard drive without one erasing the other. :$ I do have partitionmagic, but I'm kind of afraid to use it since I don't want to corrupt any of my data (I have heard that this can occur).

Thanks,
Bensky :guitar:

Welcome,  you can use 10 gigs and that would work it has for me in past and the live cd will create a partition for ubuntu without hurting windose ( better to back up just in case) and it wil resize windose partition to get you the space needed. Good luck !

---

### Post by oilchangeguy on 2007-03-10
if you've only go 6gb left on your master drive you don't need/want to add any more to that. use the second drive. there's no "dual boot software" built in. you can partition your hard drive to run different versions of windows if you want to. you don't say what operating system you're using now. the computer i'm using now has two hard drives. a 30gb with only 6.06 installed. and a 10gb slave drive with xp pro installed, just incase i need it.

---

### Post by Bensky on 2007-03-10
> **halitech said:**
> I'm running similiar hard drives (30 and a 40). I would almost recommend using the 30 gig for windows and installing ubuntu on the 20 and making sure you have at least 10 gig on the bigger drive that is fat32 that both OSes will be able to read.

when you start the install, you will be able to partition there but I would recommend doing a complete defrag on both drives before you start.

Thanks for the help. 2 more questions: If I install ubuntu on the 20 gig, I won't need to partition will I? Also, I just realized that my screen res might not be supported by ubuntu :X. I have a 19" widescreen LCD, and it uses the resolution 1440 X 900 - is there a way to change it easily? I ran a live CD called SLAX a while ago, and some people told me I had to mess around with modelines, and it might screw up my monitor permenantly...I hope it's not that complicated. :confused:

EDIT: @oil: sorry, I'm running windows xp pro.

EDIT2: @paul capps: By 10 gigs, do you mean I would need to clear up 4 gigs more or would I have to clear up 10 gigs more? :P

---

### Post by halitech on 2007-03-10
you won't have to manually partition it, just the installer to use the entire drive and it will set up a standard structure for you.

it's going to depend more on your video card then the monitor and if the card is supported or not. If it's relativily new, shouldn't be a problem

---

### Post by Bensky on 2007-03-10
> **halitech said:**
> you won't have to manually partition it, just the installer to use the entire drive and it will set up a standard structure for you.

it's going to depend more on your video card then the monitor and if the card is supported or not. If it's relativily new, shouldn't be a problem

Oh, forgot to mention that. I have an ATI Radeon 9600 XT (128 mb). It's a few years old I think.

---

### Post by vavroom on 2007-03-10
FWIW, I've used partitionmagick for *years* (actually, before it became Norton's...) and never had data loss using it, and I've delted created swaped renamed converted partitions.

The trouble with trying to squeeze too much on the drive that has your XP install is that *windows* doesn't play well with your system if you have less than 10% or so of free space on it.  They *say* that's not so anymore, but my experience tells me otherwise.  If you have a 30Gb drive running Windoze on it, I would make sure to have at least 3Gb of free space on it, no matter what.  This means that you have in effect access to 27Gb.

As for knowing if your monitor will work, you should easily be able to tell by sticking the LiveCD in your drive and starting Ubuntu in LiveCD mode.  If it works, you're a happy camper :)  If not, you'll have to fiddle ;)

---

### Post by halitech on 2007-03-10
the 9600 should work

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

---

