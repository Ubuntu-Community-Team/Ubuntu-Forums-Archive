---
title: "[SOLVED] Command line to revert to factory default?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by FrancesL on 2008-02-25
Hi,
Like so many un-informed newbies ..I have been 'trying' things that I find in the forums , it has backfired on me now..in so much as I just followed a 'how to' that gave command instruction to install compiz-fusion on an Acer Aspire 4315, which has now 'crashed'. Well  the screen went grey, then returned to normal but other than a VERY sluggish none responsive cursor, I could do nothing. I should have known better, but my mistake. 
Is there a way to revert to the settings I had before I made this change? or if not, then a way to get back to what it all was when I unpacked the box? Many thanks

---

### Post by jordanmthomas on 2008-02-25
It depends on what exactly you did.  Do you have a link for the tutorial you followed?

---

### Post by FrancesL on 2008-02-25
> **jordanmthomas said:**
> It depends on what exactly you did.  Do you have a link for the tutorial you followed?
I searched and forund the tutorial using Acer Aspire 4315
Also I have used the power button and restarted ..have managed to open add/Remove and applied changes to remove Advanced Desktop effects..is that enough?

Have just returned the desktop to No Effects..Hope thats enough..oh and the tutorial was in the hardware and laptop section on Ubuntu forums headed [ Acer Aspire 4315 ] - Installation and Workaround

this is a copy and paste: 
The next thing to do if you want to enable compiz, you can do a workaround by editing an executable file. But please remember that by doing so, you won't have any video playback unless you disable XV (hardware accelerated playback) in Ubuntu. If you still want to enable compiz, here's the trick:

Quote:
1. Fire up terminal
2. Type these: mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
3. Go to System -> Preferences -> Appearances and activate Desktop Effects at the last Tab.
4. If all goes well you will have compiz running.
5. If you want advance compiz configuration (you should), type these in terminal: sudo apt-get install compizconfig-settings-manager

---

### Post by jordanmthomas on 2008-02-25
Ok, if that's all you've done you can undo it with:
```
rm ~/.config/compiz/compiz-manager
```
Go to System -> Preferences -> Appearances and uncheck Desktop Effects at the last Tab.
```
sudo apt-get remove compizconfig-settings-manager
```

If it's still slow after that, you either have another problem or have done something else to mess up.

---

### Post by FrancesL on 2008-02-25
Thanks for your help, I followed your guidance
seems ok thanks, but for sure ..I could have mucked up something else..why not? I am new!!! and just giving it my best shot

---

