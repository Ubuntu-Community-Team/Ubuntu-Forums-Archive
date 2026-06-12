---
title: "Almost a Convert"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by coldphyre on 2008-03-13
I'm an avid XP user, have been for years. I'm also work in IT. I've toyed with Ubuntu in the past and I'm definitely  impressed with it. Also, I'm currently in college working on a dual major and one of my current classes requires me to use Microsoft SQL Server 2005 Developer's Edition.

Here's a list of programs that I need to work on Ubuntu:

World of Warcraft (which I've seen tutorials on how to get working)
Microsoft Office 2007 (which I've been told will work in Wine/Crossover)
and finally Microsoft SQL Server (which I'm unsure about)

If anyone has any pre-apocalyptic input for me before I run with the scissors this weekend by formating my computer and throwing Ubuntu on it, I would appreciate.


Thanks, 

~Coldphyre~

---

### Post by jseiser on 2008-03-13
I was in your situation. I only use linux, then had to take a visual basic class, and a sql class.  Since they gave me a free copy of windows with that software, i just bought a used 40gb sata drive for 10 bucks, hooked it up, put windows on it, those programs, and i do my class work on them.  I just make sure that when i change something, either here or at school, it gets copied back to the thumbdrive in case my windows HD died or something. You other option would be to run windows in a vm inside ubuntu, and do all your work in it.  It would be a lot more stable i imagine then running wine/crossover for somthing critical like school work.  Wine is awesome, those people work wonders coding that software with what they are given.  But its not enterprise ready, they cant guarantee that the software working on wine version 1, will still work on wine 1.1 - they fix general bugs, not software specific bugs, correct me if im wrong.


edit : wow through wine would be fine, if it crashes, wait for the update or dont play, but if sql and wine had a problem, your then stuck unusable software that you need to use.

---

### Post by gobuntu on 2008-03-13
Hi,

Why not just a typical and simple dual boot installation?

Much better, even, create an NTFS data partition, which Ubuntu can easily read and write-to. That way it's an on-going aproach.

---

### Post by gashcr on 2008-03-13
[QUOTE=]
Microsoft Office 2007 (which I've been told will work in Wine/Crossover)
[/QUOTE]

Just curious... is there a heavyweight reason you need to use it... or just personal preferences??

---

### Post by aysiu on 2008-03-13
It sounds as if you are better off using Windows... or at least Windows as a dual boot or virtual machine within Ubuntu.

---

### Post by coldphyre on 2008-03-13
My college prefers us use Office '07 due to the fact that they are using it now and all of their files are saved with those pesky new M$ extensions. I really want to switch to linux, getting sick of windows. However, I did think about it after posting that maybe a dual boot system wouldn't be a bad idea just for school work, there's no particular reason that **I** like to use windows or office 2007 myself. Thanks for the advice!

~Coldphyre~

---

### Post by handydan918 on 2008-03-13
I'm certainly not a DBA, but I was under the impression that MySQL was pretty much on par with M/S SQL...and probably more widely deployed.

---

### Post by Eclipse. on 2008-03-13
I would dual boot, use xp when you need to and ubuntu for everything else.:)

---

### Post by Sef on 2008-03-13
> Why not just a typical and simple dual boot installation?

To set up a dual boot, read [Psychocat's Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing").

---

### Post by livingtarget on 2008-03-13
If you just need office for word processing than you can just do it in openoffice and export it to .pdf if you need to hand it in. PDF format should be allowed and it will look the same on any system I've found.

Just ask if you can submit PDF's and that's you set.

---

### Post by Nythain on 2008-03-13
Id go with a virtual windows install inside of ubuntu if you got the ram for it (not to much more if your talkin xp, maybe give it 512)

I hate suggesting dual booting scenarios, because like me, a lot of people just end up staying in windows instead of spending the time they need to learn and figure out ubuntu... but with a virtual machine install of windows, you can stay in ubuntu, then just load up windows when you need to run an app or two (wine should handle wow pretty well, at least it has for me for the last couple years) then shut it down when your done, or hell, if you have the memory, just leave it runnin in the background while playing around in ubuntu

if you needed it for more than just office and sql i would be more apt to suggest the dual boot, but a shutdown and reboot just to use 2 apps seems sort of silly really...

---

### Post by coldphyre on 2008-03-13
I appreciate the information. Now, I've run virtual machines inside windows before, if I were to run XP inside of say... vmware, would I be able to install and retain the programs? Like office (for access mostly) and SQL Server 2005? The SQL install is a true pain in the ****. ......funny, i work in IT and don't know this...

---

### Post by handydan918 on 2008-03-14
you should be able to install programs in a VM guest. I use Vbox, and it works for me.

---

### Post by coldphyre on 2008-03-14
Cool, I'll give it a shot this weekend, worse comes to worse I'll just have to load windows on that extra 20GB of space I set aside for just such a situation. 

Vbox here I come.

---

### Post by e4tmyl33t on 2008-03-15
Just be sure to remember, if you left that space blank for that and then install windows, you'll need to make sure to re-install your boot manager because Windows will take over the master boot record and only boot to itself. Not sure if that had been pointed out or not.

---

