---
title: "[SOLVED] Unable to get ATI Graphics card.."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by R@inm@n on 2008-02-05
I loaded Win XP Pro in Ubuntu 7-10 using Virtualbox just to see how it runs. I got everything going ok except my ATI graphics card, I cant load the drivers for it.

It's a dual-boot machine with XP Pro and Ubuntu running on the same HDD.

Any ideas how I can load some drivers for my graphics card please?

Win XP Pro seems to run fine in Virtualbox on Ubuntu ... :)


  R.

---

### Post by jan quark on 2008-02-05
you did check the restricted drivers manager, didn't you?

system > administration > restricted drivers ?

---

### Post by R@inm@n on 2008-02-05
I just did that, and enabled the ATI graphics...Now when I try to boot into Ubuntu, I get a screen message saying "Video Mode Not Supported" and I can't get into the Ubuntu OS.  I'm posting this through my Win XP OS.




   R.

---

### Post by R@inm@n on 2008-02-05
I tried recovery mode, it failed on Firestarter Firewall, then on the second go, gave me a root command prompt...

I'm lost on this one...:(

As it stands now, I can't get into my Ubuntu 7-10 system.

 When I just try to boot into Ubuntu normally, the "Video Mode Not Supported" comes up on my monitor.


 I hope I havn't killed my gibbon...:confused:



   R.

---

### Post by Dennis on 2008-02-05
> **R@inm@n said:**
> I tried recovery mode, it failed on Firestarter Firewall, then on the second go, gave me a root command prompt...

I'm lost on this one...:(

As it stands now, I can't get into my Ubuntu 7-10 system.

 When I just try to boot into Ubuntu normally, the "Video Mode Not Supported" comes up on my monitor.


 I hope I havn't killed my gibbon...:confused:



   R.

No it''s not dead!

This happened to me with an X300 card, you have to run the command dpkg-reconfigure xserver-xorg in the terminal. I can't remember exactly how I did it but I'm sure someone will be along soon. All is not lost. :lolflag:

---

### Post by R@inm@n on 2008-02-05
I hope someone can help me out... Is there a command in Recovery Mode that lets me access Ubuntu OS again?


   R.

---

### Post by jan quark on 2008-02-05
try this command in recovery mode 
it reconfigures the xserver automatically

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by R@inm@n on 2008-02-05
No Need to now....me = debian genius... :lolflag:


   Seriously, I sat and thought about what I had done....I enabled the ATI card in Ubuntu, which was connected to my monitor via a digital cable from the computer.  I reasoned that the sign that came up on the monitor screen " Video Mode Not Supported" was because Ubuntu wasn't able to handle the digital mode, so I substituted an ordinary non-digital line from the computer to the monitor...and Presto!   


I'm typing this in Ubuntu...yay!  My gibbon lives!...:lolflag:



  Thanks for the help.


   R.

---

