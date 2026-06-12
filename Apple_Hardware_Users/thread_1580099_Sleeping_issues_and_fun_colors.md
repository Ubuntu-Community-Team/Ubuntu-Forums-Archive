---
title: "Sleeping issues and fun colors"
date: 2010-09-22
forum: Apple Hardware Users
---

### Post by killersoap on 2010-09-22
iBook G4 // 10.04 // 

Instead of getting a sleeping computer, I am presented with a constant barrage of changing, repeating, solid colors.

That is: the screen goes from solid black to solid red to solid blue to solid grey and so on, then repeats for an indefinite amount of time.

When left alone I get my screen saver (10m) until it is set to sleep (20m). At the magical 1/3 of an hour mark the colors start. 

My beef with this is: I always have the trusty laptop with me at home, but it gets set off to the side when I am not perusing the series of pipes and tubes we call the internet. After 20 minutes of inactivity it starts screaming in the periphery of my vision (USE ME! USE ME!).

Like a persistent puppy, I have to play with it or shut it up and put it off. But then it takes considerably longer to get going again, should I feel the need to look up who first introduced cereal to milk. Or play tug-of-war with an inferior animal.

I am very comfortable with geek-speak and the rest but clearly have no diagnostic ability with this particular problem. If I am missing some obvious post elsewhere please give a link and I will wander off with my head hung low, muttering curses.

Help me. Please.

---

### Post by linuxopjemac on 2010-09-23
What exact iBook G4 ?
[http://everymac.com](http://everymac.com)

Do you have normal X behavior? You can login and see a nice desktop?

---

### Post by killersoap on 2010-09-23
Mid 2005 as shown [_here_]("http://www.everymac.com/systems/apple/ibook/stats/ibook_g4_1.42_14.html")

Normal X behavior, everything has been working fine for quite some time, save the colors. It was not broken at any update that I can recall, it has always been.

On a side note, I could never get desktop effects to work. Maybe something with the graphics card and/or drivers is the cause of the colors as well? I cannot enable them on my old(er) PowerMac either, so I assumed being PPC was the issue there. I'll dig around.

---

### Post by linuxopjemac on 2010-09-24
Try like he did for his eMAc, maybe you could have compiz working too then. If it works, let us know what exactly you did.

Sleep problems are normally kernel related. I don't have such problems under Debian with a recent kernel.

---

### Post by killersoap on 2010-10-14
Well, after 2 weeks of messing around with drivers, screwing with xorg.conf, and countless restarts into simple graphics mode I have yet to make any progress in any form.

Which leads me to cry out for a:

bump.

---

### Post by linuxopjemac on 2010-10-14
People are very happy about MintPPC....

---

### Post by zeroti on 2010-10-14
have you tried disabling KMS on your graphics card? I have a radeon card. Put this in /etc/modprobe.d/radeon-kms.conf :

```
options radeon modeset=0
```

Then reboot. Visual effects work for me after this change, it could make sleep work too. However, I've been having some graphical issues with certain games that come installed with ubuntu. you might want to try them out before and after the change, to make sure it nothing gets broken. : )

---

### Post by killersoap on 2010-10-14
> have you tried disabling KMS on your graphics card? I have a radeon card. Put this in /etc/modprobe.d/radeon-kms.conf :

Code:

options radeon modeset=0

Then reboot. Visual effects work for me after this change, it could make sleep work too. However, I've been having some graphical issues with certain games that come installed with ubuntu. you might want to try them out before and after the change, to make sure it nothing gets broken. : ) 

I did exactly this (though I did not have a radeon-kms.conf file, I created one and placed the code inside) and now I have working Desktop Effects after a reboot. Have not tested anything else nor have I waited for the colors to start (or not I hope). I will update.

In the meantime I will check out MintPPC, I have a couple old Macs to mess around with.

Thank you kindly to both of you.

---

### Post by killersoap on 2010-10-19
With the changes indicated above, and nothing more, Desktop Effects works. However the flashing colors continue (though intermittently) and waking the machine from sleep/hibernation is impossible without a hard restart.

---

### Post by killersoap on 2010-10-19
On a separate note:

I have installed MintPPC on my PowerMac G4 (3,5) and have so far fallen in love. It is much snappier than my previous Ubuntu 10.04 install, and I have yet to see any downsides.

Save one, but I believe it is my own ignorance and selective vision:

I cannot seem to find the Software Manager. I will look elsewhere for help on this (but if you end up reading this linuxopjemac, maybe you could point me in the right direction? You have been a tremendous help in your other posts, that kind of support is a godsend).

I have looked and looked and am very embarrassed to ask such a thing but after a couple hours toying with my new OS I have to swallow my pride...

All in all, if anyone has issues with PPC's and Linux, MintPPC is the way to go. Now to install it on the lappy-toppy .  .   .

---

### Post by linuxopjemac on 2010-10-20
> I have installed MintPPC on my PowerMac G4 (3,5) and have so far fallen in love. It is much snappier than my previous Ubuntu 10.04 install, and I have yet to see any downsides.
All in all, if anyone has issues with PPC's and Linux, MintPPC is the way to go.

:)

Try Preferences -> Synaptic Package Manager
[http://www.mintppc.org/files/Screenshot-1.png](http://www.mintppc.org/files/Screenshot-1.png)

---

### Post by killersoap on 2010-10-20
Thanks again linuxopjemac.

After a breeze of an install on the iBook I have some wireless issues, but I will continue this discussion on the MintPPC forums.

---

