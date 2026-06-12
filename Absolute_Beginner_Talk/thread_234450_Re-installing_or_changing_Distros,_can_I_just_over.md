---
title: "Re-installing or changing Distros, can I just overwrite?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-11
Hi all, 

This might be the n00biest question ever, but I'll ask it anyway. If I want to reinstall Ubuntu to get things back to their OOTB defaults, or if I wanted to change to another distro, can I just load the live CD and install, and let the installer overwrite the HDD, or do I need to wipe the drive first? And if so, how? Since I let Ubuntu have the whole drive there should not be DOS on there anymore, so I don't think that I could fdisk or any of that, so would I just let the installer of whatever Linux distro do it?

I have been a Mac person for quite a while, so haven't had to play around in the BIOS to make changes (until I had to change the boot order to install Ubuntu), and I don't know if I can format the drive from the BIOS. So I just need some basic help.

I realize that this is a *very* basic question, but I searched the forums and couldn't find anything (or actually too much to filter), so I would really appreciate some advice.

TIA

KC

---

### Post by wpshooter on 2006-08-11
Do you have Ubuntu installed on your MAC or on your IBM or both ?

---

### Post by davebgimp on 2006-08-11
It's always a good idea to wipe the partition first before you install into it. The Ubuntu install cd has a partitioner to help you with it.

---

### Post by kinematic on 2006-08-11
if you want to reinstall ubuntu or install another distro just select the partition and reformat it(always reformat and never just overwrite).
every distro installer gives you the option to reformat so you'll be fine. 
i don't know about fdisk tho because i've never used a mac.
but one thing you can't do is format from the bios.....it doesn't have that option.
if you want to know exactly what the bios does do a google search like "what is bios" ;)

---

### Post by moosbruxxer on 2006-08-11
Sorry, this is another noob question. 

What if I want to re-install Ubuntu from scratch but want to leave my home partition untouched? How do I make sure that the installer understands that this is what I want to do instead of it formatting the whole lot?

---

### Post by kinematic on 2006-08-11
don't mark it for formatting :rolleyes:

---

### Post by davebgimp on 2006-08-11
> **moosbruxxer said:**
> Sorry, this is another noob question. 

What if I want to re-install Ubuntu from scratch but want to leave my home partition untouched? How do I make sure that the installer understands that this is what I want to do instead of it formatting the whole lot?

Assuming /home/ is in it's own partition, away from the ubuntu install, you can select to manually edit the partitions in the Ubuntu installer. Just delete the partitions you don't want, leave the /home/ one and install into the free space.

If /home/ si not on it's own separate partition, you'll need to create one and copy it over before reinstalling ubuntu.

---

### Post by moosbruxxer on 2006-08-11
Thank you good people. I appreciate your replies. I just don't need to go losing my home dir right now.

---

### Post by Carbonfish on 2006-08-11
> **wpshooter said:**
> Do you have Ubuntu installed on your MAC or on your IBM or both ?

I just have Ubuntu installed on my ThinkPad.

 I bought the T23 with the specific purpose of using it to learn more about Linux. I will admit that I wasn't brave enough to do a dual-boot on the iBook as I work for the Public School System and am a student as well (still an undergrad), and use the Mac everyday for work and school and can't afford *any* downtime.

So I have the ThinkPad to experiment with without having to worry about disrupting my work-flow.

I am having quite a bit of trouble getting this distro to play nice with my networking hardware and if I can't resolve these problems soon I may have to change distros, even though I really like what I have seen so far in Ubuntu. But, I have work to do, and *whatever* distro I use, it has to be stable enough to work every  day on a laptop and I have to know that I'm not going to spend more time with a terminal window open than I am "working". If I have to re-configure every time I want to connect to an "open network", or change from a wired ethernet connection to a wireless connection, that's just not practical or useful. It "just doesn't work". So what I am trying to find out is how to easily find a distro that "just works" for me and my hardware (in this case an IBM ThinkPad T23).

Thanks for your responses, and I'll gladly accept any and all advice.

KC

---

