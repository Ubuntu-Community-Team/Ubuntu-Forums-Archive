---
title: "BlackBuntu??? Is there anything similar?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-05-02
Well...another friend of mine asked me a weird question. Since I really don't know what to tell him, I decided do place the question here, hoping someone will know the answer.

He has a Pc even older than mine! I think it's a Pentium 133 mHz with 64 Meg of memory. Not really sure about the rest of the hardware, but it's a very old computer.


The question he asked me, is this one: Is there any BlackBuntu? Like, there is a fluxbuntu with a fluxbox interface, only he insists in having blackbox. Mine has XFCE, but it seems the fluxbox and the blackbox are a bit different and lighter on the hardware.

So, does anyone knows if thre is a Blackbuntu, or some linux with only blackbox? 



P.S. Why does he insists on having blackbox? Is it that good?


P.P.S. He his a windows user, and doesn't have a clue how to use the terminal.

---

### Post by GrueTamer on 2007-05-02
What he could do is get fluxbuntu, then install blackbox and use that.  Tell him that after he gets fluxbox, to enter this in the terminal

```
sudo apt-get install blackbox
```

That way, if he decides that fluxbox is better, he can use that.  He can also get other window managers like this, such as icewm.

Note, exact commands are simple, since he can just copy and paste it, and it should work perfectly.

---

### Post by Ganda_Melga on 2007-05-02
> **GrueTamer said:**
> What he could do is get fluxbuntu, then install blackbox and use that.  Tell him that after he gets fluxbox, to enter this in the terminal

```
sudo apt-get install blackbox
```

That way, if he decides that fluxbox is better, he can use that.  He can also get other window managers like this, such as icewm.

Note, exact commands are simple, since he can just copy and paste it, and it should work perfectly.


I'll tell him that. I'm still trying to handle XFCE, let alone those box things. :lolflag: 


Thank's a lot!

---

### Post by RedSquirrel on 2007-05-03
> **Ganda_Melga said:**
> Well...another friend of mine asked me a weird question. Since I really don't know what to tell him, I decided do place the question here, hoping someone will know the answer.

He has a Pc even older than mine! I think it's a Pentium 133 mHz with 64 Meg of memory. Not really sure about the rest of the hardware, but it's a very old computer.

The question he asked me, is this one: Is there any BlackBuntu? Like, there is a fluxbuntu with a fluxbox interface, only he insists in having blackbox. Mine has XFCE, but it seems the fluxbox and the blackbox are a bit different and lighter on the hardware.

So, does anyone knows if thre is a Blackbuntu, or some linux with only blackbox? 



P.S. Why does he insists on having blackbox? Is it that good?



P.P.S. He his a windows user, and doesn't have a clue how to use the terminal.



Another possibility is to install the ubuntu server and then add fluxbox or blackbox on top of that.

[Here]("http://www.psychocats.net/ubuntu/minimal#barebones") is a guide to install the barebones system using the net installer. He could also download the [server ]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition")CD and install from there.

I don't think there's that much of a performance boost in using Blackbox instead of Fluxbox. (The support on these forums for Fluxbox is excellent, by the way.)

---

### Post by bodhi.zazen on 2007-05-03
I do not think the black box project is maintained any longer ... 

I agree with the advice to go with Fluxbox or Openbox

For that old box have your friend look at DSL and Puppy Linux (64 Mb ram is pushing it as far as most distro's go. It can be done, but it may be worth a lighter distro).

---

### Post by RedSquirrel on 2007-05-03
> **bodhi.zazen said:**
> I do not think the black box project is maintained any longer ... 


Yeah, I meant to look that up. It seems the last version was 0.70.1 released November _2005_.

---

### Post by Ganda_Melga on 2007-05-03
Well, just to see if this blackbox was anygood, I installed it in my xubuntu. I started in this blackbox, but all I get is a dark grey screen, with nothing at all. Ah.. theres a small bar in the bottom, but is doesn't do anything. With right click, only 3 options available; Xterm, restart, exit.

I guess for myself, i will stick to Xfce.


Or I will have to learn the terminal commands to use the blackbox.

---

### Post by urukrama on 2007-05-04
The default menu of Blackbox (or Openbox and Fluxbox) can easily be edited. Check the forums for howto's on Blackbox, Openbox and Fluxbox. Once you have it set up, it is very fast on older hardware, and you don't need the command line that often if you don't want to. There are several GUI applications that allow you to edit the menus, etc.

If you come from a WIndows environment, the *boxes may require some getting used to. But once you've everything set up and at home in the new environment, you'll realise how smooth things work. I use Openbox, and find other DE (Gnome, KDE, Windows, etc.) a bit clumsy now. Give it some time.

---

### Post by macogw on 2007-05-04
Maybe he used BB4Win at some point and liked it?

---

### Post by Ganda_Melga on 2007-05-04
> **urukrama said:**
> The default menu of Blackbox (or Openbox and Fluxbox) can easily be edited. Check the forums for howto's on Blackbox, Openbox and Fluxbox. Once you have it set up, it is very fast on older hardware, and you don't need the command line that often if you don't want to. There are several GUI applications that allow you to edit the menus, etc.

If you come from a WIndows environment, the *boxes may require some getting used to. But once you've everything set up and at home in the new environment, you'll realise how smooth things work. I use Openbox, and find other DE (Gnome, KDE, Windows, etc.) a bit clumsy now. Give it some time.


Thanks. I found a thread with quite some help about editing blackbox. Will study it in detail.

---

### Post by Ganda_Melga on 2007-05-04
> **macogw said:**
> Maybe he used BB4Win at some point and liked it?

I have no idea. What is BB4win? He his an windows 98 user, and now seems interested in linux as a second choice. Myself I like windows XP a lot, but the 98 doesn't apeall to me.

---

### Post by Ptero-4 on 2007-05-04
> **Ganda_Melga said:**
> I have no idea. What is BB4win? He his an windows 98 user, and now seems interested in linux as a second choice. Myself I like windows XP a lot, but the 98 doesn't apeall to me.

BB4win is a shell (DE in Windoze-speak) that looks like (black/flux)box (except the window borders which windoze shells doesn´t handle, since windoze handles them).

---

### Post by Harii on 2007-06-07
I found that blackbox is easier to learn and i hate the tabs.
blackbox + thunar is what i'm using.
the thunar site claim that its lighter than rox-filer and i find it easier.

---

### Post by RedSquirrel on 2007-06-07
> **Harii said:**
> I found that blackbox is easier to learn and i hate the tabs.
blackbox + thunar is what i'm using.
the thunar site claim that its lighter than rox-filer and i find it easier.

I prefer to use something that is still in active development, so I prefer Fluxbox. The tabs can be turned off. ;)

---

