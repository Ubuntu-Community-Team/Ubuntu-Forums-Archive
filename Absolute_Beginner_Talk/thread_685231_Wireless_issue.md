---
title: "Wireless issue"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by phelan1988 on 2008-02-02
I know there are threads like this, and I've been looking through them as best I can, not finding anything that seems to be helpful at all - my roomate said his friend installed ubuntu and everything on his laptop worked just fine - I've been wanting to try this for a while so I did, and now... lo and freakin behold.

No wireless. 

For reference, I'm running ubuntu 7.1 on an Acer Aspire 5100 that was previously cursed by Vista. Vista has been removed and that partition formatted, I dont want it anymore. 

Running iwconfig in terminal informs me there is no wireless card or anything of the sort, despite the obvious fact that one exists - I went first to the help menu, which told me to go to the synaptic package manner and install ndisgtk - which isn't there. I went online, found that, and it told me the prereq ndiswrapper -utils is not satisfiable. So, I went, downloaded ndiswrapper, but for the life of me I cannot figure out what to do with it. I run the executable but it just pops up the terminal and then closes it, and frankly, though I'm kinda ashamed, I have no idea at all what the readme is talking about - windows has apparently ruined me a bit. 

It says something about finding the right driver for the card, I THINK I have, but frankly Acer's site SUCKS and doesnt actually tell me what the card is, it just lists a bunch of drivers for this model laptop,  plus, for some wierd reason, I can't open the device manager to see what it says there. Basically, everything in the help files doesnt seem to exist, and none of the things I've tried or been directed to from other people's posts seems to work, and I just dont have the experience with this sort of thing to fix it - so I'm hoping one of the experts here does...

Thanks

---

### Post by quimbo on 2008-02-02
While I don't have a laptop and am no guru I did do a quick search as I too have had problems in the past getting hardware to work - this is what I found.

Site 1: [http://www.linuxforums.org/forum/linux-laptops/76298-linux-acer-aspire-5100-a.html](http://www.linuxforums.org/forum/linux-laptops/76298-linux-acer-aspire-5100-a.html)

Site 2: [http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)

Hope this helps you out.

PS according to the people at the first site you should have a Broadcom card.

---

### Post by phelan1988 on 2008-02-02
I'll try some of this, thanks - the problem is those guides refer to ndiswrapper which like I said I can't get to work...

---

### Post by legend2440 on 2008-02-02
This might help


[http://ubuntuforums.org/showthread.php?t=609297](http://ubuntuforums.org/showthread.php?t=609297)

---

### Post by phelan1988 on 2008-02-02
No, unfortunately it doesnt. I've already installed the driver using that method, it doesnt work.

I think I need the other version of the driver, the net5416 instead of net5211 but I can't find that one anywhere, 5211 is the one on the acer site and the download the guide links me to for the 5416 is, for some reason, the 5211 again...

UPDATE - Finally got it working, I found the 5416 driver, saved the ndiswrapper settings, and now it works like a charm. Anyone with an Aspire 5100 should check this page out
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

