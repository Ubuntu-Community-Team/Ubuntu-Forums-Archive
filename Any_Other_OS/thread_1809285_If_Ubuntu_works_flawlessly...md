---
title: "If Ubuntu works flawlessly.."
date: 2011-07-21
forum: Any Other OS
---

### Post by Kannokki on 2011-07-21
Just a quick question here.
If Ubuntu 11.04 works flawlessly on my *eMachines E642G* laptop, is it possible to get Arch Linux working _flawlessly_ too  ?

Currently I'm dualbooting Ubuntu and Windows 7, and I'm thinking about ditching both of these to learn something new. The thing I'm most worried about is my wireless.

If Ubuntu works, Arch works, right?

---

### Post by snowpine on 2011-07-21
Theoretically yes. :) The Arch Beginners Guide (which you should read immediately, if you haven't already) explains how to set up wireless networking.

My advice is to keep Windows, keep Ubuntu, and set up a triple-boot with Arch. Or run Arch inside of Ubuntu using VirtualBox.

Out of curiosity, what are you hoping to learn from Arch that can't also be learned from Ubuntu?

---

### Post by Kannokki on 2011-07-21
I'm not very happy with my current Ubuntu installation. I was messing around with Unity, Gnome and XFCE. I'm currently in a place where I can't get a new LiveCD to re-install, so I can't easily fix these mess-ups.  


> **snowpine said:**
> 
Out of curiosity, what are you hoping to learn from Arch that can't also be learned from Ubuntu?

I was reading random articles about Arch one day, and found this [[COLOR="Red"]Installing Arch Linux, part 1: What Do You Want?[/COLOR]]("http://www.mintcast.org/2010/08/installing-arch-linux-part-1-what-do-you-want/")
> But now I want to build the house. I want to learn where the boards
go, where the pipes are, how everything is connected and why it
works. I feel that in Ubuntu, someone else did all the work for me. I installed Ubuntu, because I believed that Ubuntu is the easiest distro to get working on my laptop. First I tried Fedora 15 LiveCD, and the wifi didn't work. Then I installed Ubuntu, and It worked out-of-the-box.

---

### Post by doas777 on 2011-07-21
> **Kannokki said:**
> 
 I feel that in Ubuntu, someone else did all the work for me. I installed Ubuntu, because I believed that Ubuntu is the easiest distro to get working on my laptop. First I tried Fedora 15 LiveCD, and the wifi didn't work. Then I installed Ubuntu, and It worked out-of-the-box.

there is some truth to that.

Arch is very flexible, so yes, in theory it is very possible to make everythign work well. that said, ubuntu does add drivers to their kernel image that do not exist in the vanilla, and they also provide some nice mechanisms for installing/upgrading proprietary drivers that Arch lacks. you can always install whatever drivers you need manually, but they need to be reinstalled with each kernel upgrade.

---

### Post by snowpine on 2011-07-21
A good first step is to figure out which wireless chipset your laptop has.

```
lspci
```

Also which module Ubuntu uses to make it work.

```
lsmod
```

Once you have that information you can make your wireless work in any distro (including Fedora).

ps You can also do a "boards and pipes" install of Ubuntu if you wish: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Kannokki on 2011-07-21
I think I'm going to give Arch a try. This laptop is my "number 2" computer, so it really doesn't matter if it's unusable for a while. I'll install Arch over Ubuntu, And if I can't get it working, I'll install Xubuntu. (I can't stand Unity or Gnome 3. )

---

### Post by Bucky Ball on 2011-07-21
Do a Ubuntu minimal install and work your way up. Build it as you like, or compile your own kernel. That way you will be building it and installing only what you want (right down to hardware drivers and modules if you like).

(PS: You can install xfce in Ubuntu, naturally, if you can't stand Unity or Gnome, without installing Xubuntu. Having said that ... I generally run a stripped back Xubuntu.)

---

### Post by Kannokki on 2011-07-21
> **snowpine said:**
> 
ps You can also do a "boards and pipes" install of Ubuntu if you wish: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

This caught my interest. I shall read more about this.

---

### Post by Kannokki on 2011-07-21
Thanks to everyone posting in this thread. I shall mark this thread as [SOLVED]

---

### Post by snowpine on 2011-07-21
I'll repeat my advice above about using "lspci" and "lsmod" to learn more about your hardware *before* you make the leap. :)

---

### Post by Kannokki on 2011-07-21
> **snowpine said:**
> I'll repeat my advice above about using "lspci" and "lsmod" to learn more about your hardware *before* you make the leap. :)

I'm perfectly aware of my hardware :). Thanks for the tip, anyway!

---

### Post by handy on 2011-07-21
One of the benefits of installing Arch as opposed to minimal Ubuntu, is that the [**_Beginners' Guide_**]("https://wiki.archlinux.org/index.php/Beginners%27_Guide") is brilliant. As is the Arch wiki. As far a reference material & great guides go, Arch is very hard to beat. Gentoo also has a great wiki & installation guides.

When installing Arch you are best advised (at least for the first successful attempt) to follow the Beginners' Guide to the letter.

Some people can't stand the way Arch works & very quickly dump it. There is only one way to find out if it suits you...

Many find the Arch installation an enjoyable adventure. :)

---

