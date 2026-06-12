---
title: "tell me about ubuntu vs. kubuntu vs. Xubuntu"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by b9anders on 2007-01-24
I have run on Xubuntu initially, but I am gonna do a re-install as I have a feeling I might have messed up a few installations and I haven't gone that far with this installation yet anyway.

So I thought that would make for a good opportunity to reconsider whether xubuntu is the best choice for me or if I should consider plain old Ubuntu or Kubuntu.

I really really like the speed of Xubuntu. Windows XP was driving me nuts with it delay times everytime I right clicked something or opened the start menu and its slow startup time. Xubuntu starts up about as fast as my old Amiga 500. I run a 1.4 ghz/256 MB RAM laptop, so if I can expect delay times running [K]Ubuntu, that would be a negative for me.

I guess the main question is: What do I get with the main Ubuntu that Xubuntu doesn't have? Here, I am also considering that I am rank beginner when it comes to linux. Will it be easier for me to learn? Less hitches?

And what does Kubuntu offer that is significantly different?

---

### Post by renzokuken on 2007-01-24
From personal experience, i would say that they all offer the same things really. the all vary in  design and style and may have one or two apps that are unique to that desktop manager, although there is always an equivalent app for each desktop manager. Gnome and KDE are arguably easier to use than XFCE, but thats a matter of personal preference i guess.

On that hardware, i would recommend sticking with XFCE, it may be slightly less featured than Gnome or KDE, but the performance will be better. You can always try all three on one install though.

After installing Xubuntu, you can do

```
sudo apt-get install ubuntu-desktop
```
for Gnome

and 
```
sudo apt-get install kubuntu-desktop
```

to get KDE.

You can then select which environment you want at login. This will use up a fair bit of memory though and they are quite large downloads. If you have a fast net connection and some spare CD-Rs, you could always try the live cd for each desktop environment and decide that way without having to install anything

---

### Post by Pobega on 2007-01-24
Xubuntu is by far my favorite.

KDE is ugly and hard to get used to in my opinion, and it has *too many* options, most of which you really don't care about.

Gnome runs into some slow down occasionally, and is a tiny bit easier to use than Xfce.

But once you learn how to use Xfce it's like having a fast version of Gnome; Plus Xfce is much better to skin, since it accepts both GTK skins and Window Manager skins (Gnome as far as I know only accepts GTK skins).

---

### Post by hyper_ch on 2007-01-24
I also prefer Xfce... it's nice, it works, it has all I need, it's quick...

But then I als run quite a bit of KDE appz in Xubuntu like: Konversation, Kopete, Kontact, KFTPGrabber and a few more...

As said, the different GUIs just look different and come, when you use the according install cd, with different pieces of software preinstalled... but you can run all the appz on all three guis...

---

### Post by b9anders on 2007-01-24
Another question that has been on my mind is: What do I need to watch out for in tutorials and advice on here etc. when using Xubuntu? Most advice seems tailored to Ubuntu, so I'd like to know what is unique to Ubuntu and what is generic for both.

---

### Post by hyper_ch on 2007-01-24
If it's about the GUI then it's for the specific gui... however most of the things asked are gui-independant (I think)... with your experience you will be able to judge yourself whether it concerns the gui or *buntu in general :)

---

### Post by renzokuken on 2007-01-24
One small piece of advice is to look out for the name of packages/programs you are installing, for example, if it starts with g (e.g. gedit, gftp, etc) it is usally for gnome, although should still work on XFCE.

if it starts with a k (e.g. kopete, kedit etc etc) more often than not it is for KDE and wont work on XFCE without the KDE libs installed.

there are loads of exceptions but this is a general rule of thumb, the packages home page usually tells you everything you need to know

---

### Post by b9anders on 2007-01-24
> **renzokuken said:**
> One small piece of advice is to look out for the name of packages/programs you are installing, for example, if it starts with g (e.g. gedit, gftp, etc) it is usally for gnome, although should still work on XFCE.

if it starts with a k (e.g. kopete, kedit etc etc) more often than not it is for KDE and wont work on XFCE without the KDE libs installed.

there are loads of exceptions but this is a general rule of thumb, the packages home page usually tells you everything you need to know

So what is the telltale signs of programs that are preferable for xfce?

Where do programs like opera, skype and the software on easyubuntu and automatix feature in this scheme?

---

### Post by hyper_ch on 2007-01-24
the necessary libs for running kde appz will also be installed when you install the kde appz :)

---

### Post by renzokuken on 2007-01-24
> **b9anders said:**
> So what is the telltale signs of programs that are preferable for xfce?

Where do programs like opera, skype and the software on easyubuntu and automatix feature in this scheme?

i dont think there is one really. skype, opera, programs like that are pretty much cross-environment.

at the end of the day, you can get most programs to run on any platform, as long as dpendencies are met, which apt-get takes care of anyway. probably best to assume that all programs will work and ignore my last post

---

### Post by jcarmona on 2007-11-08
If i have ubuntu can i install xubuntu on top of it with the following:

sudo apt-get install xubuntu-desktop

Will it clobber my files and setting on my ubuntu install?

---

### Post by jcarmona on 2007-11-08
> **renzokuken said:**
> From personal experience, i would say that they all offer the same things really. the all vary in  design and style and may have one or two apps that are unique to that desktop manager, although there is always an equivalent app for each desktop manager. Gnome and KDE are arguably easier to use than XFCE, but thats a matter of personal preference i guess.

On that hardware, i would recommend sticking with XFCE, it may be slightly less featured than Gnome or KDE, but the performance will be better. You can always try all three on one install though.

After installing Xubuntu, you can do

```
sudo apt-get install ubuntu-desktop
```
for Gnome

and 
```
sudo apt-get install kubuntu-desktop
```

to get KDE.

You can then select which environment you want at login. This will use up a fair bit of memory though and they are quite large downloads. If you have a fast net connection and some spare CD-Rs, you could always try the live cd for each desktop environment and decide that way without having to install anything

--------------------------------------------

Would (sudo apt-get install xubuntu-desktop) clobber my ubuntu install or would xubuntu install on on top.
I have 7.1 ubuntu.

---

### Post by qamelian on 2007-11-08
> **jcarmona said:**
> --------------------------------------------

Would (sudo apt-get install xubuntu-desktop) clobber my ubuntu install or would xubuntu install on on top.
I have 7.1 ubuntu.

Installing xubuntu-desktop will not harm your Ubuntu install. It will just give you the Xubuntu environment in addition to Ubuntu. In fact, you can install as many different desktop environments / window managers as you like, so you can test them all and see which ones you like.

---

### Post by hotweiss on 2007-11-08
Xubuntu all the way...

---

### Post by bodhi.zazen on 2007-11-08
More about DE and WM :

[http://xwinman.org/](http://xwinman.org/)

WM = windows manager = boxes, mouse, keyboard.

DE = WM + apps. For example Gnome is a window manager (metacity or compiz) + gedit + other gnome apps.

You can mix an match as much as you like, the only penalty is Bloat. After a while you will find one you like.

I like *box (Fluxbox / Openbox) and XCFE, and I use K3b because it is the best, most reliable CD burning application, IMHO at least.

---

### Post by RedSquirrel on 2007-11-08
> **bodhi.zazen said:**
> I use K3b because it is the best, most reliable CD burning application, IMHO at least.

I like to burn using command line tools.

[https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning)

Have a look at the section entitled... wait for it... *Burning a CD or DVD using Command Line tools*. :grin:

(Note that cdrecord is now wodim.)


**Edit:** You may already know all about this, but I just thought I'd mention it for those who want an alternative to a graphical burning application. By the way, is there something that K3b offers that the command-line method does not? (I'm just curious...;))

---

### Post by bodhi.zazen on 2007-11-08
> **RedSquirrel said:**
> **Edit:** You may already know all about this, but I just thought I'd mention it for those who want an alternative to a graphical burning application. By the way, is there something that K3b offers that the command-line method does not? (I'm just curious...;))

LOL

While I *know* K3b is "just" a giu front end for the command line tools, K3b burns disks faster and with less coasters then anything else, which is why I use it.

IMO GUI tools should make things easier, and for me, +1 K3b. With one tool I can meet all my burning needs and K3b checks the integrity of both the source iso and the burn.

~ good old fashioned laziness

---

### Post by A$h X on 2008-04-25
So lets say I ran sudo apt-get install xubuntu-desktop from ubuntu, then at login I could select whether to use gnome or XFCE? But they are BOTH consuming memory, even if I'm using one not the other? So my system would take a performance hit as opposed to just using either GNOME or XFCE, I assume.

I would really like to give XFCE a try (not from the live CD as it's not a fair indication of how well it performs) without screwing up my hardy installation, but if installing xubuntu-desktop means slowing down my system, then it looks like I'm stuck. :frown:

I have the xubuntu 8.04 live CD here right now, anyway to run a triple boot of ubuntu, XP and xubuntu without borking any of the OS's?

---

### Post by lewisskinner on 2008-04-25
Hey, How about using Kubuntu with the new KDE4 DE on top of Ubuntu?  wouldn't 'sudo apt-get install kubuntu-desktop' get Kubuntu 8.04 but with KDE 3.5.9?  I wanna try KDE4!!

---

