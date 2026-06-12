---
title: "Wireless toggle borked"
date: 2011-11-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by clegends on 2011-11-08
Hi Ubuntuer's, not sure how to fix this one. My wireless toggle seems borked. I can use the hot key to toggle it on or off (fn+f2), but after toggling my wireless off, after I toggle it on again, no networks are detected. Any idea how to trouble shoot this? Currently I need to reboot in order to detect any wireless networks again... feels like I'm back on Windoze, way back when.

I'm running an eeepc 1015px with ubuntu 11.10, and all current updates. This issue has been present since installing, and testing the beta versions. I haven;t filed a bug yet, as 1, I'd like to see if there's a workaround, and 2, I'd like to figure out the best way to troubleshoot this first. Cheers.

---

### Post by clegends on 2011-11-14
***Bump!***

---

### Post by r_mano on 2011-11-15
It happens the same to me (to be honest, it's not a new thing, it's happening since 11.04 --- before the killswitch did not work ;) ). 

It's a workaround, but you do not need to reboot: for me 

```
sudo restart network-manager
``` 

is all what's needed to get the wireless back. With wired network sometime I have to unload/reload the atl1c module:

```
sudo rmmod atl1c
sudo modprobe atl1c
```

---

### Post by clegends on 2011-11-15
Thanks heaps for that! That's a fine workaround. I'll file a bug in launchpad, and see if we can get this fixed for 12.04, if not sooner. the 1015px's are 'certified' hardware, so it would be good form to get this solved. Cheers.

---

### Post by r_mano on 2011-11-15
> **clegends said:**
> I'll file a bug in launchpad, and see if we can get this fixed for 12.04, if not sooner. 

Happy to help, you're welcome! 

Please post the bug number here, so that I can add myself to it (I have a 1005P, but I suppose they'revery similar).

---

### Post by clegends on 2011-11-15
Wow, there were several really similar, if not identical bugs. I'll find the bug number later, but looks like a patch has been proposed that fixes the problem. I've asked for a copy of the .deb, see what happens. The patch is actually there, but I'm not sure how to apply it, and to be honest, I'm unlikely to find out. You any good at patching debs?

---

### Post by r_mano on 2011-11-15
I was ;-)(*), now I have not so much time to play with sources, packages and similar things. 

Cheers,
       Romano

(*) my first Linux distro was Slackware, kernel 0.99pl8, around 1989.

---

