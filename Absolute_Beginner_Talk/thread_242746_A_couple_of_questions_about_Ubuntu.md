---
title: "A couple of questions about Ubuntu"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Akova on 2006-08-24
For the past few weeks I've been reading more and more about Linux and distros and I thought maybe I'd give it a chance. My computer restarts a lot with WinXP and programs give off random errors. This happens several times a day. In the beginning it was frustrating, now it's just accepted. It's to the point where the computer is mainly used by my younger brother for watching movies/tv-shows. I've heard people say the crashing stops with Linux, so the main question is: Will the crashing stop if I switch to Ubuntu?

Ubuntu seems to support/have alternatives to all the apps I use so no problem there.

This computer is part of a network where all the other computers are WinXP. It's easy to get files across. I was wondering if this will work with Ubuntu installed on one of the computers and XP on the rest? Also, we have a standard broadband internet connection that is split up between three computers, what will the install process be like?

I have two partitions on my single 80gb harddrive. One is 4gb for WinXP and the other one is for storage, so that when I need to format I just format 4gb. I was thinking of installing Ubuntu to the bigger partition but I've read that it will override the Windows XP startup files. If something doesn't work, or I just want to resort back to WinXP, will reinstalling WinXP be my only option?

I've been more attracted physically to Kubuntu and maybe I'll try it first because of the different desktop interface. Nothing else is different, right?

Lastly, I have a laptop next to this computer where I can visit all sorts of good things during the install and afterward. Any links other then the sticky'd link thread that I should be aware of?

That's all the questions I have for now, looking forward to the replies =)

---

### Post by benfindlay on 2006-08-24
Hey there

Firstly it depends whether your crashes are due to hardware violations. If it's due to some seriously screwed hardware, then there is a good chance it will still crash in ubuntu, However if they're caused by "Winblows" (which is more than likely) then an ubuntu installation will probably sort it out straight away.

You can install ubuntu into another partition than windows, and just by following through a few, fairrly self explanatory screens, you can set your partitions so that your windows install will still be there. It will also install GRUB boot loader for you, so when you turn your pc on, you can choose which OS you want to use each time. If you decide you dont like Ubuntu, then you just delete the OS in windows (i.e. reformat taht drive) and then reboot with your XP disc in, go to repair console and type "FIXMBR" and you're back to where you were before you tried Ubuntu.

Programs like videolan controller (vlc) media player will play just about any media file format there is (exceptions that come to mind are real player files and files with DRM in them). It also plays dvds rather well, and is an ideal player to use on older pcs with not too much memory.

Windows file sharing can be sorted rather easily using only 2 lines of code after you've installed Samba server. All in all, once I had read up on what I needed to do, it took about 2 minutes to get my ubuntu pc onto my home network! The sheer beauty of ubuntu is that it has a program called "Synaptic Package Manager" which installs programs for you via a GUI system (so you don't have to sit around typing horrendous code and tearing your hair out when dependencies are missing). There are plenty of guides out there for setting it up, and they're all very detailed, but if you're happy with the default settings for stuff (which works fine for my file sharing between windows and Ubuntu) then you literally need about 1% of the guide!

Your broadband connection will work straight "out of the box" as long as you have a router, and not just a modem (since you're running multiple pcs already I assume this is so!). Also, to state the obvious, you need an Ethernet card in the pc with Ubuntu on! :wink: 

Ubuntu, Kubuntu, Edubuntu, Xubuntu (am I missing any?) all work the same. Sure there are some cosmetic differences, and I think that a couple of system optionsa are located in different menus (due to the different desktops methods of functioning). There are plenty of KDE vs GNOME (i.e Kubuntu vs Edubbuntu) debates out there, with both sides making rather heated arguments why their chosen desktop is better. Personally I like GNOME and XFCE (ubuntu and Xubuntu). Many people say that KDE is power hungry and bloated, but I have only used KDE when booting Knoppix from a Live CD on an old P2 laptop. It ran fine, so I dont think the bloatedness claims are warranted.

In terms of links, you can't get much better than this forum. It's so comprehensive!

Anyways, hope this helps!

---

### Post by hotbrainz on 2006-08-24
Hello Akova,

I am not a pro Ubuntu User and switched to it just 4 months ago and have been quite satisfied with it.

Here are a few pointers with regard to your questions

> I've heard people say the crashing stops with Linux, so the main question is: Will the crashing stop if I switch to Ubuntu?

This may be a hardware fault. But yes, if this is due to some virus or some software incocnsistency then Ubuntu will be free of any such problems.

> This computer is part of a network where all the other computers are WinXP. It's easy to get files across. I was wondering if this will work with Ubuntu installed on one of the computers and XP on the rest? Also, we have a standard broadband internet connection that is split up between three computers, what will the install process be like?

Yup, its possible to network atleast for file sharing without any issues with the XP systems. You could use file sahring software like Samba share.

The broadband should not be an issue. But you might have to dig a bit in the forums to get it cofigured and running. As always, all you gotta to do is ask, there a lot of friendly folk here.

> I have two partitions on my single 80gb harddrive. One is 4gb for WinXP and the other one is for storage, so that when I need to format I just format 4gb. I was thinking of installing Ubuntu to the bigger partition but I've read that it will override the Windows XP startup files. If something doesn't work, or I just want to resort back to WinXP, will reinstalling WinXP be my only option?

It will be a very good idea to dual boot. That is , to have windows XP and Ubuntu with an option of choosing the OS at startup. This way you can get used to the Ubuntu system before you make a full conversion to Ubuntu.

Here is how you can do it:
[Dual Booting XP and Ubuntu]("http://users.bigpond.net.au/hermanzone/")

Kubuntu is one type of desktop. If you want this one then you have to install Kubuntu and not Ubuntu :)

The normal ubuntu has Gnome desktop. You may do the Ubuntu install and then get the kubuntu desktop to run on it as well. It is very easy to do that.

Go ahead and ask any other specific queries that you may have.

It may be a good idea to try the LIVE install session before anything else.
Hope this helps

Cheers

---

### Post by macogw on 2006-08-24
> **benfindlay said:**
> The sheer beauty of ubuntu is that it has a program called "Synaptic Package Manager" which installs programs for you via a GUI system (so you don't have to sit around typing horrendous code and tearing your hair out when dependencies are missing). 
It's not horrendous code.  It's one line.  You type:
sudo aptitude install nameofprogram
then enter your password.  It resolves all dependencies automatically when youuse aptitude.

> Ubuntu, Kubuntu, Edubuntu, Xubuntu (am I missing any?) all work the same. Sure there are some cosmetic differences, and I think that a couple of system optionsa are located in different menus (due to the different desktops methods of functioning). There are plenty of KDE vs GNOME (i.e Kubuntu vs Edubbuntu) debates out there, with both sides making rather heated arguments why their chosen desktop is better. Personally I like GNOME and XFCE (ubuntu and Xubuntu). Many people say that KDE is power hungry and bloated, but I have only used KDE when booting Knoppix from a Live CD on an old P2 laptop. It ran fine, so I dont think the bloatedness claims are warranted.
I have been told xfce is the least ram-hungry desktop.  I was told it because I said there's a chance the computer I want to use for testing Edgy will only have 128 mb of ram, and so I was told to use Xubuntu instead.

---

### Post by benfindlay on 2006-08-24
With reference to the horrendous code, I was referring to the preponderance of articles that list pages and pages of config files to be edited. By using Synaptic and just using the default settings for these configs it makes it much easier for a new user to get it working. The only real code required is to enable your user account with Samba.

And yes xfce is fantastic for low end machines as it is a much more lightweight desktop, but still looks good. Its also quite useful if you're familiar with and like Mac OS X, as it maintains much of the same look (whilst obviously doing things differently). The point is that, since the thread topic starter's pc has  an 80 gig hdd, then it is likely to be of decent spec, and therefore able to handle running more power-hungry desktops like KDE and GNOME.

---

### Post by RRS on 2006-08-24
[This site]("http://psychocats.net/ubuntu/windowstoubuntu.html") has an excellent tutorial on installing Ubuntu.

It's a good idea to run from the live cd for a few sessions before installing to explore and learn about how some things work before installing. This will also give a good "test" for hardware compatibility and if any special setup is needed for your internet connection.

Using the laptop to follow instructions while installing is a good idea. I used a KVM switch and a second machine myself the first time but a second monitor would've made reference even easier.

Both the site I've listed(Psychocats) and Herman's from the 3rd post also have a good bit of post installation tips.

Welcome aboard and let us know if you have any other questions.

---

