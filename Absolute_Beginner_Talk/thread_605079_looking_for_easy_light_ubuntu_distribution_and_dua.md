---
title: "looking for easy light ubuntu distribution? and dual boot with ubuntu"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-11-06
Hi

Currently, I have fiesty installed on a desktop system (primarily used by my mom) but it is kind of slow and tends to hang. The configuration is: 
Intel Celeron D Processor 335
(2.80GHz, 533MHz FSB, 256KB L2 cache)
Intel 865GV chipset
RAM: 256MB DDR
Hard Drive: 	80GB

1)  I was thinking of trying a light weight distribution like xubuntu or fluxbuntu ... (or any other you think is better). but I would prefer to dual-boot it with ubuntu fiesty so that it can be tested first. 

The primary use is : Internet surfing and creating documents (presently done in openoffice, pdf)

Here are some other questions:

2) whats the difference between xubuntu and fluxbuntu? Which one is similar/closer to ubuntu? and what about the support ? (Is it as good as ubuntu? :) )

3) Before installing, I'd like to backup the data. What is the best way to do so? any applications etc.

Thanks

---

### Post by skymera on 2007-11-06
light ubuntu...hmm

Xubuntu!

worked wonders on my mums old lappy!

192mb RAM
800MHz

now faster! than her..

1GB RAM
1.6Ghz Dual CorVista

go linux 

2. the different between ubuntu and fluxbuntu?
fluxbuntu has fluxbox installed.

---

### Post by bodhi.zazen on 2007-11-06
+1 fluxbuntu.

Fluxbuntu uses Fluxbox as a window manager and the base installation if much lighter then *buntu.

If there is an application missing, you can install with apt-get or synaptic.

Support is available here, the Fluxbuntu forums, or irc at #fluxbuntu (freenode)

---

### Post by KCPokes on 2007-11-06
Just remember that a lightweight distro is only as good as the programs you use with it.  For example, Xubuntu works well (now that does depend on just how old your machine really is) but if you are sold on using programs like Amarok with it, then you've somewhat defeated the point.  Lightweight distro with lightweight applications.  

You can go far more lightweight, IMHO, then Xubuntu, but it really moves away from the 'Buntu architecture.  Your machine looks substantial enough to be able to handle Xubuntu without issues.  Worse case, add more memory.

---

### Post by Pabx on 2007-11-06
Well There is a way to do all you Want!

I recommend Xubuntu, but you can try both
If you have decided what to use, you should install the system then, in other partition, to Dual boot

To make a backup you can use [COLOR="Red"]Simple Backup Restore [/COLOR] You'll find it on the synaptic or in Add/Remove applications

Or you can use keep 
to install:
```
Sudo apt-get install keep
```

:D

---

### Post by ofb on 2007-11-06
> **genbuntu said:**
> 2) whats the difference between xubuntu and fluxbuntu? Which one is similar/closer to ubuntu? and what about the support ? (Is it as good as ubuntu? :) )

Xubuntu is an official derivative. After that, Xubuntu is a distro based around xcfe, while Fluxbuntu is based around fluxbox, both lighweight windows managers.

Personal opinion, Xubuntu isn't noticeably lightweight at the moment. I think of the 7.10 release as simply another flavour of 'bu, like Kubuntu is. Fluxbuntu is a recently restarted project and I haven't looked at 7.10. I'm expecting equal measures of enthusiasm and teething-problems.

Support... well, that'll depend on what you mean by support. The great majority run Ubuntu of all the 'bu's, so you'll find many more people to help out when you ask. The numbers receed for Kubuntu, Xubuntu, and Fluxbuntu respectively.

Looking at your hardware, I'd be thinking of adding another 256MB stick and running Ubuntu. Which is not a slag at Xu or Flux at all - I only suggest they're suited for people who'd like a little more adventure. ;) You sound like you want the least trouble.

EDIT - I type too slow - four answers while I was busy. Now you have lots to think about.

---

### Post by rsambuca on 2007-11-06
> **Pabx said:**
> Well There is a way to do all you can

First , I recommend Xubuntu, but you can try both
If you have decided what to use, you should install the system then, in other partition, to Dual boot 

**[COLOR="Red"]After install you MAYBE Wont be able to enter ubuntu , What you need to do is:[/COLOR]**

Edit the menu.lst in Xubuntu

I'm not sure about this But it maybe like in ubuntu:

In a terminal:
sudo gedit /boot/grub/menu.lst 
Then you Should add this :
At the end of the menu.lst you could see this

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

If You see it you wont need to add it if you dont , then add it

After it:
title		Ubuntu 7.04 
root		(hd0,1)---------------------------------> **Here you have to put your HD**
kernel		/boot/vmlinuz-2.6.22-14-generic --->**Here I think its the same if it wont Boot then you should find some File called vmlinuz-XXXXX-generic in the 7.04 Boot menu and add the name here **
quiet

If you Want to do it from ubuntu

1) Use the live Cd to enter
2) Acces the terminal
3) Type in a Terminal session : sudo grub
4) f you do not know your boot partition, use this Find command: find /boot/grub/stage1
5) type root (hd0,1) #Hit the <Enter> key
6) Type setup (hd0) #Hit <Enter> key
7) Done! :D

After Doing This, You'll have to edit the menu.lst , 

Go to a terminal Session and type

sudo gedit  /boot/grub/menu.lst 
Then you Should add this :
At the end of the menu.lst you could see this

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

If You see it you wont need to add it if you dont , then add it

After it you have to add:

title		Ubuntu 7.04 
root		(hd0,1)---------------------------------> **Here you have to put your HD**
kernel		/boot/Xubunutu Vmlinuz --->**Here you should find some File called vmlinuz-XXXXX-generic in the 7.04 Boot menu and add the name here **
quiet


Thats All! you should be able to Dual boot

Whoa, let's not get ahead of ourselves here.  That shouldn't be necessary as the Xubuntu installation grub should detect the existing ubuntu installation.  Also, Your instructions will turn up two different stage1 grubs, so it is important to use the right one for clarity going forward.  In either case, let's not confuse matters here with too much info.  I suggest the OP ignore these two posts!

---

### Post by ofb on 2007-11-06
> **skymera said:**
> worked wonders on my mums old lappy!

Was that with 7.10 skymera? I didn't notice much difference on a P3 450 526MB GF2 here.

---

### Post by aysiu on 2007-11-06
I'd recommend IceWM as a window manager.

You don't have to install a dual boot with an entire distro. As long as you have the Universe repositories enabled, just ```
sudo apt-get update
sudo apt-get install icewm
``` Then log out, choose IceWM from the Session menu and see how you like it. If you don't like it, log back into Gnome and ```
sudo apt-get remove icewm
``` I promise that's a lot simpler than installing a dual boot to try something out.

You can find some good IceWM tips [here](http://ubuntuforums.org/showthread.php?t=263710).

---

### Post by Pabx on 2007-11-06
> **rsambuca said:**
>   That shouldn't be necessary as the Xubuntu installation grub should detect the existing ubuntu installation.  

Well then I supposed that... :D

---

### Post by SteveHoffmanUK on 2007-11-06
OFB wrote:
> Looking at your hardware, I'd be thinking of adding another 256MB stick and running Ubuntu.

Agree completely. Memory is so cheap, why struggle with lite versions? I have a 1.8MHz processor but upgraded my 256Mb RAM by a Gig (i.e. now 1.3 GB) and Ubuntu flies!:)

---

### Post by jordanmthomas on 2007-11-06
> **SteveHoffmanUK said:**
> OFB wrote:
Agree completely. Memory is so cheap, why struggle with lite versions? I have a 1.8MHz processor but upgraded my 256Mb RAM by a Gig (i.e. now 1.3 GB) and Ubuntu flies!:)

I don't care how much RAM I have, I still prefer a light, stay-out-of-my-way window manager because it's easier (for me anyway) to be productive.

---

### Post by aysiu on 2007-11-06
> **jordanmthomas said:**
> I don't care how much RAM I have, I still prefer a light, stay-out-of-my-way window manager because it's easier (for me anyway) to be productive.
Same here. I have 512 MB of RAM, and I like IceWM a lot on it, even though I can run KDE or Gnome on it just fine.

---

### Post by genbuntu on 2007-11-06
wow, thanks a lot guys. I'm leaning towards Xubuntu, but the option suggested by aysiu (using IceWM) sounds interesting and simple enough to be tried. :)
(hmm.. RAM upgrade is always an option, but for the basic needs like internet/word processing , I'd refrain from it ).

[QUOTE=genbuntu] 3) Before installing, I'd like to backup the data. What is the best way to do so? any applications etc. [/QUOTE]
So any further suggestions for backup. Would simply copying the contents of /home folder for all users suffice? or shall I use a backup software like "Simple Backup Restore" as Pabx mentioned ?

P.S: Installing and using IceWM would keep my files and folders intact; Right ? What about the desktop items?

---

### Post by misfitpierce on 2007-11-06
Xubuntu official branch
Fluxbuntu as a derivative someone made off Ubuntu...

---

### Post by Dr Small on 2007-11-06
+1 for Fluxbuntu
Even though I have never tried it (yet!) I know it has to be good.
I am still working on getting it ;)

---

### Post by aysiu on 2007-11-06
> **genbuntu said:**
> 
P.S: Installing and using IceWM would keep my files and folders intact; Right ? What about the desktop items? Yes. It would keep that all intact.

When you use IceWM, however, no icons will appear on the desktop (they're still in your desktop folder--you just won't see them when you use IceWM).

If you're really concerned about it affecting your user settings, create a new test user and install *xnest*: ```
sudo apt-get install xnest
gdmflexiserver --xnest &
``` and then log into IceWM with that user.

---

### Post by ofb on 2007-11-06
You can just copy /home as a straighforward backup. asiyu talks about a more refined method here,
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

There's a nice GUI backup system for Ubuntu in the works, btw. Maybe next release?

Personal suggestion - while you're at it you might make a backup of /etc if you've been doing any amount of modification to your setup at the system level. Like say you've made additions to your hosts file, or fstab, or blacklisted a module at some point or something. You'd never want to just copy files from this backup into a new install of course, but it's handy when you find you still need some little fix you once did and can't remember the exact syntax you used.

A word on RAM - RAM is commodity priced, meaning a type of RAM gets real cheap when everyone is using it. But the price starts to climb right back up after this vogue. Manufacturing switches to a newer variety, people with older machines buy up the remaining stock, and suddenly the few sticks you can find at the dealers start to cost more than bigger newer types.

I just mention that as your machine is otherwise reasonably modern. Might be worth filling its RAM before the curve climbs, just to extend the useful life on the cheap. Ubuntu 7.10 desktop requires 384MB to install now, for instance.

---

### Post by genbuntu on 2007-11-06
thanks for the suggestions. 
I now feel 'knowledgeable' enough to tackle this speed issue.

Any further comments/advices are always welcome ! :)

---

### Post by HermanAB on 2007-11-07
Hmm, install Puppy Linux and everything runs instantaneously:
[http://www.puppylinux.com](http://www.puppylinux.com)

Puppy gives a whole new meaning to 'speed'.

Cheers,

Herman

---

