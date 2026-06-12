---
title: "Question about my MX510 mouse"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by MrPaez on 2008-03-31
I have a MX510 and I was wondering how I could go about getting the the two side buttons work. When I lookup the mouse settings under: System->Preferences->Mouse I don't see anything about setting up the buttons. Specifically in using Firefox browsing and through the file system I would like to be able to use the side buttons to go back and forward. 

Any help would be appreciated.

P.S.

I have tried "/etc/X11/xorg.conf" but I am getting denied access. Am I missing something?

---

### Post by Michael.Godawski on 2008-03-31
To edit the xorg.conf file you must have superuser privileges. To get them run in terminal:

```
gksudo gedit /etc/X11/xorg.conf
```

5 button mouse issues are not my strong side though.

---

### Post by MrPaez on 2008-03-31
Mr. Godawski,

I appreciate your help even though the 5 buttons aren't your forte. Thanks to you I am at least in xorg.conf

I will let you know how I make out.

---

### Post by MrPaez on 2008-03-31
Um I edited the xorg.conf and rebooted. Afterwards I rebooted and everything was very odd looking. Once I put in my creds Everything was out of whack (wrong resolution, compiz kept disappearing) i then got notification that the was an issue with my x1250 graphics card. I select the flgrx video drivers and restart. Afterwards I have no video. 

I dun effed it up!:lolflag:

---

### Post by 1875 on 2008-03-31
> **MrPaez said:**
> Um I edited the xorg.conf and rebooted. Afterwards I rebooted and everything was very odd looking. Once I put in my creds Everything was out of whack (wrong resolution, compiz kept disappearing) i then got notification that the was an issue with my x1250 graphics card. I select the flgrx video drivers and restart. Afterwards I have no video. 

I dun effed it up!:lolflag:

You did make a backup of xorg.conf ? Say yes.

---

### Post by MrPaez on 2008-03-31
I really, really wish I could say yes to that Mr1875 but alas being a noob I didn't realize that the xorg.conf is like the registry for windows and that whenever working on it you should always back it up,

I am in recovery mode and I am following instructions from this page: [http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/](http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/) 

I am gonna try loading xorg.conf.failsafe

---

