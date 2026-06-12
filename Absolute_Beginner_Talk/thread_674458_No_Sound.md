---
title: "No Sound"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by jbmswow on 2008-01-21
After I install Ubuntu I get sound the first 2 or 3 times I bring the system up.  The next time and thereafter -- No Sound  Help would be appreciated.

---

### Post by zipperback on 2008-01-21
> **jbmswow said:**
> After I install Ubuntu I get sound the first 2 or 3 times I bring the system up.  The next time and thereafter -- No Sound  Help would be appreciated.


Did you start losing sound after a system update or after you installed something by any chance?

- zipperback
:popcorn:

---

### Post by thelatinist on 2008-01-21
Did you install any software or make any other system changes in the interim?  What kind of audio adapter do you have?

---

### Post by jbmswow on 2008-01-21
I essentially made no changes

---

### Post by Redptc on 2008-01-21
I have a similar problem in that the sound volume control does not come on when System is booted. I often have to go to the 'Master' volume control icon, right click to>Open Volume Control....then I have to adjust the first two buttons....Master and PCM.....this activity usually fires up my sound to full volume!

It would be nice if I didn't have to do this but it seems to happen frequently. I spend most of my computer time not needing sound but it should be there. I am content that I can bring it to life when needed.

I am not trying to hijack your thread but rather offering a suggestion that worked, at least partially, for me. Lotsa luck!:)

---

### Post by thelatinist on 2008-01-21
> **jbmswow said:**
> I essentially made no changes

That didn't really answer the question.  What changes _did_ you make, and what make and model is your audio adapter?

---

### Post by jbmswow on 2008-01-22
I have made no changes.  I have a PCI card that overrides my on board sound.  I'm running an intel pentium D 930 chip on a D945GNTL board.  That's for info purposes.   --  The last time I turned ths system off and restarted it it took 4 starts to get the system to come up  - Strange- and when it did I had sound.  I have found that Ubuntu does something different every time I boot up.  I'm thinking it might be the chip and board I'm running.????!!!!

---

### Post by thelatinist on 2008-01-22
> **jbmswow said:**
> I have made no changes.  I have a PCI card that overrides my on board sound.  I'm running an intel pentium D 930 chip on a D945GNTL board.  That's for info purposes.   --  The last time I turned ths system off and restarted it it took 4 starts to get the system to come up  - Strange- and when it did I had sound.  I have found that Ubuntu does something different every time I boot up.  I'm thinking it might be the chip and board I'm running.????!!!!

Okay, so you have a PCI card.  That's something.  But you still haven't told us what brand and model or chipset it is.  How about this: post the output of:

```
lspci | grep -i audio
```

If this doesn't show the details of your card, post the entire results of

```
lspci
```

---

### Post by jbmswow on 2008-01-22
the output from your suggested entry is

04:00.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
04:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
04:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


Jerry

---

### Post by thelatinist on 2008-01-22
> **jbmswow said:**
> the output from your suggested entry is

04:00.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
04:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
04:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


Jerry

Is this the complete output of lspci?  I wouldn't expect the first and third lines if it were lspci | grep -i audio, and I would expect much more if it were the complete output (PCI bridges, graphic cards, etc.).  Also, only one adapter is showing up, which is not how you described your system.  If only one adapter is being detected (especially if it's only intermittent) that might go a little way toward explaining your problem.

The adapter that is showing up is a fairly cheap C-Media adapter, which I suspect is the built-in sound from your motherboard (ASUS, by any chance?).  In any case, I've got that same chipset, and it works just fine with a default installation, so I doubt that's the problem

Please double-check **lspci** and post the complete results here.

---

