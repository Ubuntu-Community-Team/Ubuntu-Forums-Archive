---
title: "installing...just about anything"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Liger_XT5 on 2007-02-19
Howdy, I've recently decided to go to Linux and was told to use Kubuntu 6.10 for a beginner.
A lot of my friends, family, and co-workers consider me as a IT when it came to windows, but with recent problems with Microsoft, I decided to get a head start with Linux before things got ugly.

Thinking Linux would be a good challenge to tinker with and, well, have fun, I guess I took more than I could bite. :popcorn: 

Anyways, I'll get to the point.
The only thing that I have found as the most un welcomed surprise, I'm not upset, I was expecting some new things to learn, was the installing stuff like the drivers for my geforce card.
I've done a quick search on doing installing stuff, even checked the nvidia's forum about installing the Linux driver, but couldn't understand it.

So, the only thing I've been able to get working so far from the web  is firefox. So if anyone would LIke to help when they have the time, it would be grateful. I know how it feels to have new members because I have a forum to help players understand a game.

---

### Post by tronica on 2007-02-19
this is a great guide for newbies

[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

---

### Post by Liger_XT5 on 2007-02-19
Thanks, I'll take a look.

edit:
I have looked under the how to install, but that section I didn't quite understand. Do try to understand, I am completely new to any Linux programs.

---

### Post by aysiu on 2007-02-19
**Step 1**:
Read this to get a basic understanding of how software installation works.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Step 2**:
Enable extra repositories (you'll need to in order to get Nvidia drivers) by following these instructions.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 3**:
Go to KMenu > System > Adept Package Manager (see attached screenshot)

**Step 4**:
Search for the word *nvidia*--the specific packages you're looking for are *nvidia-glx* and *nvidia-kernel-common*. Click those and mark them for installation by clicking **Request install**. Then click **Apply Changes** to actually install the packages. (see other screenshot)

---

### Post by Maestro23 on 2007-02-19
> **Liger_XT5 said:**
> Thanks, I'll take a look.

edit:
I have looked under the how to install, but that section I didn't quite understand. Do try to understand, I am completely new to any Linux programs.

Welcome to the community. Couple of sites to get your feet wet:

Commands and File Structure:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

How to Install in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Restricted Formats(mp3 and DVD): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good luck.

---

### Post by aysiu on 2007-02-19
> **Maestro23 said:**
> 
How to Install in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/) While that's an excellent link, it's also Gnome-centric and would be confusing to a new Kubuntu user.

---

### Post by Liger_XT5 on 2007-02-19
Thanks, I have looked, tested it out by having it download wine, and it sounds a lot easier to understand than the other stuff that I've been coming acrossed.


edit:
I guess I forgo to refresh the page.
But yes, that link, [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/), was very helpful

Otherwise, I already have Kubuntu installed and what not, just needed a few things installed.

---

### Post by Bachstelze on 2007-02-19
It is not that much Gnome centered, It just uses Synaptic, which I would recomend to a new user since I find it more intuitive than Adept - in fact, I have it installed on my Debian even though I'm a KDE user.

---

### Post by Maestro23 on 2007-02-19
> **aysiu said:**
> While that's an excellent link, it's also Gnome-centric and would be confusing to a new Kubuntu user.

Good catch aysiu.  I didn't catch he was using Kubuntu.:)

*Oh well, long as he gets help.

---

### Post by Liger_XT5 on 2007-02-19
Thanks, and I thought I didn't look in detail. (hint below my avatar pic say the OS)

Anyways, I got a file, NVIDIA-Linux-x86-1.0-9746-pkg1.run, as it says .run, how would I put it in the konsole?

---

### Post by aysiu on 2007-02-19
> **Liger_XT5 said:**
> Thanks, and I thought I didn't look in detail. (hint below my avatar pic say the OS)

Anyways, I got a file, NVIDIA-Linux-x86-1.0-9746-pkg1.run, as it says .run, how would I put it in the konsole?
Don't bother.

Read post #4 in this thread. I've revised it to be a bit clearer.

It will not only help you get Nvidia drivers installed but it will also give you a better understanding of how to install software in general.

---

### Post by Liger_XT5 on 2007-02-19
Thank you. I have got to admit, this is one of the most, no, this is the most helpful, yet nicely adidtude forum I have ever come accrossed in my life, even a nicer additude then the forum I'm working with, just can't find good help for staff. Lol.

---

### Post by tubasoldier on 2007-02-19
> **Liger_XT5 said:**
> Thanks, and I thought I didn't look in detail. (hint below my avatar pic say the OS)

Anyways, I got a file, NVIDIA-Linux-x86-1.0-9746-pkg1.run, as it says .run, how would I put it in the konsole?


First of all you can not install the Nvidia drivers from the graphical interface.

but you would want to install a few things in order to install those anyways.

```
 sudo apt-get install build-essentials
```

Then you need to stop kdm for Kubuntu, or gdm for Ubuntu

```
/etc/init.d/kdm stop (Kubuntu) or /etc/init.d/gdm stop (Ubuntu)
```

then you have to log in

after you log in you need root privileges. I do believe that you need full root and not just sudo. That is best achieved by
```
sudo bash
and then by typing
su
```

Make sure you are in the directory that you have the driver saved in.
Then you can start the graphics driver install. 
```
sh NVIDIA......run
```
hint: press the tab button after typing NVIDIA


OR you could install the nvida-glx package from the repositories

```
sudo apt-get install nvidia-glx
```

---

### Post by aysiu on 2007-02-20
> **tubasoldier said:**
> First of all you can not install the Nvidia drivers from the graphical interface. > OR you could install the nvida-glx package from the repositories

```
sudo apt-get install nvidia-glx
``` Of course you can install Nvidia drivers from the graphical interface. Adept Package Manager (Kubuntu) and Synaptic Package Manager (Xubuntu / Ubuntu) are just graphical frontends for *apt-get*.

---

### Post by skyhopper88 on 2007-02-20
I would suggest using the envy script for graphic driver installations (ATI or Nvidia). Some like it, some don't. But it's an option that's out there.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Liger_XT5 on 2007-02-20
thanks, but aysiu's tip helped, just need to figure how to get it to enable my second monitor witch is a nvidia quadro.
it detects it, but both monitors go to 640x480, and it says the card is a geforce 2, not quadro.

I can't say what it is exactly, I baught it from a scrapped out pc, but the card work beautiful on windows.

---

