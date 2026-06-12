---
title: "UK digital freeview TV cards to use with MythTV"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by feistyfirsttimer on 2007-08-22
I'm hoping that someone who is successfully using MythTV, for instance, to watch digital Freeview television in the UK, can tell me what the best digital freeview TV cards compatible with Ubuntu are.  Or maybe not a MythTV user, but someone who's using a card or USB TV stick to successfully watch the freeview programmes on their PC.  What *is* the best card/stick/whatever to use?  That's compatible with Ubuntu, of course.  And is perhaps not too expensive?  Can anyone help me out with some advice here?  Remember, I'm asking about devices that are compatible with the **UK DIGITAL FREEVIEW SYSTEM**.

---

### Post by chrome307 on 2007-08-23
The [COLOR="Red"]KWorld DVB-T 100[/COLOR] works in Feisty with one small tweak. The LinuxTV DVB kernel drivers don't load automatically in the 2.6.20 kernel used by Feisty, so you need to add "cx88-dvb" to /etc/modules and reboot. No changes are necessary if using the card in Edgy.

---

