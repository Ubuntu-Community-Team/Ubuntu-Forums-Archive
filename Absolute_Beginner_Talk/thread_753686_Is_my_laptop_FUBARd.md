---
title: "Is my laptop FUBARd?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Aphox on 2008-04-13
I recently got an old laptop from my mom because Windows was killing it, so I put Ubuntu 7.10 on it and it works perfectly... Until now.

I was fiddling around, trying to get GTK to work so I could switch my theme (can anyone help me with that too?) and now everything is ... Well, EVERYTHING looks like [] boxes. The text, I mean. I have some pictures of the screen... Thing wont connect to the internet or even open firefox.

[img]http://i25.tinypic.com/ycewk.jpg[/img]
[img]http://i25.tinypic.com/35m16kx.jpg[/img]
[img]http://i30.tinypic.com/a27yj9.jpg[/img]

Can anyone help me with this? I can't navigate and I can't connect to the internet or do anything... Could really use some help.

---

### Post by Gen2ly on 2008-04-13
help sure.  

yikes!  looks like gtk theme got set to an unreadable font.  Gtk theme properties are set in either ~/.themes, in ./gconf, or in ~/.gnome2.  Rename these, trying the foremost first and see if the settings nreset.

This looks like the computer won't be able to use gnome-terminal so try entering console (usually ctrl-alt-F2) Consoles go from F2 to F6.

---

### Post by Aphox on 2008-04-13
I'm in the terminal but I have no clue what to do.

---

### Post by Aphox on 2008-04-13
Oh, and the letters on the normal terminal show up. Just everything else is boxes. It's really screwy.

---

### Post by PilotJLR on 2008-04-13
It may be helpful if you describe what was wrong with the previous Windows installation.

I ask because problems like this don't happen without some root cause... if, for example, a bad hard disk is causing data corruption, then that could explain what you are experiencing.

---

### Post by russo.mic on 2008-04-13
I've for the hell of it done a sudo rm -r / (NOBODY DO THIS) before a reinstall to see what happens, and that's what happens.  My first guess is some kind of harddrive failure.  If that's the case, see if you can mount the drive via knoppix or something and take a look at the filesystem.

My vote, your hosed.  Could be wrong though!  GOOD LUCK!

Russo

---

### Post by Aphox on 2008-04-13
It was having harddrive errors X______X

---

### Post by Tews on 2008-04-13
If you dont have a lot of data that you need to save, I'd just go ahead and do a reinstall.  IMO it would be a lot simpler than looking for conf files to edit.... Just my opinion..

PS... be sure to defrag that hard drive!

---

### Post by Gen2ly on 2008-04-13
geeesh, no... completely unnecessary I hope.  Let's try and fix the problem before predicting the destruction of the world.  If gnome-terminal is working good.  Let's use it.  Get to the home directory by:

```
cd ~
```

and rename the theme directory:

```
mv .themes .themes.backup
```

logout and login and hopefully the fonts will be back.  if they aren't try again with the other folders I mentioned above.

---

### Post by PilotJLR on 2008-04-13
If there was data corruption / disk failure with both Windows and Ubuntu, then band aid fixes won't help you long term.
Might want to buy a new hard disk now, and swap it out while you can still recover some / most of your data!

---

### Post by Fate Reconciled on 2008-04-13
Also, look into RAID 1/5 backup as these are two of the best methods out there.

---

### Post by spydon on 2008-04-13
I think something went wrong when you were tweaking the gtk themes and like Dirk.R.Gently said just move the files and new default files will be created. If it is a harddrive error like badblocks or something I really recommend buying a new one. You can check if you have badblocks from a live cd by ```
sudo badblocks /dev/sda
``` or something like that. It will take a while to complete it.

---

### Post by kerry_s on 2008-04-13
if it is a bad hd, make sure you have a copy of dsl or puppy, you can run those in ram till you get a new drive. dsl saved 1 old comp i had, the hd went, wasn't worth buying a new one, ran dsl in ram for 6 months, just left it on, then the rest of the computer finally went, but i knew the motherboard was going, so no big loss.

---

### Post by spydon on 2008-04-13
> **kerry_s said:**
> if it is a bad hd, make sure you have a copy of dsl or puppy, you can run those in ram till you get a new drive. dsl saved 1 old comp i had, the hd went, wasn't worth buying a new one, ran dsl in ram for 6 months, just left it on, then the rest of the computer finally went, but i knew the motherboard was going, so no big loss.

All live cd's run in RAM...

---

### Post by kerry_s on 2008-04-13
> **spydon said:**
> All live cd's run in RAM...

no i mean to ram, you can remove the cd and use the drive.

---

