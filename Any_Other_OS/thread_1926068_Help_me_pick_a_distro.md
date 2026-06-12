---
title: "Help me pick a distro"
date: 2012-02-15
forum: Any Other OS
---

### Post by nineveh on 2012-02-15
Hello everyone!

I've been trying to set up a linux system on my netbook for the last few days, and it's become such a frustrating task, trying to solve all the issues that come up with the various distros I tried out, that I have decided to ask for some direction.

I'm leaning towards Ubuntu purely for the sake of it's **out of the box compatibility** with so many systems, but I'd like to ask some questions before I settle.

For the last few months, I've had my HP Mini 210 series running Fedora 15 (gnome). It was somewhat of a pain to set up in the first place, but once I got past that initial struggle, it was doing well. **Battery life** was over 7 hours (which is very important to me), hibernate allowed it to stay but a few **seconds away from a full boot** for days without having to charge it. The only thing I minded was that it became a bit sluggish after a while, for no reason I can tell.

At some point however, I started having major problems - long story short, it's starting to require more effort than I'm willing to put in to get it working.

So, basically, I'm wondering if Ubuntu can match Fedora's battery life and boot time from hibernate. I use it for taking notes for example, so I really need it to be energy efficient, and be responsive when I pop the lid.

Secondly - performance. Just overall performance felt a bit sluggish in Fedora 15 like I said. I'm wondering if Ubuntu is faster in that regard. Maybe if I used lxde or xfce?

If Ubuntu is not the best choice for me, I would be happy to hear your opinion on other distros that do well in what I need them to. I'd just like them to be as compatible as Ubuntu seems to be with every system upon install. I'm not all that skilled in linux, but I CAN get by with a million open tabs on how to get something done - I just don't want to anymore, because it takes too much time. Just the memory of trying to enable wireless on fedora raises hairs on the back of my neck. Yeah, at least**wireless working out of the box** would be just dandy.

(relevant?)Hardware specs:
1.66ghz Intel Atom
1GB RAM
Display controller: Intel n10 family
[B]Ethernet: Realtek RTL8101E/RTL8102E 
WLAN: Broadcom B4313
[/B]
Thanks in advance.

---

### Post by cwklinuxguy on 2012-02-15
In terms of responsiveness and speed, your best options for desktop environments are LXDE, XFCE, or E17 (by far the most flexible out of the three, but if you don't like tweaking every little thing in your system, don't bother with it). Another thing I do know is that battery performance is benchmarked on Windows, because of course...that's what all the OEMs offer to their customers, and they assume no one would ever in the history of Earth want to use a different operating system (makes me laugh, actually)! I have found Karmic (Ubuntu 9.10) and Pinguy OS to both give me less battery life on my netbook than Windows, but that may be due to my particular power management settings (which are very liberal and aren't exactly the best for conserving the most possible energy) as well as a variety of other factors--I'm sure it varies from user to user and netbook model to netbook model. [WattOS]("http://www.planetwatt.com") however, claims to use a very small amount of power. Some more lightweight distros like [Puppy]("http://www.puppylinux.com/") and [Slax]("http://www.slax.org/") would probably also work out alright for you if you want the most speed and performance possible and are willing to compromise a bit on what software is available and how much tweaking you can do to your system.

---

### Post by snowpine on 2012-02-15
Broadcom requires the user to download and active a "firmware." This should be a painless 5-10 minute project in any distro (assuming you have temporary access to wired ethernet). Here's the instructions for Ubuntu:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

For your BCM4313:

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

(If necessary: ) Under the desktop menu System > Administration > Hardware/Additional Drivers, the STA drivers can be activated for use. 

Regarding power management, you might want to do a forum Search on Jupiter, it is a very handy dock app for netbooks.

Regarding system "peppiness" vs. lag, you might get better results with Xubuntu (Xfce desktop environment) or Lubuntu (LXDE).

You probably could have figured this all out in Fedora eventually, but if your heart is set on switching distros, Ubuntu is a good one to try. :) You might also be interested in Debian and Mint; these are two other ".deb-based" distros as opposed to Fedora which is ".rpm-based" method for installing software.

---

### Post by nineveh on 2012-02-15
Thanks for the quick replies, guys.

As regards the systems you mentioned - I currently have WattOS installed. It seems to be what I'm looking for, but I can't get the wireless to work at the moment. There's an issue with wired as well, it seems only to work with some routers, and the one I'm at now doesn't seem to be one of them, so I can't do much at the moment.

I didn't want to go into detail in the initial post so as to avoid making it far too big a wall of text, but what initially put me off Fedora 15 was the fact that wireless just abruptly stopped working months after having no problems whatsoever, and I was unable to fix it. Wired appeared to have stopped working as well - turns out it just started being selective, like I said before.

My first instinct was to try upgrade to Fedora 16, thinking it would resolve the issues, but they all persisted. I suppose I could have probably got it working in the end, but after having FINALLY managed to get a wired connection working on F16 today, I started an update only to have it print out errors some 30 mins into it, and end up giving me Kernel Panic. I don't mind putting effort if it yields results in the end, but there is a limit to my patience, and this definitively put me off Fedora per se.

Anyway, since my problems seem not to be distro-dependant, I'll see if I can get WattOS to work first. If I don't like it, I'll try out ubuntu with the relevant tweaks or some of the other OSs mentioned.

Thanks again. :)

---

### Post by cwklinuxguy on 2012-02-15
^No problem at all. Hope things work out for you.

---

### Post by drawkcab on 2012-02-15
I've worked with these broadcom problems for years.

What often happens is that, for whatever reason, the standard driver doesn't turn on some broadcom cards.  It's as if the card remains shut off at the level of the BIOS.  To make a long story short, you have to do a lot of Googling and editing configuration files but you can find a way to edit the config file so that the card turns on when you boot.

---

### Post by Rodney9 on 2012-02-16
[COLOR="Blue"]**Lubuntu**[/COLOR]

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by fuduntu on 2012-02-16
If you want to stick with an RPM based distribution, take a look at Fuduntu.  Your Broadcom woes can be solved with little more than an ethernet connection, and yum install akmod-wl if it isn't detected and working out of the gate.

---

### Post by snowpine on 2012-02-16
Fuduntu is very nice; I've been using it for about a month, it feels right at home for me, switching from Fedora and CentOS. :)

---

### Post by mihalybaci on 2012-02-16
I have Ubuntu 10.04 on my laptop right now, and it works pretty well. Though I think I'm going to switch to Lubuntu when the 12.04 LTS release comes out in April to try and save some operating power since LXDE is a bit lighter weight. If you do like to tweak everything, my brother uses Openbox because its lightweight and you can customize EVERYTHING. Another option would be #! (Crunch Bang) Linux, but again you have to spend a while to get it set up.

---

