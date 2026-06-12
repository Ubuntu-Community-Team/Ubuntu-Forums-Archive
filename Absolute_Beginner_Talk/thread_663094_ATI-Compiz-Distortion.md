---
title: "ATI-Compiz-Distortion"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by rmx on 2008-01-09
Hello

I have an ATI Radeon 9700.

I've installed Ubuntu 7.10 and fglrx from restricted driver manager.

I run:

$sudo gedit /etc/X11/xorg.conf

$sudo apt-get install xserver-xgl

reboot

$sudo apt-get install compizconfig-settings-manager

everything was working fine.

however, after rebooting again:

- the characters became distorted (almost unreadable), and the colour  inverted with the bakground.
- navigating with firefox for example became extremely slow as so scrolling and typing.

I've searched this topic already but couldn't find a solution

can anyone help me please?

thanks

rmx

---

### Post by Law506 on 2008-01-09
> **rmx said:**
> Hello

I have an ATI Radeon 9700.

I've installed Ubuntu 7.10 and fglrx from restricted driver manager.

I run:

$sudo gedit /etc/X11/xorg.conf

[B]$sudo apt-get install xserver-xgl
[/B]
reboot

$sudo apt-get install compizconfig-settings-manager

everything was working fine.

however, after rebooting again:

- the characters became distorted (almost unreadable), and the colour  inverted with the bakground.
- navigating with firefox for example became extremely slow as so scrolling and typing.

I've searched this topic already but couldn't find a solution

can anyone help me please?

thanks

rmx

Does your card require this extra step after you install the restricted driver?  I use a 9000 on my other system and just using restricted works pretty well.

---

### Post by rmx on 2008-01-10
If you mean **$sudo apt-get install xserver-xgl**, it is not related with the card, but with compiz in a general way.

I guess compiz runs over a different window server (xgl).

So I need to install it and I guess you did too (perhapes without noticing it).

Am I wrong?

---

### Post by rmx on 2008-01-10
I noticed the cause for graphical programs were incredible slow is related with the xgl  process (~95% CPU!)

So I uninstalled xgl and system became normal but without compiz effects

do I need to make an adicional step to have xgl working with my ATI RADEON 9700 Mobile?

Thanks

---

