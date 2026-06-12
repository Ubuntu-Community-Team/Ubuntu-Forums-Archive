---
title: "Which ISO to download - desktop or alternate or server?"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by rvbhute on 2006-05-29
Which ISO should I download if I want to keep a CD as my first repository? Does the Ubuntu Desktop CD, which is a live CD, serve as a repository in Synaptic? 

I googled and found out that alternate and server CDs will be having the packages on them; so they will do as respositories. But is the alternate CD ok for a simple home-user text-install like the previous Ubuntu releases?

---

### Post by Sef on 2006-05-29
I would just download Ubuntu.  You can set it up as a server, if you so desire.

---

### Post by rvbhute on 2006-05-29
But which? - They have spoilt me with choices - Desktop or Alternate? I would like to go for Desktop (who doesn't love a live CD which can do a hdinstall) if I'm sure that it can used in Synaptic after the installation.

---

### Post by jimrz on 2006-05-29
[QUOTE=rvbhute]But which? - They have spoilt me with choices - Desktop or Alternate? I would like to go for Desktop (who doesn't love a live CD which can do a hdinstall) if I'm sure that it can used in Synaptic after the installation.[/QUOTE]

i used ubuntu dapper rc alternate Saturday on my laptop and it worked beautifully. and, thus far, so does dapper

---

### Post by barbarian on 2006-05-29
From now:
LiveCD-Desktop 
InstallCD-Alternate

---

### Post by mcduck on 2006-05-29
[QUOTE=barbarian]From now:
LiveCD-Desktop 
InstallCD-Alternate[/QUOTE]
Not exactly.. 

Desktop = Live CD with GUI installer, this is what most people want.
Alternate = text-mode installer (the same that was in previous Ubuntu versions) for OEM and RAID installs, and for those who want to do expert install or more complex partitioning etc.

So both CD's are able to install Ubuntu, only the Alternate has more options for those who need them.

Also, I'm pretty sure that the Desktop-CD doesn't work as repo for Synaptic, so if you need that, get the Alternate CD :)

---

### Post by RAV TUX on 2006-05-29
[quote=mcduck]Not exactly.. 

Desktop = Live CD with GUI installer, this is what most people want.
Alternate = text-mode installer (the same that was in previous Ubuntu versions) for OEM and RAID installs, and for those who want to do expert install or more complex partitioning etc.

So both CD's are able to install Ubuntu, only the Alternate has more options for those who need them.

Also, I'm pretty sure that the Desktop-CD doesn't work as repo for Synaptic, so if you need that, get the Alternate CD :)[/quote]


when you say most people want this I am not sure who you are refering to as most people?

I downloaded and burned both desktop and alternate, I only used the alternate (AKA install CD).

I would suggest for experienced Ubuntu users even newbies who are fimilar with Ubuntu like myself just stick with the alternate CD, others my disagree but that is my suggestion.

---

### Post by rvbhute on 2006-05-29
[QUOTE=mcduck]Also, I'm pretty sure that the Desktop-CD doesn't work as repo for Synaptic, so if you need that, get the Alternate CD :)[/QUOTE]

Alternate it is then! :)

---

### Post by mcduck on 2006-05-29
[QUOTE=yozef]when you say most people want this I am not sure who you are refering to as most people?

I downloaded and burned both desktop and alternate, I only used the alternate (AKA install CD).

I would suggest for experienced Ubuntu users even newbies who are fimilar with Ubuntu like myself just stick with the alternate CD, others my disagree but that is my suggestion.[/QUOTE]
Well, based on how many people have been complaining about the text-mode install with previous Ubuntu version, and the fact that the Desktop CD is what you get with ShipIt, and that it does everything that all those people with no special needs at install time need, I'm pretty sure that most people only need the Desktop CD :)

---

### Post by morgs on 2006-05-29
[QUOTE=yozef]I would suggest for experienced Ubuntu users even newbies who are fimilar with Ubuntu like myself just stick with the alternate CD, others my disagree but that is my suggestion.[/QUOTE]

I definitely prefer the alternate CD, however shipit.ubuntu.com will only be sending the Desktop (Live) CDs.

If you have time for testing before the release, definitely give the Desktop CD installer (called Ubiquity) a try - it's worth catching as many bugs as possible before the release, since the Desktop CD is what many new users will be getting through shipit.

---

### Post by barbarian on 2006-05-29
> that all those people with no special needs at install time need, I'm pretty sure that most people only need the Desktop CD

Not exactly, in general, you can't always ignore command line in linux, IMHO :)

---

### Post by mcduck on 2006-05-29
[QUOTE=barbarian]Not exactly, in general, you can't always ignore command line in linux, IMHO :)[/QUOTE]
I think you have misunderstood what we are talking about :rolleyes: 

Question is about differences between Ubuntu 6.06 Desktop and Alternate CD's.

Both cd's install exactly the same Ubuntu system, with GUI and command line..

Only difference is that the Desktop CD is a live-cd that includes a GUI installer to install Ubuntu to your hard drive, whereas Alternate CD is a plain text-mode installer CD like the Breezy Install disk is.

The Desktop CD is able to do all basic installs, including dual boot with windows and such, but the Alternate CD can do OEM install and other things most people won't need.

What comes to ignoring command line, if someday people are able to use and administrate linux systems without using CLI, that's great for them and fine by me, I'll use CLI anyway :D

---

### Post by zhoux on 2006-05-29
I personally found that the text-based or alternate installer to be easier to install.

---

### Post by barbarian on 2006-05-29
> I'm pretty sure that most people only need the Desktop CD

I have answered to your particular statement. In case, if you haven't noticed quote text.:D

---

### Post by az on 2006-05-29
[QUOTE=rvbhute]Does the Ubuntu Desktop CD, which is a live CD, serve as a repository in Synaptic? 
[/QUOTE]

Why do you ask?  What is it in partitcular that you need?  To dist-upgrade from breezy to Dapper without net access?  Then use the alternate cd.

The Desktop cd does contain a small repository of packages needed if you have to compile an extra kernel module (linux-headers, build-essential, other networking stuff like linux-wlan-ng) but you cannot dist-upgrade from the Dekstop cd like you could with the alternate cd.

---

### Post by rvbhute on 2006-05-30
[QUOTE=azz]Why do you ask?  What is it in partitcular that you need?  To dist-upgrade from breezy to Dapper without net access?  Then use the alternate cd.

The Desktop cd does contain a small repository of packages needed if you have to compile an extra kernel module (linux-headers, build-essential, other networking stuff like linux-wlan-ng) but you cannot dist-upgrade from the Dekstop cd like you could with the alternate cd.[/QUOTE]

Well, it would take me around 6-7 days to download the CD - which is still faster than a Shipit delivery. That took 5-6 weeks :). With speeds of 4-5 kBps, I would want to ensure than the CD stays useful after the install, atleast until the first upgrades are available. 

The dist-upgrade option sounds interesting  - but I also want to increase the partition size this time around, so I'm doing a clean install.

---

### Post by mrweirdo on 2006-05-30
so my question is does the alternate allow you to install the server? reason I ask is I have some systems that are desktops and some that run as servers. It would be nice to only have to have one cd around for both systems.

---

### Post by rvbhute on 2006-05-30
Yes. I think both are same, only server gives you a non-GUI environment. Install using the alternate, add whatever you want - dhcp, http, ftp.

---

### Post by mcduck on 2006-05-30
[QUOTE=barbarian]I have answered to your particular statement. In case, if you haven't noticed quote text.:D[/QUOTE]
Sure, I did notice it. I just don't see how using the 'Desktop CD' to install Ubuntu is 'ignoring command-line'.. :confused:

---

### Post by barbarian on 2006-05-30
Ok you won, you know, you are picky..](*,)  
I just compared text mode install with using CLI. Most linux newcomers should get accustomed to text input. The earlier they understood it, the easier live with linux. So text mode install - perfect  way for beginning,** IMHO.**

---

### Post by az on 2006-05-30
[QUOTE=barbarian]Most linux newcomers should get accustomed to text input. The earlier they understood it, the easier live with linux. So text mode install - perfect  way for beginning,** IMHO.**[/QUOTE]

You are entitled to your opinion, however I think the vast majority of people dissagree with that.  You should never need to drop to the command line to run your Desktop box.  Ever.  

It should just work.

If you compare the stuff that just worked even just two years ago to the stuff that just works today, you will see how fast we are getting there.

I think that the majority of people who will install and run Dapper will not need to drop to the command line to get something done.

---

### Post by barbarian on 2006-05-30
sorry for offtopic, last thing.

Ok, somehow you right, linux aspire to desktop.


But,
> The majority of people, able to use their mobile phones nowadays, with no problems, but earlier it was wonder of engineering.:cool:

---

