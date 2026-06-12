---
title: "Problem Installing Ubuntu 6.06 on a Dell Inspiron 1100"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by barrack on 2006-09-07
My friend asked me to help her w/ her computer. It's a Dell Inspiron 1100. 128MB RAM and 2GHz. It originally had XP on it, but using it was nothing short of a slow death. It was just BOGGED DOWN.

Knowning that all she needed was the ability to check email and write papers, I thought "here's a perfect opportunity to spread ubuntu!"

The only problem is that it won't install. I inserted the LiveCD. It goes so far, and then screen just blacks out with nothing more than two white squares about in the middle of it. I tried this several times mind you. 

I got really frustrated and tried to reinstall windows on it. It installed no problem. It was even rather fast and responsive for about an hour. But once I did a few updates, it bogged down again. So I thought, "let's try ubuntu again." Only, this time, I used DBAN (Darik's Boot and Nuke) and did a 7-pass hard drive wipe to take care of any malicious whatever there may be on the comp that was slowing her down.

I did a little reading, discovered the existence of the "alternate installation disk" which was optimal for machines w/ less than 192MB RAM. I  gave this a try. Using the text-based prompts, I actually got a LOT farther. During the "installation of software" section of the install, i just turned my head sometime after the 48% mark. When I looked back... the black screen again!

Does anyone have any insight into what's going on? I'm getting really frustrated, especially considering that this is system's specs should be more than adequate.

(My next attempt, btw, is to get the output onto a different monitor of somesort, as I have read that the 1100 monitor got some issues with resolution output.)

---

### Post by benfindlay on 2006-09-07
You could try installing the server edition, which will install onto machines with even less RAM than her laptop.

Once it's all up and running, you can then install your choice of desktop using one of the following:

```
sudo aptitude install ubuntu_desktop
```
```
sudo aptitude install xubuntu_desktop
```
```
sudo aptitude install kubuntu_desktop
```

Seems that ubuntu installations have problems installing on machines without much RAM, especially the live disk, as the live disk relies heavily on the RAM during installation.

Hope this helps!

EDIT: I'd recommend xubuntu on a laptop with that amount of RAM

EDIT: also try removing all excess hardware, like pcmcia cards, in case it's one of them thats the problem

---

### Post by xyz on 2006-09-07
More info on Linux on the Dell Inspiron 1100:
[http://www.geocities.com/randomnumbergenerator2001/?200614](http://www.geocities.com/randomnumbergenerator2001/?200614)

---

### Post by barrack on 2006-09-07
befindlay and xyz,

thanks very much for your ideas. i'm reading through the link now. this system already has the BIOS 32 revision, but i'll keep reading.

the "alternate" installation CD *did* have an option to install as a server. i don't have much experience with xubuntu, but i will give it a try if this current attempt fails.

thanks, and i'll keep you posted.

---

### Post by xyz on 2006-09-07
Hi barrack,

> During the "installation of software" section of the install, i just turned my head sometime after the 48% mark. When I looked back... the black screen again!

Not sure this'll help but I experienced the same thing trying to install Dapper's alternate! I also ran DBaN, Digital Dolly and I don't know what else anymore. I read threads, asked questions but nothing worked despite the fact that CD's integrity checked fine; so did md5 sum.

My HW was fine, too...among other things, a brand-new HD on my Toshiba Satellite A40 which is only 2-years old!

Out of despair and sheer luck, I tried the following and it worked:
(don't ask me how!!)

I grabbed my old Breezy CD and proceeded to install; all went fine. Then I downloaded the hundreds Breezy updates.
After that I upgraded to Dapper via Internet and everything's been fine ever since...knock on wood!!

---

### Post by barrack on 2006-09-07
> **xyz said:**
> I grabbed my old Breezy CD and proceeded to install; all went fine. Then I downloaded the hundreds Breezy updates.
After that I upgraded to Dapper via Internet and everything's been fine ever since...knock on wood!!

I was actually contemplating this! But I didn't know where to get the breezy install CD! I only jsut started using ubuntu this summer (and love it, ps) but I'm only familiar w/ dapper.

if you can direct me to a breezy x86 iso, we'll go for it as plan c.

lol, as we speak, plan a just failed. i did the whole text based installation using an alternate monitor output and just got the bblack screen w/ white squares again. (this happened at about 56% through the "select and install software" phase.

on to plan b, server install and then installing xubuntu desktop.

---

### Post by xyz on 2006-09-07
I'm "laughing" WITH you...
Check this Breezy thingy out...let us know how it goes!
Hang in there...it WILL work sooner or later.
[http://mir2.ovh.net/ubuntu-releases/5.10/](http://mir2.ovh.net/ubuntu-releases/5.10/)

---

### Post by K.Mandla on 2006-09-07
I've had this same black-screen-with-white-boxes when using the alternative (install) CD on a desktop with Intel 915 video. It has something to do with switching out of the text environment and back again. My Optiplex 260 couldn't snap back from the video tests, and left me with a black screen with a single white box.

But in my case the CD continued to spin and installation was still going on -- I just couldn't see what was happening in the background. :confused: 

So long as you're not building a dual boot, you might be able to wait it out and press return when the CD pops out. It installs fine and boots perfectly, but it's a little disconcerting to have that happen.

Anyway, I don't know if that was what you were experiencing, but that might help. Cheers and good luck! 8)

---

### Post by barrack on 2006-09-07
> **K.Mandla said:**
> I've had this same black-screen-with-white-boxes when using the alternative (install) CD on a desktop with Intel 915 video. It has something to do with switching out of the text environment and back again. My Optiplex 260 couldn't snap back from the video tests, and left me with a black screen with a single white box.

But in my case the CD continued to spin and installation was still going on -- I just couldn't see what was happening in the background. :confused: 

So long as you're not building a dual boot, you might be able to wait it out and press return when the CD pops out. It installs fine and boots perfectly, but it's a little disconcerting to have that happen.

Anyway, I don't know if that was what you were experiencing, but that might help. Cheers and good luck! 8)

Glad to hear that someone else had this problem! (Also glad that I described it well enough that someone was able to recognize.) At any rate, i left this thing going for 6 hours, and the CD never spit out! So assumed it just got stuck.

I'm going to try the breezy (plan c) and maybe address your approach again. 

Do you have an estimate for about how long this process takes? I've installed on a couple different machines, and it has taken as much as 3hours, or less than 20 minutes. Depending on the machine. But I definitely left this guy to install overnight.

As we speak, we're on plan b (server install... and then xubuntu install) and it's at "select and install software" at 5%.

---

### Post by barrack on 2006-09-07
> **benfindlay said:**
> 

```
sudo aptitude install xubuntu_desktop
```



I installed as server and was given a terminal prompt. I did this and this is the message that I got.

```
Couldn't find any package whose name or description matches "xubuntu_desktop"
```

Ideas?

---

### Post by xyz on 2006-09-07
> Do you have an estimate for about how long this process takes?

The Breezy Install took a regular 30 to 60 minutes; the Breezy Updates took 2 to 3 hours (about 700 updates, if I remember right) and a couple of hours to upgrade...all of this, of course as you know, depends on your connection speed! 

This is approximative timing! I say this because I don't exactly remember; in fact, it actually took me DAYS (including: DBaN and so forth, reformating/partitioning, install Breezy and so on...).

So long as it works...:cool:

---

### Post by barrack on 2006-09-07
Still on plan b here. 

The server ubuntu is up and running lovely. It's just like a big terminal! ha ha.

Anyway... i followed the instructions on the following page

[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

to install xubuntu from desktop. I edited the source.list and everythign. Updated... and using either aptitude or apt-get, I still got the message "couldn't find package xubuntu-desktop"

As we speak, I am downloading the .iso's for breezy and for xubuntu-dapper (alternate installation disk).

so plan c is breezy (may not even upgrade to dapper once it's on, just cos i'm so over this and my friend just needs email and OOo) and plan D is xubuntu alternate cd installation.

---

### Post by xyz on 2006-09-07
**may not even upgrade to dapper once it's on, just cos i'm so over this and my friend just needs email and OOo) and plan D is xubuntu alternate cd installation.**

That's plenty since your friend only needs that!
Sure hope one of the "plans" work. I'm sure it will!
Signing off for now - keep us informed.

---

### Post by YeahBuntu on 2006-09-07
I think the correct way is to do this:


```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by barrack on 2006-09-07
> **YeahBuntu said:**
> I think the correct way is to do this:


```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

I tried that, but to no avail. I'm sure that there's another step to it that I'm missing.

At anyrate, plan C seems to be working alright. I'm installing Ubuntu Breezy. It's almost done. We'll see what happens.

---

### Post by barrack on 2006-09-07
Here's the update.

Ubuntu Breezy loaded just fine... but it was just still way too slow. So as of right now, I'm installing xubuntu to see what I can get.

I am using the xubuntu 6.06 alternate install disk. So far everything seems to be working fine.

fingers crossed.

---

### Post by Paul133 on 2006-09-07
Well, can you apt-get ubuntu-desktop on the server install? I had the same problem on my Inspiron 1200 (256 MB of RAM) and it works fine with the server install and apt-get install ubuntu-desktop. By the way, do you have internet on this computer? If not, you realize you need to leave the CD in while apt-getting ubuntu-desktop or xubuntu-desktop. I think that's probably your problem!

---

### Post by dhanwada on 2006-09-07
I am having a similar problem. I tried installing Ubuntu onto a Compaq Presario XXXX, very old, AMD K6-2 processor with 120 MB of RAM. The computer wouldn't boot up from the CD, I get a black screen with a blinking pointer.

But the good news is, there seems to be an alternate install CD which will install on systems with less than 192MB RAM .... Below, is clipping from the draper download page...the last bullet says "installs on systems with less than about 192MB of RAM. "



Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 


Cheers

---

