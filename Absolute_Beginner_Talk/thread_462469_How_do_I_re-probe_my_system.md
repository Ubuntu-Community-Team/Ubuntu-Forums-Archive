---
title: "How do I re-probe my system?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by ericdegen on 2007-06-02
Ok Newbie question here.

I have been running Feisty on my notebook for about a month now, all is going well.  Then I moved my HD to a new notebook, same model an HP NC8430, the new one has more RAM and a faster Core 2 Duo, but all the other components are the same (video, audio, etc.)

But it appears that I have no network, wired or wireless. not sure if this is due to the mac being different or not. As far as I know the drivers are the same (same Intel chips as the old model.) 

Is there some command I can issue from the command line to just redetect my components? I've seen a few posts about "modprobe" but I am unfamiliar with it's usage, and would like to just issue a blanket reprobe?

Any help would be great, thanks!

---

### Post by Inxsible on 2007-06-02
If you plug back the HD in the old laptop, does it still work ?
if so you might wanna do a 
```
lspci
``` on both machines and compare whether all the hardware is actually the same.
post the contents of it here and mebbe someone might be able to help you further

---

### Post by ericdegen on 2007-06-02
Reconfirmed that both HP NC8430s have the same Broadcom gigabit nic and Intel 3495 (or something like that) wireless.  I am just trying to get the wired connection working at this time.

Good idea Inxsible to swap the drives back, that will be my next step. 

Anyone else know of a simple way to re-detect a nic?

---

### Post by Inxsible on 2007-06-02
why dont you open a terminal and start the nm-applet
```
nm-applet
``` ---i think :?

---

### Post by ericdegen on 2007-06-02
I've been booting to a text console, as it takes Gnome about 5 minutes just to get to the login screen, and then about another 5 minutes to populate the panels, and then another 5 minutes to give me a Gnome error, you get the idea...  The system is so unresponsive when I bring up the GUI.

---

### Post by ericdegen on 2007-06-02
Ok I can confirm that putting the drive back in the original notebook results in  everything booting fine, so there is something about the new one that does not like. 

Can anyone help with some other trouble shooting I should be doing here?

---

### Post by Inxsible on 2007-06-03
Do you have any other drives in the new machine ?

If yes, that might be a problem since, the device names may conflict and therefore you might not be able to load ubuntu correctly

---

### Post by ericdegen on 2007-06-03
Nope, no difference on drives, the one I am moving actually has two partitions one is XP and the other Feisty.

The XP side boots flawlessly in both notebooks, all the drivers are happy, another confirmation that there is something in the Linux config that is reginzing some difference.

That's why I was leaning toward the NIC, as it has a different H/W MAC. I tired googling for something about that , but none of the post I've tried thus far have had any effect.  About to call it a night and look at it the AM.

I really don't want to reload the whole system over this.

---

### Post by ericdegen on 2007-06-03
still looking for a suggestion, thanks

---

### Post by ericdegen on 2007-06-03
So a chap over in IRC was able to help with my NIC IP problems.

 sudo dpkg--configure -a

got my nic backonline.  But Now Gnome is still taking 5 minutes plus just to login... that the heck is going on?

---

