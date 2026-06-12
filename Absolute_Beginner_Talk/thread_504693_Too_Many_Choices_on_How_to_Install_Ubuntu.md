---
title: "Too Many Choices on How to Install Ubuntu"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by porcorosso on 2007-07-19
I have Vista Business running on a notebook computer with 2 gigs of RAM, a 60 gig primary hard drive, and a bay with swappable 80 gig hard drive / DVD writer. I also have an external USB DVD writer. I need to keep Vista business (on ntfs) running on that primary drive.

I'd like to install Ubuntu 7.04 and test it. Can't make up my mind whether --

a) it's best to just install Ubuntu on the second drive and change boot order in BIOS setup for selecting which OS to run or

b) it's best to try Ubuntu on a virtual machine, from within VPC 2007 or VMWare Player 2.0

Does anyone here have experience using Ubuntu under a virtual machine with Vista as the Host OS? Can I install VMWare Player 2.0 and just use my Ubuntu 7.04 CD (or an .iso) to install Ubuntu under the player? Or do I have to use an appliance for this?

I already tried to install Ubuntu under VPC 2007, but ran into a few issues. Not sure whether they are solvable or not. I'd rather use the VMWare product if possible, anyway. If I understand what I've read so far I'll be able to use my USB devices on the host from within the Ubuntu virtual machine.

The thing is, installing Ubuntu on the second drive seems like a good idea, but then I have to lug around the external DVD drive all the time -- at least if I want an optical drive to be available when I'm using Ubuntu. On the other hand, I'm worried that I'll be running into all sorts of artificial restrictions trying to run Ubuntu within a virtual machine.

Thanks for any suggestions you can make to help me make up my mind.

---

### Post by -=Viper=- on 2007-07-19
you know dude that you can just run the live disk (it does not install but you can try it out)  just boot with the live disk in and you can try it.

---

### Post by lord_zerg on 2007-07-19
if you only want to try the OS the live cd may be your best choice.
if you're are set on installing the OS, well, i would install it on the second drive. the simple solution i guess.

---

### Post by phidia on 2007-07-19
There are lots of ways to install linux/ubuntu I think that's a good thing. I agree that using the live cd is your best and easiest choice. Running from a live cd will tell you how well your hardware is supported.

You didn't ask but you could also install to a usb drive (given that some thumb drives are pretty large and always seem to be dropping in price) Liink to the many ways to [install ubuntu]("https://help.ubuntu.com/community/Installation").

---

### Post by porcorosso on 2007-07-19
Thanks. I should have mentioned that I've already fiddled around with the Live CD. It's nice, but it's darned slow, and I want to be able to configure and customize the installation. I want to learn to really use the OS, not just look around in it -- you know what I mean?

I think you're right to suggest that it will just be easier to install on the second hard drive -- rather than fiddling around with virtual machines. I've been using MS Virtual PC with several Windows operating systems running in their own virtual network. That has been very instructive and useful, but it looks as though VPC isn't going to play very nicely with Ubuntu.

I was hoping that someone might have had some experience running Ubuntu under a VMWare Player VM and might have some observations for me. It sounds like the player is pretty nice -- especially in that it lets you use USB devices with the guest operating systems.

If someone has run Ubuntu under a VMWare virtual machine and can throw me a lifeline I'd appreciate it. If not, I'll follow the sound advice already given and just stick it on the second drive.

Thanks!

Edit: I agree that it's nice that there are a lot of ways to install Ubuntu, but it does require quite a bit of head-scratching as I try to figure out what's going to work best in my particular situation. Thank you for that link to the community documentation location on installation. I also found Wubi, which looks almost too good to be true. They claim it's not emulation, but it's installed under Windows as though it were an application. I'm going to have to learn more about the technology before I got that route.

---

