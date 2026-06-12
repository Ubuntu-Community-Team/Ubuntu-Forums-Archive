---
title: "I'M AN ID10T!!!! ...Need Help!"
date: 2008-02-19
forum: Apple Intel Users
---

### Post by KS. on 2008-02-19
ok so i finally got nix on my MBP using live cd........ everything was great EXECPT for the wireless driver, (which i still have NO clue to how to fix) ...*i can get around in term. but not too good with too many commands or there options.* .... AND, the ATI gfx card driver prob. SO .... i know theres a way to fix this, so i was playing around with the gfx card settings, and GUESS WHAT!?? ... i screwed myself by changing the settings, (stupid me!) ... and i KNOW the system's still there, i just can't see it? .... i can get to the cmd line. Is there any way to fix it, or fix it from the "safe mode" cmd line? ... or will i have to reinstall? 



I KNOW, I KNOW.... *TEST* SETTINGS NEXT TIME! lol.



Thanx all.

---

### Post by pmgr33r on 2008-02-19
From command line type

```
$ sudo dpkg-reconfigure xserver-xorg
```

and follow instructions to reconfigure x. This should do the trick

---

### Post by cyberdork33 on 2008-02-19
It might be helpful to use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install the ATI driver next time.

Also, I am assuming that you have an older Macbook Pro (since you are trying to install the ATI drivers), so this page might be of some help regarding the Wi-Fi:
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

---

### Post by KS. on 2008-02-19
Ok so i tired the "sudo..." and it works, BUT i guess i'm not choosing the right card or something. I've heard people say "vesa" so i tried that at a few different rez's and NOTHING.... so i went back and did the same thing with the ATI setting (because i know there's an ATI card inside this demon box of mine)..... still, nothing. ..... any idea's why? / or what to do?



Yes, i'm using a: MBP, 15", 2.16, 128 vRam, 1gb Ram, 2nd gen. 

Thanx for all the help everyone.

---

### Post by cyberdork33 on 2008-02-19
> **KS. said:**
> Ok so i tired the "sudo..." and it works, BUT i guess i'm not choosing the right card or something. I've heard people say "vesa" so i tried that at a few different rez's and NOTHING.... so i went back and did the same thing with the ATI setting (because i know there's an ATI card inside this demon box of mine)..... still, nothing. ..... any idea's why? / or what to do?



Yes, i'm using a: MBP, 15", 2.16, 128 vRam, 1gb Ram, 2nd gen. 

Thanx for all the help everyone.vesa is not the "right" driver for your computer. It is just a generic display driver that should work well enough to install your "right" driver. As I suggested, try using Envy.

---

### Post by KS. on 2008-02-19
is there a way to install envy from the cmd prompt? ...Cause i tried vesa, (just to get back to gnome) but it's not working. .... any other ideas?

Thanx again far all the help.

---

### Post by KS. on 2008-02-19
ok I GOT IT! thanx all, it's not your fault, apparently i'm just retarted! .... i went back in, choose the "vesa" and this time i !IDIDN'T! choose a rez, rebooted, and there it was! :-) sorry for all the trouble, Thanx for all the help! .... i'm about to go try the envy thing ;-)

if you find you have this problem try this:

Boot into safe (cmd line)
type in the "sudo..." cmd above.
choose "vesa"
DO NOT CHOOSE !!!ANY!!! REZ.
type "reboot" 

that will get you back to the default video settings and allow you to fix it from there. 

;-)

Thanx every.

---

