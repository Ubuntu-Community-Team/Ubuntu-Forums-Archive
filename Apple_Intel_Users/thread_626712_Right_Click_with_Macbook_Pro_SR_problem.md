---
title: "Right Click with Macbook Pro SR problem"
date: 2007-11-29
forum: Apple Intel Users
---

### Post by neatokino on 2007-11-29
I've got the newest model Macbook Pro Santa Rosa 15" and Ubuntu Gutsy.  I've never been able to get a right-click without using an external mouse.  

I tried modding Xorg.config with gedit to change the trackpad settings per the MBP SR wiki, but none of the changes I make seem to be implemented;  I have not been able to figure out why those settings won't change (something else must be overriding the Xorg.config settings, but I can't for the life of me find out whats getting in the way).  I've given up on that.

I'd be reasonably satisfied with the current 'out of the box' functionality of the trackpad if I could just get a right click somehow or other.

Any suggestions?

---

### Post by ditsch on 2007-11-29
Here is a sample configuration which works on my MBP: [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
Please note you need sudo rights to edit the xorg.conf and you need to restart XServer in order to activate the changes.

---

### Post by cyberdork33 on 2007-11-29
> **ditsch said:**
> Here is a sample configuration which works on my MBP: [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
Please note you need sudo rights to edit the xorg.conf and you need to restart XServer in order to activate the changes.

He just said he followed the instructions in the wiki and they didn't work...

---

### Post by neatokino on 2007-11-29
That's correct... the instructions in the wiki do nothing at all.  I'm completely baffled as to why the changes to Xorg.conf don't have any effect on my trackpad's behavior.

I'm still hoping someone has a suggestion on how to make the trackpad work.  My Santa Rosa MBP is the latest model, by the way.  2.2 GHZ Intel Core 2 Duo, and I have 4 GB of ram (though only 3 are recognized in Linux).

Somebody here must have success in making one of these things work, right??????

---

### Post by derald on 2008-04-02
I trialed and errored a solution - 
hold fn + ctrl then press the f10 button. Your cursor must already be positioned. After the right-click menu is up you can generally use the cursor keys to navigate within the menu. 

This solution works on my MacBook Pro with Ubuntu.

Luck

---

