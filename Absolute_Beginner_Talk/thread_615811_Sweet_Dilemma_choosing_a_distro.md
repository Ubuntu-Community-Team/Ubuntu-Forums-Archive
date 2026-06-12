---
title: "Sweet Dilemma choosing a distro"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-11-17
My sister has an old laptop. The config is :

1.13-GHz/733-MHz Pentium III-M CPU, 
256MB of SDRAM, 				512KB L2 cache, 
Windows XP Professional, 15-inch 				active-matrix screen, 
NVidia GeForce2 Go graphics with 32MB 				of DDR SDRAM, 
30GB hard drive, 
8X DVD-ROM and 8X/8X/24X 				CD-RW combination drive, 
built-in V.90 modem and network 				adapter, 
touchpad and eraserhead pointing devices

I was wondering which distro to install. I am currently looking at DSL, Puppy and fluxbuntu.

I want to install a different distro so that I can find out how the other OS'es are. But on the other hand I am very comfortable with ubuntu since I have been using it since Breezy Badger.

So the question is: Should I go with a newer distro or stick to Fluxbuntu since I will be able to help my sis out remotely if i have to.

Which one would be a better option ?
I mean the basic commands and such would be the same. Will the other OS'es like DSL or Puppy be very different than ubuntu?

Your views?

---

### Post by Arthur Archnix on 2007-11-17
I'd install xubuntu 7.1 for the support and true desktop feel. Remove some apps, disable some services, you're laughing on that hardware. I don't know what the support for fluxbuntu is like, nor how friendly your sister would find fluxbox.

DSL and Puppy, I used DSL a while back, it was nothing like i would expect an os to be. I certainly wouldn't give one of those to my sister.

I've had xp running on a weaker system than that. Give her comfort and familiarity before performance.

That's my two cents.

---

### Post by rsambuca on 2007-11-17
Have you considered a Minimal Installation of *buntu?  It installs just the most basic elements to get you started, and then you only add the components you need, such as X, a DE/WM, login manager, etc.  [You can find insructions here]("https://help.ubuntu.com/community/Installation/LowMemorySystems").  This is also good to do on a new machine if you know what you want, as it is much faster than the default Ubuntu installation.  The instructions are very easy to follow.

---

### Post by Inxsible on 2007-11-17
> **rsambuca said:**
> Have you considered a Minimal Installation of *buntu?  It installs just the most basic elements to get you started, and then you only add the components you need, such as X, a DE/WM, login manager, etc.  [You can find insructions here]("https://help.ubuntu.com/community/Installation/LowMemorySystems").  This is also good to do on a new machine if you know what you want, as it is much faster than the default Ubuntu installation.  The instructions are very easy to follow.That seems like a good idea. But then how do you know which apps will be heavy on the resources etc. For instance when I am choosing a file manager, lets say, how do i find out whether nautilus would be better or dolphin or thunar etc. ?

---

### Post by Arthur Archnix on 2007-11-17
It's far, far easier to install a complete DE then remove uneeded components, than it is to install a bare-bones cli and build one up. I tried once and wouldn't recommend it unless you want to learn a lot about ubuntu or the target system couldn't support a xubuntu install from alt cd. 

THat's four cents now. ;)

---

### Post by rsambuca on 2007-11-17
> **Inxsible said:**
> That seems like a good idea. But then how do you know which apps will be heavy on the resources etc. For instance when I am choosing a file manager, lets say, how do i find out whether nautilus would be better or dolphin or thunar etc. ?

For lean and mean, the most important thing is to make sure you don't mix your libraries.  Stick to one set, like gtk.  Thunar is probably one of the lighter file managers.  As soon as you start running QT and gtk apps on a low resources machine, you really bog things down.

---

### Post by rsambuca on 2007-11-17
> **Arthur Archnix said:**
> It's far, far easier to install a complete DE then remove uneeded components, than it is to install a bare-bones cli and build one up. I tried once and wouldn't recommend it unless you want to learn a lot about ubuntu or the target system couldn't support a xubuntu install from alt cd. 

THat's four cents now. ;)

I agree it is definitely way easier in some aspects, but I find it is very difficult to achieve the same efficiency with the reverse method.  Trying to hunt down every little daemon and determine whether it is essential to your OS is near impossible.  Sometimes it is just easier to start with nothing, install the stuff you know you need, and then see what happens!  If you need something else down the line, just add it.

---

### Post by Inxsible on 2007-11-17
> **rsambuca said:**
> For lean and mean, the most important thing is to make sure you don't mix your libraries.  Stick to one set, like gtk.  Thunar is probably one of the lighter file managers.  As soon as you start running QT and gtk apps on a low resources machine, you really bog things down.See that's exactly what I mean. If I build a bare bones machine, I will have to find out the same thing about every app and then contend with it.

I think I would go with installing a complete DM and then removing something if i dont like it, like Arthur Archnix suggested too.

Remember, this machine would not be with me, but my sister. So I need to be able to support her remotely too. This is not the first time she is using computers, and she has dabbled in linux before too. but she may need names etc of apps or packages to do something in particular. With that in mind, i am more inclined towards fluxbuntu or xubuntu.

Just that trying out different distros appeals to me and that's why I was wondering if installing DSL or Puppy would be a good idea.

---

### Post by Frak on 2007-11-17
[ubuntu-lite]("http://ubuntulite.tuxfamily.org/")?

---

### Post by Inxsible on 2007-11-17
> **Frak said:**
> [ubuntu-lite]("http://ubuntulite.tuxfamily.org/")?I didnt know about that one. Let me have a look at it. Thanks

---

### Post by Colro on 2007-11-17
I'd personally go with a minimal Slackware install on that kind of hardware, it tends to run very well on older machines. It's not the most user friendly thing on the block, though, so if you're not confident in your ability to configure something like that then I wouldn't risk it. 
I don't really like Puppy or DSL, but that's just me. I'm sure either would run just fine, but they are quite a bit different from the *buntu distros. Xubuntu/Fluxbuntu may both still be kind of slow on that hardware. Really, your limiting factor is your RAM. If you added 512mb+ (probably fairly cheap), you'd be able to run pretty much any distro you want as long as you didn't touch the graphical desktop effects.

---

### Post by rsambuca on 2007-11-17
> **Inxsible said:**
> See that's exactly what I mean. If I build a bare bones machine, I will have to find out the same thing about every app and then contend with it.

I think I would go with installing a complete DM and then removing something if i dont like it, like Arthur Archnix suggested too.

Remember, this machine would not be with me, but my sister. So I need to be able to support her remotely too. This is not the first time she is using computers, and she has dabbled in linux before too. but she may need names etc of apps or packages to do something in particular. With that in mind, i am more inclined towards fluxbuntu or xubuntu.

Just that trying out different distros appeals to me and that's why I was wondering if installing DSL or Puppy would be a good idea.

Yeah, no problem.  I still think it wouldn't hurt to try though - you might surprise yourself.  If you ever get stuck, you can always just "sudo apt-get install xubuntu-desktop" or "sudo apt-get install xfce4" for a lighterweight version, and then you have everything you need anyways.

---

### Post by Inxsible on 2007-11-17
> **Colro said:**
> I'd personally go with a minimal Slackware install on that kind of hardware, it tends to run very well on older machines. It's not the most user friendly thing on the block, though, so if you're not confident in your ability to configure something like that then I wouldn't risk it. 
I don't really like Puppy or DSL, but that's just me. I'm sure either would run just fine, but they are quite a bit different from the *buntu distros. Xubuntu/Fluxbuntu may both still be kind of slow on that hardware. Really, your limiting factor is your RAM. If you added 512mb+ (probably fairly cheap), you'd be able to run pretty much any distro you want as long as you didn't touch the graphical desktop effects.
The machine is about 6 years old now and my sis has no intention of upgrading anything in it including RAM.

She wants to primarily use the laptop for three things:

1) Remote Login to her office machine (Most important). Her company has proprietary VPN software that she has to use. They do have a linux version she said. Probably its a tar gz. so that its not restricted to a particular distro
2) Surf the internet
3) Use the messengers once in a while

What makes you say that x/Flux will also be slow on the machine, only the RAM? The specs on their respective site says that it would even work with 128MB RAM.

---

### Post by Inxsible on 2007-11-17
> **rsambuca said:**
> Yeah, no problem.  I still think it wouldn't hurt to try though - you might surprise yourself.  If you ever get stuck, you can always just "sudo apt-get install xubuntu-desktop" or "sudo apt-get install xfce4" for a lighterweight version, and then you have everything you need anyways.That is true too :D

That's why the dilemma ;)

---

### Post by Frak on 2007-11-17
Ubuntu-lite has the smallest footprint of anything out there.

---

### Post by Colro on 2007-11-17
> What makes you say that x/Flux will also be slow on the machine, only the RAM? The specs on their respective site says that it would even work with 128MB RAM.

Pretty much. I could be entirely wrong, though, so don't let my words prevent you from trying them out :)

---

### Post by Inxsible on 2007-11-17
To summarize, my list is now;
1) Fluxbuntu
2) Ubuntulite
3) DSL
4) Puppy Linux

I guess I could burn 4 Live CD's and check them each out on her machine when I see her on Thanksgiving :)

I might even try the minimal install, if I have enough time after a heavy turkey dinner :D

Thanks guys

---

### Post by Inxsible on 2007-11-17
I am reading up on the minimalist ubuntu install and it looks pretty straight forward. 

It could be a viable option when I do this next week :)

---

### Post by Arthur Archnix on 2007-11-17
If that's the route you go, I'll expect my four cents back. :P

---

### Post by Inxsible on 2007-11-17
> **Arthur Archnix said:**
> If that's the route you go, I'll expect my four cents back. :P
LOL. Do you take checks ;)

---

### Post by oldos2er on 2007-11-17
Vector Linux standard is good on older systems too.

---

### Post by ferebee on 2007-11-17
I run Ubuntu Gutsy on a machine with similar specs - pIII 600mhz Nvidia Geforce4 mx 440, 640mb ram - multi booting with winxp pro, Puppy, and PclinuxOS - A full Ubuntu install runs just fine on my machine. 

It's no speed demon, but it's faster than XP, not as fast as Puppy - I think Ubuntu might be a better choice for a linux beginner though. Ubuntu with Xfce installed has worked well for me in the past.

---

### Post by Inxsible on 2007-11-17
> **ferebee said:**
> I run Ubuntu Gutsy on a machine with similar specs - pIII 600mhz Nvidia Geforce4 mx 440, 684mb ram - multi booting with winxp pro, Puppy, and PclinuxOS - A full Ubuntu install runs just fine on my machine. 

It's no speed demon, but it's faster than XP, not as fast as Puppy - I think Ubuntu might be a better choice for a linux beginner though. Ubuntu with Xfce installed has worked well for me in the past.Yeah I need a fast OS on there. My sis is getting back into the Linux world and I don't want her to tell me that Windows was better. So Ubuntu is pretty much out.

Curiosity : Will I be able to run Compiz on Fluxbuntu ? If not, is it because of the video card (32 MB video card) or just that fluxbuntu can't handle compiz?

I would like to know how much eye candy can I add to dazzle her. :)

---

### Post by gn2 on 2007-11-17
I can thoroughly recommend Xubuntu 7.04, installed from the Alternate CD.
I run it on a P3 500mhz 192mb RAM laptop and it's very useable, not too slow at all, much faster than W2kPro which it used to run.

For increased performance Gnome and KDE services can be stopped from loading at boot.

Another good distro to look at is Linux Mint XFCE Community Edition: [http://www.linuxmint.com/mirrors.php?id=14](http://www.linuxmint.com/mirrors.php?id=14)

Also Sam Linux: [http://sam.hipsurfer.com/](http://sam.hipsurfer.com/)

Maybe Zenwalk: [http://www.zenwalk.org/](http://www.zenwalk.org/)

All will run fine on your PC.

---

### Post by ugm6hr on 2007-11-18
> **Inxsible said:**
> To summarize, my list is now;
1) Fluxbuntu
2) Ubuntulite
3) DSL
4) Puppy Linux

I guess I could burn 4 Live CD's and check them each out on her machine when I see her on Thanksgiving :)

I might even try the minimal install, if I have enough time after a heavy turkey dinner :D

Thanks guys

If you are going down the minimal install route - if you haven't already seen this:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
IceWM and Thunar as Desktop / File Managers will seem intuitive for someone from Windows.

I personally wouldn't choose DSL (Fluxbox-based) for someone who is not well-versed in Linux.  Doing simple tasks like mounting and unmounting USB sticks can be tricky if you aren't familiar with Terminal, and will appear to be a backwards step from XP.

Puppy is a good choice to try.  I haven't used it since 2.14, so I suspect it has come on in leaps and bounds in terms of usability since then.

Ubuntu-lite seems a good idea, although Openbox will take some getting used to from a Windows background.

Just thought I'd offer a different viewpoint....

PS: I put Xubuntu 7.04 on an old laptop for my sister for web-surfing, yahoo email access, and as an mp3 jukebox.  A veritable success, and she preferred it to XP.  But she went back to Windows when her work gave her a newer faster laptop with XP-preinstalled.

---

