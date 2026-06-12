---
title: "Seemingly random crashes. HELP!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by iNoob.x on 2007-06-07
First time playing with Ubuntu (and linux in general). Been using it for 2 days now and lovin' it.

Today I started noticing what seem to be random crashes. I would be reading tomshardware in firefox and when i try to move the mouse i realized the computer has frozen. I would search something in google, press enter to submit my search and the computer would freeze. Once it froze at the login screen after I submitted my password (I'm sure I didn't type it wrong).  It crashed a few other times too, but there doesn't seem to be a pattern associated with the crashes. Any help please?

See my signature for specs.

---

### Post by benanzo on 2007-06-07
It really could be anything.  I would start by looking through your system logs for errors.
**System -> Administration -> System Log**.

You will want to look in **messages** or **kern.log** or**syslog**.  The problem should show up in one of those.  It is most likely something like your ethernet driver or some motherboard component driver.

---

### Post by w4ett on 2007-06-07
Are you running the 32 bit or 64 bit versions?  Also, how much overclocking have you done?...not saying it's an issue...just a consideration.

---

