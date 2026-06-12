---
title: "Gnome Dock questions"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-09-30
I've just installed gnome dock (cairo dock) and I was wondering about some things...

1.  How do I remove shortcuts from it
2. How do I add shortcuts to it
3. How do I add icons to those shortcuts
4. How do I make it so that it dosn't close when I close terminal
5. How do I get it to run on startup

Thanks fr any help.

---

### Post by Ludford on 2007-09-30
any ideas?

---

### Post by JBAlaska on 2007-09-30
You right click on a launcher icon to modify or remove it, to add one just drag it into the dock.

Don't launch it from terminal, do alt-F2 and launch it from there.

To change the icon of a launcher (shortcut) right click on it and select modify, then add your icon name to "images name or path"

To run on startup, add a entry to gnome sessions.

If you want the config screens in english and it's not, right click and do a update, restart and it should be in english (happened a couple of updates ago..sweet)

---

### Post by Ludford on 2007-09-30
Cheers, What command should I use in alt + f2, I tried the command from the tutorial, 

./cairo-dock --no-glitz

but it didn't work.

Also right clicking does nothing for some reason.

---

### Post by JBAlaska on 2007-09-30
cairo-dock

I'm not sure why right clicking on the dock does not work for you, What build do you have and where did you get it.

---

### Post by Ludford on 2007-09-30
I followed this guide..

 [http://ubuntuforums.org/showthread.php?t=302570](http://ubuntuforums.org/showthread.php?t=302570)

And typing cairo-dock, into the run aplication window just opens

/home/matt/cairo-dock

---

### Post by JBAlaska on 2007-09-30
I just had a look at that thread, it seems that's a different version than the one I'm using.
I got mine from the developers page (version 1.3.4 is current), no need to compile, just install the deb.
[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

If you can't get yours working, you might want to un-install yours and try the above, very stable and now with English config screens (The first version I got was in French only and was a bit of a pain to configure.

To start mine, I use a panel launcher with "cairo-dock" as the command.

---

### Post by TRDownShift on 2007-10-01
heh, ^^" lets say i used the same guide he did, how would i go about uninstalling it? cus i would like to use the new one you pointed out, but i have no clue how to uninstalling, as i JUST today got the hang of compiling files for an install... i dont know how to uninstall them T.T

---

### Post by JBAlaska on 2007-10-01
The version I'm using is quite different than the one in that thread, so I didn't have a answer on how to uninstall that version.

After going through the whole thread, I came up with this;
Q: How do I uninstall it?
A: sudo dpkg --purge cairodock

I hope that works for you. I think you will be pleased with the 1.3.4 version in the link above, much more stable, easy to configure and the great update feature.

Good luck

---

### Post by TRDownShift on 2007-10-02
Thank you, it works great now.

---

