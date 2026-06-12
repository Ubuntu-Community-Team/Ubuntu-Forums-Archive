---
title: "How to do offline installation - 6.10"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by xtkid on 2007-06-18
Hi guys, I am trying to install Network Manager or Wifi Radar on Ubuntu 6.10. But I don't have wired internet connection (trying to use pubic wireless ). Please let me know how to do it. 

And also, I am using Ubuntu 6.10 just because I have broadcom wireless card and I heard that 6.10 works easily with Broadcom cards.

Thanks in Advance.

---

### Post by jimbob on 2007-06-18
Network Manager is part of the standard installation so why would you want to install it again?

Type *[COLOR="RoyalBlue"]apt-cache policy network-manager[/COLOR]* in a terminal and you should see it.

Network manager is kind of dumb IMHO but if you can get it to connect wirelessly you should be able to download WIfi-radar over the wireless network.  I would recommend Wicd instead as it seems to be a better package.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by xtkid on 2007-06-19
Thanks a lot. :D. One thing more In case I try to use **Ubuntu 7.04** and I still need to do some offline installtion, what's the best place to fine offline installation packages. I know these are available on Ubuntu site also [http://packages.ubuntu.com/](http://packages.ubuntu.com/), but it also says some "Depends" "Recommends" etc files for the respective package. Are these dependent files I need to download along with the main package, because If I download the main package it just give error. Thanks again.

---

### Post by mikewhatever on 2007-06-19
> **xtkid said:**
> Hi guys, I am trying to install Network Manager or Wifi Radar on Ubuntu 6.10. But I don't have wired internet connection (trying to use pubic wireless ). Please let me know how to do it. 

And also, I am using Ubuntu 6.10 just because I have broadcom wireless card and I heard that 6.10 works easily with Broadcom cards.

Thanks in Advance.

You can download and install gnome-mn for 6.10 following instructions from [here]("http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945"), post #12. Off-line installation is a real pain, because you have to take care of all the dependencies. About broadcom cards, I've heard quite the opposite. You'll probably need ndisrapper to make it work.

---

### Post by xtkid on 2007-06-19
Hi thanks. I realized broadcom problem has same level of pain on both 6.10 and 7.04 . So I have installed 7.04. Now I also have Hawking HWC54G wireless card (not built-in), but when I insert this card, in Network Manager in the taskbar I see two wirelss cards listed Hawking at the top, then list of available connections and then Broadcom card ! But when I try to connect any of the available non-password protected connections, nothing happens. Do I have to blacklist or disable broadcom card for this. (I don't know how to disable either:()

Thanks again.

---

### Post by jimbob on 2007-06-19
I used this guide:
[http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)

Worked perfectly for me the first time with Wicd on an HP Compaq nx6110 laptop.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

