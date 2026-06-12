---
title: "assistive technology feature?"
date: 2008-06-25
forum: Assistive Technology &amp; Accessibility
---

### Post by witwolf on 2008-06-25
Sorry totally new here.. I tried to use the accessibility features, so far I only got the ORCA to work but not the magnifier.  I can't seem to find where the on-screen keyboard also.  Can someone show me how.  Thanks

---

### Post by witwolf on 2008-06-25
Also I have no idea what Oxa means.  I like shortcuts, but the keyboard shortcuts is hard to understand.

---

### Post by Sef on 2008-06-25
Moved to Assistive Technology forum.

---

### Post by RCC2k7 on 2008-06-27
In order for the magnifier to work in Orca, you need to disable Desktop Effects. Press ALT+F1 for the menus, go to System, Preferences, Appearance. Go to the last tab in that dialog and select the None radio button.

After this, you should be able to enable the magnifier in Orca. Press Insert+Space to bring up the Orca UI preferences window. Go to the Magnifier tab and check Enable Magnifier.

---

### Post by witwolf on 2008-06-30
thanks... the Magnifier works with orca.  However I get dizzy after a bit of using the magnifier.  I change the prefences for the arrow to be centered so it helped a bit.  But I still find it strange that I can't just activate the magnifier without the orca.

---

### Post by witwolf on 2008-07-01
I still can't use the magnifier by itself without the screen reader.  Do you know how to just turn on the magnifier?

---

### Post by Declan Moriarty on 2008-07-17
To stop speech you need to get orca preferences up.  Go to the speech tab and uncheck Enable Speech.  Press OK and the speech should stop.  Another tip.  You can quit the magnifier by pressing the quit button next to the preferences button.  To restart the magnifier you can get a terminal up and type the command

```

orca &

```

---

### Post by RCC2k7 on 2008-07-17
> **witwolf said:**
> I still can't use the magnifier by itself without the screen reader.  Do you know how to just turn on the magnifier?

Press ALT+F2 for the Run Command.
Type **orca -d speech** and press Enter.
If this works, you can create a Desktop launcher with this command.

---

