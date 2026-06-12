---
title: "Some questions before installing ubuntu on a laptop"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Venerence on 2007-07-11
(threads I looked at first to avoid the "use search" argument :) )
_[Quick questions about laptops](http://ubuntuforums.org/showthread.php?t=181550)_: *Why it doesn't answer my question* - This thread is for largely older laptops, so it is largely irrelevant
_[Questions about laptops](http://ubuntuforums.org/showthread.php?t=99848)_: *Why it doesn't answer my question* - It does address a question I ask, but it's too specific for what I want to know
And of course I've all the stickies in this thread, though it's very possible I missed some information

So I have decided, as a fun project, to install ubuntu on my _[ASUS F3JP](http://www.asus.com/products4.aspx?l1=5&l2=26&l3=316&model=1358&modelmenu=2)_ laptop. After doing some research though, I have some questions before I jump into the installation and making everything work.

First, I found a compatibility chart for the ASUS _[here](http://members.ozemail.com.au/~tony.young/asusf3jpmdk2007.html)_. Note that the compatibility chart is for mandriva and not for ubuntu. For the most part it seems that everything works, and for what doesn't, he provides workarounds. Unfortunately, the workarounds are jargon to me. I'm not expecting answers on how to implement it (yet!), as I'll definitely wait until I have installed and gotten the basics worked out before I do that. However, I do want to know how intensive these fixes are. Is it worth my time to go ahead with the installation, or should I find a more compatible distro (assuming there's one out there that provides similar compatibility charts).

Also, as the distro he used for compatibility is mandriva, should I expect more or less compatibility with ubuntu?

I am also wondering about battery management tools. Do they exist for ubuntu? Is there options such as fan speed reduction, cutting back clockspeed, dimming the monitor? In battery saving mode for windows my laptop can run for ~3 hours, and on average I use battery power for about two hours. Without a good battery management tool, linux probably won't work out for me.

Finally, how compatible is linux with windows networks? Does it support workgroups, can routers handle a connection from a linux based computer? My first thought is yes as the protocols are probably the same, but still I want to be certain before I install ubuntu.

Thanks for taking the team to read these questions, and I'm looking forward to trying out ubuntu if it is right for me!

EDIT: [Here](http://www.w1ldt4ng3nt.net/blog/item/77) is a Ubuntu compatibility chart for a nearly identical model of the laptop.

---

### Post by Zzl1xndd on 2007-07-11
I would say it is worth the time. I have never looked back at windows after I got over the Learning curve. There is a battery management tool I have not adjusted any of the setting s with mine as I have been getting about 3 hours. I do networking with windows all the time works great.

---

### Post by serfcx on 2007-07-11
Try the live CD, if that works then you should be OK to install

---

### Post by Venerence on 2007-07-11
So I have downloaded and burned the live-cd, and have run into one particular problem while installing.

Halfway through the boot-up from the cd, I get the following error:
> Failed to start the X server (your graphical interface). It is likely this is not set up correctly.

At this point, it doesn't continue any farther, and doesn't accept any commands (at least none that I know of) until I tell it to shut down.

As I the f3jp comes with a radeon x1700, I'm guessing this problem is related to [this](http://ubuntuforums.org/showthread.php?t=414194). The problem with that solution is that I don't want to install ubuntu completely without trying it out from the CD. Is there a way to resolve this problem using the live cd?

---

### Post by orbital on 2007-07-11
Have you tried to boot the live cd with the following commands?

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

I have an ATI card and had the same problem and I was able to boot following the instructions on that thread.

---

### Post by orbital on 2007-07-11
When you get the "Failed to start the X server (your graphical interface). It is likely this is not set up correctly"

Type:

sudo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

startx


It should boot into the live cd.

---

### Post by Venerence on 2007-07-11
couple problems with that. First, with the live CD, the network hasn't been established yet (I think). Since I don't know how to set up my network (assuming the wireless hardware can even be recognized), I can't connect to the internet to download from any repositories. If someone could provide a command-line way to connect to the internet via wireless, then I would be able to do that. Otherwise, I have to find a way to do it offline.

The next problem is that there is no place to download to. It's booting off the CD, it doesn't have access to any hard-drives. Even if I could download the correct drivers, ubuntu has no place to put it.

The good news though is that I could get to command line, which suggests that ubuntu is working (even if not graphically). However, the two problems above were confirmed when I tried getting the correct drivers -- ubuntu couldn't get anything from the repositories, or even update them.

If there isn't a quick-fix way to get ubuntu working off the CD, I'll try using the text-based installation and just making a dual-boot.

---

### Post by pyros on 2007-07-11
> **Venerence said:**
> So I have downloaded and burned the live-cd, and have run into one particular problem while installing.

Halfway through the boot-up from the cd, I get the following error:
.

At this point, it doesn't continue any farther, and doesn't accept any commands (at least none that I know of) until I tell it to shut down.

As I the f3jp comes with a radeon x1700, I'm guessing this problem is related to [this](http://ubuntuforums.org/showthread.php?t=414194). The problem with that solution is that I don't want to install ubuntu completely without trying it out from the CD. Is there a way to resolve this problem using the live cd?
What happens if you choose "Start Ubuntu in Safe Graphics Mode" when you boot off of the cd?

---

### Post by Venerence on 2007-07-11
> **pyros said:**
> What happens if you choose "Start Ubuntu in Safe Graphics Mode" when you boot off of the cd?

Same problem as when I install regularly. I don't think this laptop has an internal graphics card, so any sort of rendering will require the graphics card to work. However, since I could get to command line, that's enough to know that (for the most part) ubuntu is working. It looks like, that if I want to get any farther, I'll have to install ubuntu properly with its own partition.

---

### Post by Venerence on 2007-07-13
I have one last problem before trying to install the text-based installer of ubuntu. To get the graphics card recognized, specifically this:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
```

And for the wireless:
```
sudo apt-get install linux-restricted-modules
```
won't I need an internet connection to download it (from what I understand, apt-get accesses the online repositories)? Since my wireless card won't be working (probably), what would be the best way to get this installed, or at least the best way to get connected through the defaults?

---

### Post by Hendrixski on 2007-07-13
hey, I see you're new so I thought I would give you a warm welcome that comes from the heart... (hope you're finding that all of your questions are being answered)

[B]
WELCOME TO THE COMMUNITY![/B]
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others.  Some of us here are even the same people who write the software you're using, or the documentation you're reading.  Why?  because we value freedom so we built a platform that is free.

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC. Installing IRC is easy and fun. Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too! Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it. A lot of it is written by the same people who answer questions on these forums. If dry manuals aren't your thing then relax and watch some videos. [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc. Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

