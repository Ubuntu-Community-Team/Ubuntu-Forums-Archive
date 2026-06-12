---
title: "Need some help with X"
date: 2008-02-10
forum: Arch and derivatives
---

### Post by lespaul_rentals on 2008-02-10
I'm trying to get either KDE, KDEmod, or Xfce installed on my Arch system.  I can get all the necessary packages but when I run **startx** I get all sorts of errors.  If I run **startx** as root the same thing occurs.  I tried installing x-server, xinit, all those packages, but no dice.

Can anyone tell me how they got X working?  Thanks, it's appreciated.

---

### Post by sujoy on 2008-02-10
for KDEmod have a look here. [http://kdemod.ath.cx/](http://kdemod.ath.cx/)

as for X, you need to do a xorgconfigure and then check if it works. also make sure you got the required drivers. i use an intel 945 board with onboard graphics and i needed to do pacman -S xf86-video-intel to get my x working

---

### Post by Rumor on 2008-02-10
I generally use hwd to set up X.
```
pacman -S hwd
hwd -u
hwd -xa
```

hwd -u updates the xorgtable
hwd -xa generates and installs your xorg.conf file

More info here: [http://user-contributions.org/projects/hwd/hwd.html](http://user-contributions.org/projects/hwd/hwd.html)

---

### Post by K.Mandla on 2008-02-10
> **Rumor said:**
> I generally use hwd to set up X.
```
pacman -S hwd
hwd -u
hwd -xa
```

hwd -u updates the xorgtable
hwd -xa generates and installs your xorg.conf file

More info here: [http://user-contributions.org/projects/hwd/hwd.html](http://user-contributions.org/projects/hwd/hwd.html)
Hm, I always do ...
```
X -configure
```
but I'll have to see if that works better for me. I remember using it a long, long time ago, but I stopped. I don't remember why. :-k

---

### Post by lespaul_rentals on 2008-02-10
> **sujoy said:**
> for KDEmod have a look here. [http://kdemod.ath.cx/](http://kdemod.ath.cx/)

as for X, you need to do a xorgconfigure and then check if it works. also make sure you got the required drivers. i use an intel 945 board with onboard graphics and i needed to do pacman -S xf86-video-intel to get my x working

Thanks, but I followed the directions on that website *to the letter* and pacman said there was an unresolvable conflict between **kde-arts** and **arts**.  I could not remove **arts** either.

I know I have standard drivers and everything.  My motherboard with its on-board graphics never needs special drivers.  I got X and KDE working before with a previous install of Arch.  The only reason I didn't stick with it was because of the horrible interface for KDE; the desktop, kicker, etc. were not seamless (is there a fix for that?).

Thanks for that post, Rumor.  I will try that out as soon as I get a shower. :)   Thanks for the support guys.

---

### Post by sujoy on 2008-02-10
most welcome.

as for KDE or KDEmod, well i didn't install it myself. i made myself a command line system, and awesomeWM for browsing :)

---

### Post by bwtranch on 2008-02-10
Hi! I didn't have any problem with installing Gnome as a DE. BTW I have the 64-bit version of Arch. So, I first installed the xserver as per instructions and then tested it. Got me a nice little x, and then gnome. That all worked. So, then I installed a couple of KDE apps that I like, but couldn't get KStars without re-inventing the wheel, So, I went to the kdemod website and followed those instructions to the letter. I just boot into gnome and the apps I like are there. I tried both K3b and KStars and they work fine. I like krecipes, too, but it may be more trouble than it's worth on the 64 (I have a 32 I can use it there, so, no biggie). I also installed SQLite and the install went good, but I haven't tried it yet, (I did it the regular way, I'm still not used to the abs yet, and they've made some changes and some of the dir are different than what they say in the wiki. Hey, it's only day 2.4 for me, I'm doing good. Wish you luck. Oh, one thing I still like about Ubuntu? The forum:)

---

### Post by gordonh on 2008-02-10
I've a huge problem with X in that I can't get a GUI at all.

It's not practical to post the output, as I've no means to cut and paste between the ubuntu box with the problem and the windows box I'm forced to use here.

basically, I get CLI output 
failed to load module "i810" (module does not exist, 0)
and
No drivers available.

any help would be greatly appreciated

edit.  I've just run dpkg-reconfigure xserver-xorg as found in another post, and the failed to load line does not now appear

---

### Post by fwojciec on 2008-02-10
> **gordonh said:**
> I've a huge problem with X in that I can't get a GUI at all.

It's not practical to post the output, as I've no means to cut and paste between the ubuntu box with the problem and the windows box I'm forced to use here.

basically, I get CLI output 
failed to load module "i810" (module does not exist, 0)
and
No drivers available.

any help would be greatly appreciated

edit.  I've just run dpkg-reconfigure xserver-xorg as found in another post, and the failed to load line does not now appear

You should probably install the xf86-video-i810 driver.  Or xf86-video-intel should work as well, I think, althogh you have to change the driver to "intel" if you plan on using the intel driver rather than i810. 

See [http://wiki.archlinux.org/index.php/Beginners_Guide#Installing_and_configuring_X](http://wiki.archlinux.org/index.php/Beginners_Guide#Installing_and_configuring_X) for more info about this.

---

### Post by K.Mandla on 2008-02-12
> **gordonh said:**
> I've a huge problem with X in that I can't get a GUI at all.

It's not practical to post the output, as I've no means to cut and paste between the ubuntu box with the problem and the windows box I'm forced to use here.

basically, I get CLI output 
failed to load module "i810" (module does not exist, 0)
and
No drivers available.

any help would be greatly appreciated

edit.  I've just run dpkg-reconfigure xserver-xorg as found in another post, and the failed to load line does not now appear
Are we talking about Ubuntu or Arch? You're positing in an Arch Linux support thread. I can move your question, if it's in the wrong place.

---

### Post by gordonh on 2008-02-13
> **K.Mandla said:**
> Are we talking about Ubuntu or Arch? You're positing in an Arch Linux support thread. I can move your question, if it's in the wrong place.

Yes I'm using Ubuntu.  I posted here as the original question is relevant to my problem.

Thanks

---

### Post by RedSquirrel on 2008-02-14
> **lespaul_rentals said:**
> I'm trying to get either KDE, KDEmod, or Xfce installed on my Arch system.  I can get all the necessary packages but when I run **startx** I get all sorts of errors.  If I run **startx** as root the same thing occurs.  I tried installing x-server, xinit, all those packages, but no dice.

Can anyone tell me how they got X working?  Thanks, it's appreciated.

[http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)

I use 'X -configure' to generate a basic xorg.conf. It hasn't let me down.

As you may know, there is now a package group for xorg:

```
~$ pacman -Sg xorg
xorg
    xf86-input-keyboard  xf86-input-mouse  xf86-video-vesa  xorg-fonts-100dpi  xorg-fonts-75dpi  xorg-res-utils  xorg-server  
    xorg-twm  xorg-xinit  xterm  

```

Don't forget to install an appropriate video driver for your h/w:

```
lspci | grep VGA
```

I would recommend that you setup a basic X configuration and make sure it works before trying to run a desktop environment.

---

