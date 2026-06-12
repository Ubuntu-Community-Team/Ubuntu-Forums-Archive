---
title: "ATI makes my ubuntu crash"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-04-12
Well i didn't listen about not getting a ATI card. Well now i got it, Sapphire X1950 PRO 512MB AGP. Ubuntu doesn't want to boot at all... But my windows disk boots fine. 
What is the problem? May it be possible to install the ATI drivers now with my Geforce card in an then put the ATI card back in and boot it up? 

I really don't want to change from Geforce to ATI every time i want to play a game.

Anyone knows about a good idea how this could be fixed?

Thanks.

---

### Post by U5tabil on 2007-04-13
no one that knows why? and how i can fix this?

---

### Post by TrevorNet on 2007-04-13
From my experience ATI sings a sad-sad-song when it comes to supporting Linux in general. I bought my ATI card back in Windows days and have had to suffer for it ever since I moved up to Linux (Ubuntu/Fedora). Of the several times I've tried to install ATI specific drivers, I met with failure. Sorry... I really wish *I* had better news. If you do a forum search, I am sure you will find a "How To" or two. I've followed most of them. For games, I use my work XP laptop.

As for swapping out the different video cards, I think your overall experience would diminish. Under another distribution, just swapping out the monitor for a wide-screen caused my system to not boot into Gnome.

Dude, what a downer post. I'm going to end now by saying that I hope someone finds a sure-fire way to install ATI cards and drivers. I've missed playing my Unreal2004, Quake3, and Doom, on something besides my craptop.

---

### Post by freebird54 on 2007-04-13
It should be possible to boot up with the ATI card in - then do the adriver install.  Try from a recovery session, and run this command:

```
sudo dpkg-reconfigure xserver-xorg
```

Which will put you into a text mode interface to resetting your x server options (essentilly rebuilding your xorg.conf file). Most of what you see will be OK to leave either empty, or as default - except the bits about the monitor and resolution settings. By the way - <tab> key to move around between items, <arrow> keys to move within an item, <space> to 'mark' or select items (such as resolution values) and <enter> to choose OK or confirm a choice.

When you come to the bit about which driver to use, try **vesa** - they are not very capable, but they should get you in and running.  Once you are running, one method of getting the newer drivers installed that doesn't take a lot of work is to run the ENVY script from [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)  This APPEARS to be about nVidia drivers, but it does ATI as well.  Let it do its thing, and enjoy the results.

---

### Post by U5tabil on 2007-04-13
It sound like an good idea. But insted of rewriting stuff i think i will just wait until the new ubuntu release the 17 this month. Then i can install that vesa driver and do that ENVY script :) 

But i am only using this pc to surf, check mail, watch movies, chat and so on. I use the windows disk only to play on nothing more. So i really don't need any good driver that delivers the full performance of the graphic card.

---

