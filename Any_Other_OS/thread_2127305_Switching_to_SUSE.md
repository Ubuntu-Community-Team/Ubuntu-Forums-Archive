---
title: "Switching to SUSE"
date: 2013-03-19
forum: Any Other OS
---

### Post by ManamiVixen on 2013-03-19
After much consideration, I've decided Ubuntu isn't for me anymore. I've tried to like the new Ubuntu up to 13.04 and found the now Social-Centric OS a headache for me. The reason bieng I'm not a social media kind of gal and prefer a more traditional desktop. So most of what Ubuntu provides I end up removing or disabling resulting in an desktop that is pretty useless and far removed from what it's supposed to be. I just don't get what it Ubuntu really is about. So I'm moving to OpenSUSE and would really like some tips on how to best use it or a link to a great manual. Also want to know what packages you think I should be installed, codecs, drivers, ect... I've already dived into OpenSUSE and really like it.

---

### Post by The Cog on 2013-03-19
Have you tried Xubuntu - the XFCE desktop? That's the one I feel most at home with.

---

### Post by iponeverything on 2013-03-19
I agree with your observations - too many OS's and services seem to be overly or only social networking centric.  

With assumption being that everyone is on-board.  Luckily there are other choices, suse for example - 

I have a feeling that my Ubuntu days are numbered.

I am still at 10.04 on most of my boxes..

---

### Post by ManamiVixen on 2013-03-19
You know, maybe I'll give Kubuntu another try. I liked how it looked and ran. Also the Ubuntu core would make it more compatible with more software. Never really used it because of GTK issues in KDE which I just recently figured out how to fix. I happen to use GTK apps like Gimp and Audacious which look terrible in the default Oxygen GTK theme. So I'm going to install Kubuntu 12.04 64Bit.

---

### Post by iamkuriouspurpleoranj on 2013-03-19
[http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/](http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/)

The trouble for me with openSUSE is the AttachMate/Microsoft connection. Otherwise it's a fine OS and although its user base favours KDE, its Gnome version is considered equal by openSUSE itself.

---

### Post by MadmanRB on 2013-03-19
The problem with opensuse you will see is the lack of packages, such if you like watching netflix on opensuse?
Good luck on that.

Also the upgrade process on it is quite rough

---

### Post by ManamiVixen on 2013-03-19
Ok, after playing with a full install of OpenSUSE, (Yes I know I said I would Kubuntu, but changed my mind), I found the intelligence of Zypper in this release to be as advanced and vast as a few Lawn clippings. It constantly failed to install ANYTHING outside of the included repos because it couldn't figure out dependencies. Even the one-click installs openSUSE provided on their Wiki. It took me 45 Minutes to properly, properly as in get it to even load, install Cinnamon alongside Gnome-Shell and still, It didn't properly configure the desktop! No access to the desktop, just the panel, wrong start icon as in it loaded Ubuntu's Start icon, wallpapers were missing, ect... Also iw, required for wireless internet didn't install on my computer so I had no internet access, even with the network settings workaround. Lucky I had the full DVD and it had the package on it. So openSUSE 12.3 was a disaster. This is one case where a Live CD wasn't enought to see if I would like a distro. Also as MadmanRB stated, it never properly updated itself, I had to manually select the update packages it was ignoring in YaST2. I used openSUSE years ago. WHAT HAPPENED?!?!

I might just use Ubuntu again despite it not being targeted at users like me. At least it worked with zero hassles and was well designed. And no, I don't want to use Xubuntu. I dislike the XFCE enviroment. It's too archaic for my tastes. As for Cinnamon on Ubuntu, I prefer not to install it. It's just something about Unity, like it really dosen't need a replacement or companion desktop. It's fine the way it is and does everything, just not targeted at me, yet I want to use it. 

I am thinking of Fedora next. I used it in the period following Ubuntu 11.10's release. I wasn't happy at first with the Unity changes, then came back from Fedora to Ubuntu in full with 12.10. But Fedora isn't really relevant anymore is it?

---

### Post by ManamiVixen on 2013-03-19
Ok, I settled on Kubuntu 12.04. It does what I need, it works and is nice. Thanks to all that helped me and thanks to listening to my whining bum. I am happy now.

---

### Post by RoosterHam on 2013-03-19
I myself am considering trying KDE out on one of my Ubuntu machines. While I have to admit that, after I tried Fedora with the Gnome Shell, I prefer unity over the direction that the gnome project has taken, I still cannot say that either Unity nor GnomeShell make me feel at home infront of my screens.

I have a few Mint installs, and in the interest of keeping in touch with the broader Linux environment will also be trying openSUSE, but I don't have time to switch and test everything out there and migrate any of my primary systems. Lubuntu provides some great performance on my primary laptop where I run LXC and KVM for testing, but it isn't very pretty. Ubuntu, Debian and FreeBSD will always be the first three OSes I look to for my servers. But after preferring GTK for many years, I think it's time I give KDE another chance before reconsidering migrating to a completely different distribution.

I've done the whole migrate thing once before. Disgusted when unity took the default desktop position on ubuntu, I spat the dummy and installed Fedora. Unfortunately I had not realised the full extent of the changes gnome had made from v2, and I had forgotten why I had moved away from rpm based distributions in favour of .deb based platforms. In fact, a decade ago, I was so dissatisfied with .rpm based that I ran Slackware for quite a while, and was surprisingly happy with it. But Slackware had some limitations also.

So, after all that...

To install either xfce or kde on a lubuntu system, what is the procedure (commands) for a full default DE? But more than that, what extras would you recommend I install? What are the XFCE or KDE equivalents for the common tools to ubuntu/lubuntu that I should take not of?

---

### Post by MilesRdz on 2013-03-20
> **ManamiVixen said:**
> Ok, I settled on Kubuntu 12.04. It does what I need, it works and is nice. Thanks to all that helped me and thanks to listening to my whining bum. I am happy now.

You could also try adding a KDE backports PPA (so you could have the latest KDE version) and stick to Ubuntu 12.04.

---

### Post by buzzingrobot on 2013-03-20
I've installed and tried 12.3 and my experience was much different. Very polished, very smooth.  One-click installs worked.

Dependencies will not be satisfied if their host repository is not enabled, on any Linux.

---

### Post by sudodus on 2013-03-20
> **RoosterHam said:**
> ... So, after all that...

To install either xfce or kde on a lubuntu system, what is the procedure (commands) for a full default DE? But more than that, what extras would you recommend I install? What are the XFCE or KDE equivalents for the common tools to ubuntu/lubuntu that I should take not of?

You can install any of the [KLX]Ubuntu flavours into another one with these command lines

```
sudo apt-get install kubuntu-desktop
```
```
sudo apt-get install lubuntu-desktop
```
```
sudo apt-get install xubuntu-desktop
```

You will get some doublet applications (also doublet menu entries), but it can be cleaned out or migrated after testing according to this link

[[COLOR=#ff0000]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

---

### Post by malspa on 2013-03-20
> **buzzingrobot said:**
> I've installed and tried 12.3 and my experience was much different. Very polished, very smooth.  One-click installs worked.

Dependencies will not be satisfied if their host repository is not enabled, on any Linux.

True about the dependencies and repositories.

I don't have 12.3 installed yet, but I ran 12.1, and I have 12.2 running on a couple of computers here. My impression of openSUSE is that it's one of the best distros I've ever used, a lot better than I expected it to be (I've only been running it for about a year). About as stable and dependable for me as Debian Stable and Ubuntu LTS (I run both of those, too).

---

### Post by iamkuriouspurpleoranj on 2013-03-20
Just had a quick spin on openSUSE. Seems very good and I almost started to like KDE :-) But then I saw blue icons in the green theme. Blue and green should never be seen.

---

### Post by ManamiVixen on 2013-03-20
**[COLOR=#000000][MilesRdz]("http://ubuntuforums.org/member.php?u=566160")[/COLOR]**[COLOR=#000000] I already knew about the PPA and added it along with Xorg-Edgers and an upgraded kernel straight from the Ubuntu Mainline Kernel site. I'm no noob, just very picky and precise about what I want. As for SUSE, as I said, Zypper kept screwing up for me. Maybe it was the fact I was using Gnome instead of KDE, but I didn't like how broken the integration on KDE was with openSUSE. YaST2 used it's settings above the KDE settings causing all kinds of hell. On Gnome it made sense because Gnome lacks settings by design, but KDE gives you as many as it can. So there was a big rift in the settings and integration on openSUSE KDE and YaST2. [/COLOR]

---

### Post by cariboo on 2013-03-20
Closed by request.

---

