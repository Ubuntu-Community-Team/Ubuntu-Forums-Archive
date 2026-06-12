---
title: "Thought it would be safe to update to Edgy.. apparently not."
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by hyper7 on 2006-09-29
I ran update with the options to turn off, well, what I probably shouldn't have.

The latest edgy beta wouldn't boot.  I can't see why, as I followed the upgrade proceedure exactly.

Anyway, I'm not so concerned with edgy now, but I would like to get my dapper 6.06 install back.

I've no clue what to do command line wise to restore what I had.  All I know is that when I boot now, my video card goes mad.(Radeon Commando Pro 9000?).

And here I was, nearly 4 months into using dapper without a problem.

Any help would be appreciated.

Thanks.

---

### Post by hyper_ch on 2006-09-29
if you have /home on a separate partition I recommend just a total reinstall of (k/x/ed)ubuntu... however on how reverting back I have no clue... I even doubt that's possible... but I don't konw too much myself either.

---

### Post by hyper7 on 2006-09-29
> **sjau said:**
> if you have /home on a separate partition I recommend just a total reinstall of (k/x/ed)ubuntu... however on how reverting back I have no clue... I even doubt that's possible... but I don't konw too much myself either.

Yea, I can do that, but that's not what I'd like to do.

Suppose it'll be another one of those live and learn deals if someone doesn't show up to save me.

_Que guy in speedo_

It must have had something to do with the fglrx driver.. I can't see how else things coulda gone wrong. ](*,)

---

### Post by h2gofast on 2006-09-29
I wouldn't ask in another forum, but considering that this is the beginner talk, what do you mean by won't boot?  I imagine that you are getting a commandline login prompt asking for username, after X fails to load.  Or is grub screwed up and it won't even load linux.  If you could give us the Last thing your screen gives you after you turn your computer on, there is definitely a way to solve this.  
cheers.

---

### Post by hyper7 on 2006-09-29
I'm not sure if this will help or not.  Maybe you can give me some command line options so that i can fix the rest after.


I'll not put these in 'code'.. First thing that messes up "sis630 - smbus  bus not detected.

"failed to start server"

then it dumps some OS crap.. 

Lastly i get "Xserver now diabled"..

So this all has something to do with Xorg.

---

### Post by bigken on 2006-09-29
boot into safe mode and try sudo dpkg-reconfigure xserver-xorg ;)
its worth a try

---

### Post by hyper7 on 2006-09-29
> **bigken said:**
> boot into safe mode and try sudo dpkg-reconfigure xserver-xorg ;)
its worth a try

Good call.  I'll let you know what happens.

Worst case scenario "zomg!!  all my stuffs was free and i have to download them again!!!"..

Thanks for the help.

---

### Post by bigken on 2006-09-29
also in safe try sudo apt-get update & sudo apt-get dist-upgrade ;)

---

### Post by hyper7 on 2006-09-29
You're a harsh mistress, but i see where you're going.

Fudging around with the first set of commands you asked me to mess with, well, edgy at least acknowledged it existed... Seems to all go back to this stupid Xorg BS. I'll try the apt stuffs and let ya know what happens.

Thanks so much for your time.

---

### Post by bigken on 2006-09-29
what grahpics card do you have also you could try the vesa driver just to get into ubuntu then play about trying to sort the right driver ;)

---

### Post by hyper7 on 2006-09-29
> **bigken said:**
> what grahpics card do you have also you could try the vesa driver just to get into ubuntu then play about trying to sort the right driver ;)

I have a pretty old school card. Radeon 9000 Pro "Evil Commando"] 

I've done al you've asked and i'm stil clueless.  Edgy star4ts to boot, or boots as some may see it, but i'm left with what seems to be random characters and colors.

If it weren't for the fact that I like to FIX what may or may not be broken, i'd reinstall dapper.  Considering I have 755mb of Edgy right here and now, i'd like to make it work, if i can.

I'm not one to give up easily.  That's one of the reasons I like *nix.  

If you have any other ideas, let em fly.. otherwise i'll have to nuke this install and try again.

Gawd, this is bugging me.

---

### Post by hyper7 on 2006-09-29
> **bigken said:**
> what grahpics card do you have also you could try the vesa driver just to get into ubuntu then play about trying to sort the right driver ;)

I just started gaming in debian/ubuntu... I never bothered to in the past.  In fact, I decided I'd have no reason to go back to win, and I never will.  

Resolved or not, i've never seen a community like this.  i'll never go back to winwhatefver.

---

### Post by bigken on 2006-09-29
try dpkg-reconfigure xserver-xorg again and select vesa as your video driver ;)

---

### Post by hyper7 on 2006-09-29
> **bigken said:**
> try dpkg-reconfigure xserver-xorg again and select vesa as your video driver ;)

Can you tell me why?

I'm merely curious.

---

### Post by bigken on 2006-09-29
if it works your into your desktop then you can research your problem from there ;)

---

### Post by bigken on 2006-09-29
which driver is dpkg selecting for you ?

---

### Post by hyper7 on 2006-09-29
Maybe I'm stupid.

If you'd walk me through what you want me to do, I can be assured it's not me.

How to get into 'safe mode'.  What's up then?  I've done all that's been suggested, but I have the same result.

If you'd be willing to tell me how you'd do it, well, I'd try.

---

### Post by bigken on 2006-09-29
ok boot into single user mode 
at the promt type sudo dpkg-reconfigure xserver-xorg
when your asked about your video select manual selection and select the 
vesa driver the rest just select defaults ;)

---

### Post by bigken on 2006-09-29
i would also try this in the forum search bar **Radeon 9000 Pro drivers**

---

### Post by bigken on 2006-09-29
after you have run the dpkg command type startx

---

### Post by hyper7 on 2006-09-29
i know no other way.. i'm presented with which kernel i'd like to boot..

someone said hit F6 to boot into pure linux.... that works with debian, but not with ubuntu, or at least not for me.

---

### Post by hyper7 on 2006-09-29
god, i feel stupid..

---

### Post by bigken on 2006-09-29
yes and says something about single user mode or safe 
to enter the grub menu hit escape

---

### Post by bigken on 2006-09-29
[quote=hyper7;1558863]god, i feel stupid..[/qu

dont worry were all here to learn :cool:

---

### Post by hyper7 on 2006-09-29
here i go again.. you'll know if i get a better result..

---

### Post by podunk on 2006-09-29
At boot up on my computer there is a list of kernels. Use the one that has “recovery” after it (if it;'s there after an update that is)

I have an older ATI Radeon card and it's really easy to break the driver install in daper. I did it every time I tried to install compiz. Doing this
```
dpkg-reconfigure xserver-xorg
```

would result in my monitor being out of sync and then it was a complete no go, I couldn't even get a terminal.

Something that would work good enough to get me going enough to be able to reinstall the ATI driver was to have a back up of /etc/X11/xorg.conf I could write down the settings from “Section Screen” then open /etc/X11/xorg.conf  and enter those in by hand and change the driver in "Section Device” to vesa instead of flgrx and I could boot into the GUI.

The code I used to edit /etc/X11/xorg.conf was
```
 sudo nano  /etc/X11/xorg.conf
```

You might try this
```
ls-l /etc/X11
```

and see if there is something like an xorg.conf_backup in that directory. If there is you'll be able to copy the settings and get in the GUI and go to this page:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

to reinstall your driver.

a disclaimer – this is what I did for “Dapper” not Edgy, and I'm a total dumbass when it comes to Linux. I have however learned to back every thing up before I change anything. :-D

Another disclaimer – if you don't have a lot of data and what you do have is backed up – I found it a lot faster to just reinstall.

I've screwed this up so many times I'm an expert at reinstalling <sigh>

---

### Post by Kayne on 2006-09-29
Funny, I tried to update to Edgy today since it went beta. Downloaded the CD, put it in my drive and Dapper says that a new Ubuntu CD was detected and asks, if I should add it to Synaptic.
After reloading repositories, nothing happens afterwards :(

---

### Post by darrenm on 2006-09-29
I would:

Boot normally, let it error then drop you to a command prompt.

type:
```
sudo nano /etc/X11/xorg.conf
```
then go to where it says Driver "fglrx" change it Driver "ati"
then type sudo reboot and see what happens.

---

### Post by hyper7 on 2006-09-29
and now things work like they should.. 

\
thank you.. the rest i can fix  but you helped me get back where i needed to be..

i'd buy you a beer ii could..

---

### Post by hyper7 on 2006-09-29
> **darrenm said:**
> I would:

Boot normally, let it error then drop you to a command prompt.

type:
```
sudo nano /etc/X11/xorg.conf
```
then go to where it says Driver "fglrx" change it Driver "ati"
then type sudo reboot and see what happens.

some help  you were when a brother was trying to getme at leasty back up.

My video drivers are ******, but I can see.. the rest ican finger out.

---

### Post by bigken on 2006-09-29
send the doug through paypal im a big drinker lol ;)
which driver did you select ?

---

### Post by hyper7 on 2006-09-29
> **bigken said:**
> send the doug through paypal im a big drinker lol ;)
which driver did you select ?

i just went with vesa(which is slow as hell right now)...   

All I needed was to get bck to a place where I could mess with things again.

Oh, and i'll out drink you any day.. KDE or gnome.. hell.. XP or 2k..

thanks again

---

### Post by bigken on 2006-09-29
you could go though it all again and select ati as your driver its worth a try now you have the know how :D and belive me boy you will never out drink me rofl :tongue:

---

### Post by hyper7 on 2006-09-29
> **bigken said:**
> you could go though it all again and select ati as your driver its worth a try now you have the know how :D and belive me boy you will never out drink me rofl :tongue:

you showed me how to select my drivers.. .. I'll  be using some open GL shit soon enough now.  

You'll never out drink me.  I guess you're in eurpe somewhere.  You think americans weak.

I can appaend this with msn...or my email.. or i can spoof an addy.

---

### Post by hyper7 on 2006-09-29
> **podunk said:**
> At boot up on my computer there is a list of kernels. Use the one that has “recovery” after it (if it;'s there after an update that is)

I have an older ATI Radeon card and it's really easy to break the driver install in daper. I did it every time I tried to install compiz. Doing this
```
dpkg-reconfigure xserver-xorg
```

would result in my monitor being out of sync and then it was a complete no go, I couldn't even get a terminal.

Something that would work good enough to get me going enough to be able to reinstall the ATI driver was to have a back up of /etc/X11/xorg.conf I could write down the settings from “Section Screen” then open /etc/X11/xorg.conf  and enter those in by hand and change the driver in "Section Device” to vesa instead of flgrx and I could boot into the GUI.

The code I used to edit /etc/X11/xorg.conf was
```
 sudo nano  /etc/X11/xorg.conf
```

You might try this
```
ls-l /etc/X11
```

and see if there is something like an xorg.conf_backup in that directory. If there is you'll be able to copy the settings and get in the GUI and go to this page:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

to reinstall your driver.

a disclaimer – this is what I did for “Dapper” not Edgy, and I'm a total dumbass when it comes to Linux. I have however learned to back every thing up before I change anything. :-D

Another disclaimer – if you don't have a lot of data and what you do have is backed up – I found it a lot faster to just reinstall.

I've screwed this up so many times I'm an expert at reinstalling <sigh>

you and me both, brother...

---

