---
title: "UBUNTU Hardy 8.1 PPC G4 Rage128 issues"
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by scottdhansen on 2008-11-16
Thanks to many in the forums I was able to locate and install the alternate Hardy Heron.  I have also followed the [https://wiki.ubuntu.com/PowerPC]("https://wiki.ubuntu.com/PowerPC") information as well as toying with the xorg.conf until my fingers started bleeding.  This mainly focused on the xorg.conf posted here [https://wiki.ubuntu.com/PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues").

I have also toyed with other xorg.conf files posted in the forums.

running startx leads to a warning ***Invalid IO Allocation*** and some errors
Unable to find a valid framebuffer device
R128(0):  Failed to open framebuffer device...
Screen(s) found, but none have a useable configuration.
Fatal server error:
No screens found...

Some Detail...
uname -r 
2.6.24-21-powerpc

lspci | grep VGA
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage PF/PRO AGP 4x TMDS


Before posting more detail I wanted to get a feel for what is needed to properly diagnose.  I feel I am a fairly advanced user of UNIX but getting X to work is driving me crazy.

---

### Post by stream303 on 2008-11-16
Since Intrepid contains nothing in the default xorg.conf, I found that the following keeps it from barfing on me - of course I'm using values for my G5 iMac, but Intrepid seems to like the syntax.  It appears that using anything less, even if the sections are empty, causes it to go into low-graphics mode.  I'm still experimenting, but I was overjoyed that I'm now able to make a custom xorg.conf for Intrepid that doesn't get rejected outright:

[http://ubuntuforums.org/showthread.php?t=978303](http://ubuntuforums.org/showthread.php?t=978303)

For your rage card, also be sure to see the old ppc archived read-only threads about it - maybe there's something in there that will work:

[http://ubuntuforums.org/showthread.php?t=3723](http://ubuntuforums.org/showthread.php?t=3723)

Let us know how it goes!

---

### Post by scottdhansen on 2008-11-16
Thank you for the information.  I have tried the links you provided.  Much to the same effect.  startx now throws:
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "xtt" (module does not exist, o)
(EE) No drivices detected
Fatal server error:
no screens found
I tried substituting my xorg.conf with the one listed in entry #10 on [http://ubuntuforums.org/showthread.php?t=3723]("http://ubuntuforums.org/showthread.php?t=3723") that you refrenced.  In reading further I am confused by what was tried/changed.

---

### Post by stream303 on 2008-11-17
When I first started out, I just wanted to use dithering for my lcd display, so I made a very short xorg.conf that enabled that option, hoping that Intrepid would deal with the rest of it.

My G5 iMac didn't need any special xorg.conf at all, except for when I wanted that option.

So, I ended up putting things back in until it no longer threw me into low-graphics mode.

The plan was not to copy verbatim an old xorg.conf from years ago, but try to let Intrepid handle most of it, and me supplying just the bare essentials.

I did this when very tired, and hate to admit that I didn't take notes - it was a very frenzied vi / logout / login session until it seemed to take.  I'm sure it could use improvement, and other models might need even more.

I was hoping that all one really needed to change was their video driver, vertical and horizontal freqs, and go to town - but it looks like perhaps BUSID's and other things may be needed for different models....

---

### Post by scottdhansen on 2008-11-21
Would you suggest Intrepid on a G4?  If so should I try the alternate install if there is such a thing?

---

### Post by stream303 on 2008-11-22
> **scottdhansen said:**
> Would you suggest Intrepid on a G4?  If so should I try the alternate install if there is such a thing?

Sure.  In fact the "alternate" text-based install image is the one I most frequently recommend, since the live-desktop requires a lot of ram that you may not have, and tries to dump you immediately into a gui environment, which X is not trained to handle for many models.  Thus, the typical boot-to-black-screen effect is seen. :)

At least with the alternate, you can be sure you can at least get the data on the drive, and then use rescue-mode or linux-single mode techniques to custom edit xorg.conf or yaboot.conf as necessary.

You must know how much ram you have, as trying to put Intrepid on a 64 or 128mb box may be impossible.  Ram is your friend, unless you want to run mostly a commandline system, or perhaps one with just a bare minimum X system on it with a DIY approach.

---

### Post by scottdhansen on 2008-11-25
Thank you for the reply.  I will give the alternate install a try and post back here.  If I need to look for fixes to xorg.conf or yaboot specific to Intrepid Ibex should I filter bases on PPC installs only or are notes from users running intel equally valid who have a Rage128 card?

---

### Post by stream303 on 2008-11-25
I'd stick to the ppc installs since the yaboot boot loader is specific to the ppc, and we are also using the open-source video drivers.  Many Intel users are using the proprietary drivers, which may have options that aren't even recognized by the driver we use.

Tip:  after installation if your screen is black, try this at the second-stage yaboot boot: prompt

```
Linux video=ofonly nosplash
or
Linux nosplash
```

The goal is to get to a point where the system is installed, and you can easily edit /etc/yaboot.conf and /etc/X11/xorg.conf (if necessary) by using a virtual terminal (ctrl-alt-f2) to get to a text-based editor.

If things are really rough, then one has to rely on rescue-mode or Linux single, to go back in, but hopefully you won't have to do that.

Keep it fun!

---

### Post by baycoo01 on 2008-11-26
Charge stun. This 1-second stun has been one of the most annoying mechanics in a warrior's arsenal to date.we provide wow gold,cheap wow gold,warcraft gold. Charge is almost mandatory for entering combat effectively and forcing yourself to begin your stun DR (which resets after 20 seconds) with a 1 second stun just so you can get in melee range and generate a little bit of rage off of it seems very counter-productive, especially with a Protection-oriented build with 2 other controlled stuns (concussion blow and shockwave) and for any warrior in general as it shares DR with intercept stun. we provide wow gold,cheap wow gold,warcraft gold.Would it be possible to change Charge into a 1-second immobilize and 2-second interrupt? This would effectively yield the same results even for snare-immune targets (via hand of freedom) but would not annoyingly start your stun DR worthlessly. [wow gold](http://www.baycoo.com)[wow power leveling](http://www.baycoo.com/powerleveling-wow.asp)[wow power leveling 80](http://www.baycoo.com/powerlevelingreport.asp)[wow gold paypal](http://www.baycoo.com/wow_gold_paypal.html)[wow gold reviews](http://www.baycoo.com/wow_gold_paypal.html)

---

### Post by didg on 2008-11-27
> **scottdhansen said:**
> Thanks to many in the forums I was able to locate and install the alternate Hardy Heron.  I have also followed the [https://wiki.ubuntu.com/PowerPC]("https://wiki.ubuntu.com/PowerPC") information as well as toying with the xorg.conf until my fingers started bleeding.  This mainly focused on the xorg.conf posted here [https://wiki.ubuntu.com/PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues").

I have also toyed with other xorg.conf files posted in the forums.

running startx leads to a warning ***Invalid IO Allocation*** and some errors
Unable to find a valid framebuffer device
R128(0):  Failed to open framebuffer device...
Screen(s) found, but none have a useable configuration.
Fatal server error:
No screens found...

Some Detail...
uname -r 
2.6.24-21-powerpc

lspci | grep VGA
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage PF/PRO AGP 4x TMDS


Before posting more detail I wanted to get a feel for what is needed to properly diagnose.  I feel I am a fairly advanced user of UNIX but getting X to work is driving me crazy.

Do you mean 8.10 or Hardy?

For 8.10 I had to add to Section "Device":

        Option          "NoINT10" "true"
        Option          "UseFBDev" "false"


Draw back fastswitch doesn't work
 
you can also add in the same section: 
        Option          "NoDRI"

with
ection "Module"
        disable "dri"
        disable "glx"
EndSection

With a Rage 128 OpenGL is hopeless :)

---

### Post by skigil on 2008-11-27
I have almost the same problem. I am going to try the above tonight to see if I can get Xorg working on my G4 Rage128.

---

