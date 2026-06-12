---
title: "[SOLVED] Ubuntu won't start with nVidia video adapter"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-09-19
Just purchased a 3DForce 6200 - 256 nVidia adapter, with 22" LCD at 1680x1050. Installed under Windows, configured it and everything went fine.

Went to Ubuntu 7.04 on the dual-boot tonight, and I can't get it to boot at all. I know that the resolution might be a problem, but I don't know how to reset it to something more acceptable.

I previously used an ATI card with the PC, and Ubuntu recognised it when I installed the OS. I've removed the card and associated drivers, so I guess Ubuntu can't get a handle on what's there now.

Should I re-install Ubuntu (no real data loss to me - I'm still a real newbie) from the Live CD, and see whether I get the chance to configure the adapter/monitor? Or is there a another way to get the adapter recognised? I posted yesterday about getting Linux drivers for the card, and I've also downloaded the drivers from nVidia's site, altho how to instal them would be a mystery to me - it seems using Ubuntu's restricted driver manager would be the better option for this new user.

I live very remotely, and this site is my lifeline in trying to get away from Windoze. I'm making progress, but this new development has me back at square one.

Any comments/advice would be most welcome. Thanks

---

### Post by alienexplorers on 2007-09-19
To load your nvidia drivers you can use the Envy script.  I have a link to it in my sig line.

---

### Post by Jeroen Vernooij on 2007-09-19
Hi,
You say you can't boot at all: what does that mean? Do you see a black screen with something like:
<computername>:login: ??
or something like:
<user>@<computername>: ~$: ??

If that's the case, you are in the command-line. That's good. 
If you don't see nothing at all: choose Recovery mode in the boot-menu.
You should now also get in command-line.

Now:
login and type:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
```
and then:```

sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
```

and the envy script should try to guide you through the install of the nVidia driver.


However: This behaviour is crap: Report a bug! [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by corowakid on 2007-09-19
> **alienexplorers said:**
> To load your nvidia drivers you can use the Envy script.  I have a link to it in my sig line.

Thanks - but that presupposes I can get Ubuntu running, does it not? Currently I can't get past a black screen, then a multi-colored screen with fractured text referring to X not being able to be loaded.

Hope you see my problem.

---

### Post by corowakid on 2007-09-19
> **Jeroen Vernooij said:**
> Hi,
You say you can't boot at all: what does that mean? Do you see a black screen with something like:
<computername>:login: ??
or something like:
<user>@<computername>: ~$: ??

If that's the case, you are in the command-line. That's good. 
If you don't see nothing at all: choose Recovery mode in the boot-menu.
You should now also get in command-line.

Now:
login and type:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
```
and then:```

sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
```

and the envy script should try to guide you through the install of the nVidia driver.

However: This behaviour is crap: Report a bug! [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Sorry I replied to the 1st poster as you were sending your reply. What you refer to us what I'm getting - so it seems there might be light at the end of the tunnel for me.

I'm copying and printing the answers I get here so I can make sure I get it right when I start the Ubuntu session. I'll accumulate them tonight and give it a try tomorrow. Thanks for your help - much appreciated, and I'll report back on progress.

---

### Post by dcstar on 2007-09-19
> **Jeroen Vernooij said:**
> Hi,
.........
However: This behaviour is crap: Report a bug! [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Rubbish, changing the video card on an existing installation and then having issues is not a "bug", there may be limitations in Linux autodetecting new hardware but that is a feature issue, not a "bug".

The OP should do a forum search for the (many) posts on resolving this exact issue, most of them will have the following somewhere in them:
```
sudo dpkg-reconfigure xserver-xorg
```
where the system will then have the opportunity to reconfigure itself with the different video hardware.

---

### Post by PmDematagoda on 2007-09-19
If your card is the GeForce 6200 256Mb Turbo-cache PCI-E card, then you shouldn't have any problems under normal conditions as I have the same card myself and have had no problems.:)

---

### Post by ayenack on 2007-09-19
If the above does not work and you can boot into recovery mode try this. 

sudo apt-get remove nvidia-glx-new (if it says that nvidia-glx-new is not installed change to nvidia-glx)

sudo apt-get remove nvidia-settings

sudo apt-get remove nvidia-nvtv (this may not be installed)

Re-boot. See if you boot into GUI. If not boot into recovery again and do this.

sudo apt-get install nvidia-glx-new (make sure that this is the right one might be nvidia-glx way to tell is by which one you removed earlier)

Re-boot. You should now be in the GUI. If not try this from command line.

sudo dpkg-reconfigure -phigh xserver-xorg

Hope this helps. ayenack.

---

### Post by corowakid on 2007-09-19
> **Jeroen Vernooij said:**
> Hi,
You say you can't boot at all: what does that mean? Do you see a black screen with something like:
<computername>:login: ??
or something like:
<user>@<computername>: ~$: ??

If that's the case, you are in the command-line. That's good. 
If you don't see nothing at all: choose Recovery mode in the boot-menu.
You should now also get in command-line.

Now:
login and type:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
```
and then:```

sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
```

and the envy script should try to guide you through the install of the nVidia driver.


However: This behaviour is crap: Report a bug! [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

I did this exercise, and things went as you detailed. But I got an error report on missing dependencies, and the instal aborted. I see on Alberto's site that one has to make sure all repositories have to be installed - could this be the source of the problem (I haven't done that because I can't get in to the system the way I'm used to)? And how would I get the dependencies to load?

I feel I'm almost there, but log jammed.

I also see from posts that I'll need to edit the x.org file to get my resolutiion into it - I suppose that comes later(?).

Thanks for help.

---

### Post by ayenack on 2007-09-19
To edit your sources.list do this.

Make a backup of your sorces.list like this.

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup** (Write this down in case you need to restore the original).

Then do this.

**sudo nano /etc/apt/sources.list**

Un-comment (#) all the entries that start with deb.

Then do this.

**sudo apt-get update**

Good luck. ayenack.

Your sources.list should look something like this. I do not have the deb cdrom or the backports un-commented. I think but am not sure that you will need to.

---

### Post by Jeroen Vernooij on 2007-09-20
Hi corowakid,
You could indeed try to install the dependencies, but maybe better is to follow dcstar's advice:

just run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It asks a lot of questions, if you don't know the answers, just press enter.
That way you should get into vesa mode or opensource nvidia driver, so you can enter your GNOME again when you reboot. After that you can install the new nvidia driver using [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb) which in graphical mode will resolve all the dependencies.
Sorry for the inconvenience caused by my previous posts.

---

### Post by corowakid on 2007-09-24
> **Jeroen Vernooij said:**
> Hi corowakid,
You could indeed try to install the dependencies, but maybe better is to follow dcstar's advice:

just run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It asks a lot of questions, if you don't know the answers, just press enter.
That way you should get into vesa mode or opensource nvidia driver, so you can enter your GNOME again when you reboot. After that you can install the new nvidia driver using [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb) which in graphical mode will resolve all the dependencies.
Sorry for the inconvenience caused by my previous posts.

I'm writing this on my 1680x1050 screen, and it looks great. Followed Alberto Milone's instructions (more than once unfortunately) and got a final result that uses the Nvidia card to its fullest. Thanks to all those who pitched in with helpful hints - I've now got a ream of printouts for when I need to do it all again, which I understand is when there's a kernel change. Oh well, it won't be long before the next Ubuntu release and I'd have to do it anyway. Then it will be back to Alberto to see what good offerings he's got.

Thanks everyone.

---

### Post by mbrown1673 on 2007-10-19
i am having a similar problem... i just switched to a gforce 6200 agp from a radeon 9600, and when i boot it seems to freeze immediately. there is the ubuntu splash screen with about 1 mm of progress bar that doesn't move.

---

