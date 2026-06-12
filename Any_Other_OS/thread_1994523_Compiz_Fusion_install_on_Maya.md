---
title: "Compiz Fusion install on Maya"
date: 2012-06-02
forum: Any Other OS
---

### Post by noob.bot76 on 2012-06-02
Hello, 

First off, I'm not very computer savvy, so layman's terms/explanations are appreciated. 

I've just installed Mint 13 Maya. I'm trying to get Compiz Fusion to work. 

I've installed the compiz-fusion-plugins-extras, as well as compizconfig-settings-manager.

However, after selecting all the effects, etc. I'm still getting nothing. I'm reading about downloading new drivers, enabling compiz fusion in different ways, but nothing specific about MInt 13. 

I tried the following advice from compiz fusion wiki: 
                                  ~ $ LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &  
  
This ended up making the windows have less graphics (no "x-out" boxes or maximize boxes in the top right corner). Side question: Should this and, if so, can this be undone? (it seems to be gone after reboot).

Anyways, any help getting this to work would be appreciated. 

Thanks

---

### Post by jinbatsu on 2012-06-19
Try activate Windows Decoration in CCSM setting.

---

### Post by Skara Brae on 2012-06-19
> **noob.bot76 said:**
> This ended up making the windows have less graphics (no "x-out" boxes or maximize boxes in the top right corner).
Sorry, noob.bot76, no help from me. But I had the same "issue". I was also no longer able to move program windows...

I found it too much hassle to un-do those "problems" - following the procedure to uninstall Compiz did not work - so I solved it the "MS Windows-way"... Now Mint "Mate" works fine.

So, no Compiz in Linux Mint (pity, for it worked and looked awesome in "Lucid Lynx"), but that's ok. Basically Compiz is only eye candy.

---

### Post by thatguruguy on 2012-06-19
Have you considered asking this question on the Linux Mint forum?

---

### Post by mpiter on 2012-06-28
@noob.bot76: As thatguruguy pointed out, you are not on the right forum to get help for Linux Mint.  Anyway, check this page [http://community.linuxmint.com/tutorial/view/919]("http://community.linuxmint.com/tutorial/view/919").  This is a nice tutorial to install Compiz on Linux Mint 13.

@Skara Brae: If you still want to install Compiz, start with the same tutorial.  However, it might be possible that the current Nvidia driver 195.40 cannot handle your graphic card GE Force 6600.  A bug was introduced in that Nvidia driver that freezes randomly old graphic cards when composite is used.  If this is the case for you, you might try to install a more recent Nvidia driver such as version 195.49 (google to find out how to do it).  If that does not solve your problem, you might try to install the old 173 Nvidia driver that properly handle the GE Force 6600 series.  The problem you will meet if you try is that Xorg API has changed since the 173 Nvidia driver.  So that driver cannot be installed with today Xorg, Xorg has to be downgraded.  Everything is explained here [http://forums.linuxmint.com/viewtopic.php?f=42&t=102602&p=581957&hilit=geforce+8400#p581957]("http://forums.linuxmint.com/viewtopic.php?f=42&t=102602&p=581957&hilit=geforce+8400#p581957").

---

