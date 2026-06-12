---
title: "How to make terminal show what's under it? (transparency)"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-07-11
Just wondering, how do I get the effect where a terminal is anchored to one side of the screen, with no border, and completely transparent? I've seen some screenshots, but I'm not sure how to replicate it. I have tilda- but that has a border, and i'm not sure if that can be removed, but in addition, when I set it to transparency it shows my wallpaper wherever it is- not whatever happens to be behind it (icons, windows, etc), so how do I do that?

---

### Post by forestpixie on 2007-07-11
open terminal - edit profiles/ curent profile - effects - transparent

Edit:just woken up - didn't read whole post :oops:

---

### Post by Circus-Killer on 2007-07-11
okay, unfortunetly i'm sitting at work, in front of a vista machine, so i cant look for verification. however, somewhere in your console window, in the menu section, i think under the "Edit" menu, you can choose to edit the Current Profile. 

Once you select that, you will get a dialog box that has different tabs such as "Colors" and "Effects". Now I know that you can make the console transparent under the effects section. As for the rest of what you want to accomplish, I'm not too sure. I reckon if you play around in the Profile settings some you will find what you are looking for.

---

### Post by kvonb on 2007-07-11
I think you right click on the tilda window when it's dropped down to get to it's settings.

As for true transparency, you need to use "Desktop Effects", or "Beryl".  BUT for those to work you will need a supported 3d capable video card, ie Nvidia > TNT2, ATI, Intel.  Not sure about others.

Search for "beryl" on the forums, or better still, look on your system menu under preferences, and run "hardware information", somewhere in there you will see your video card type, search the forum and/or the net for that model and see what pops up :).

---

### Post by bodhi.zazen on 2007-07-11
> **Feba said:**
> Just wondering, how do I get the effect where a terminal is anchored to one side of the screen, with no border, and completely transparent? I've seen some screenshots, but I'm not sure how to replicate it. I have tilda- but that has a border, and i'm not sure if that can be removed, but in addition, when I set it to transparency it shows my wallpaper wherever it is- not whatever happens to be behind it (icons, windows, etc), so how do I do that?

Tilda will do it, look in the configuration ...

The effect you are (and forestpixie) are describing is called 'pseudotransparency'

What you want is true transparency. For that you need beryl or compiz.

---

### Post by jordanmthomas on 2007-07-11
You may want to try Eterm as well.  Run Eterm like this:
```
 Eterm -f white -n DeskTerm -O -x --buttonbar false --scrollbar false
```
and you'll get what I have in this screenshot (on the right)

Ignore my dropshadow, that's just compiz.  If you're not running it you won't have a shadow around the border.

Have fun!

---

### Post by Feba on 2007-07-11
Alright, I've got compiz on, and still, how do I do this?

well the regular terminal seems to work fine, tilda however still doesn't. I have to install eterm before I can try that

EDIT: OK, this works with the regular terminal, but not tilda or eterm, which would be preferable since those are actually anchored and sans borders.

---

### Post by jordanmthomas on 2007-07-11
Why doesn't tilda work?

Edit:  Oops, didn't see your edit

---

### Post by Nythain on 2007-07-11
> **bodhi.zazen said:**
> Tilda will do it, look in the configuration ...

The effect you are (and forestpixie) are describing is called 'pseudotransparency'

What you want is true transparency. For that you need beryl or compiz.
or xcompmgr and transset :)

---

