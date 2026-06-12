---
title: "Help with beryl/Emerald Theme Manager"
date: 2007-01-22
forum: Art &amp; Design
---

### Post by mattmagician on 2007-01-22
ok, so i have a few themes now, how do i use them? lol.
please keep in mind i'm brand new with edgy, but know a tad about Dapper, so its not like this is my first Ubuntu experiance. thanks!!

---

### Post by mand0 on 2007-01-22
open up the emerald theme manager (right click the beryl icon then go to emerald theme manager) and look around for a place to import your own themes.  I am not at my own computer right now so I cannot tell you specifics

---

### Post by mattmagician on 2007-01-22
ok, i imported (there wasnt a beryl icon, its in my system>prefrences.) and i still can find how to use them...

---

### Post by CowzRule on 2007-01-22
What exactly did you download?

---

### Post by _simon_ on 2007-01-22
Once you import them you should see them appear in the theme manager, all you do then is select the one you want and it should take effect.

Note: It will ONLY take affect if Beryl is set as your current window manager.

You say you haven't got the beryl icon, open terminal and type

```

beryl-manager

```

That should load it for you... if not what happens?

If it loads then right click on it and choose Select Window Manager and make sure Beryl is the option selected.

---

### Post by mattmagician on 2007-01-22
ok, i'll try that as soon as i get this working, but...
now whenever i try to log in, excepth through terminal, it says BERYL, then goes to a black screen, then back to my login screen. please help, i need it desperatly.

---

### Post by walter_j on 2007-12-25
[QUOTE=_simon_;2048815]Once you import them you should see them appear in the theme manager, all you do then is select the one you want and it should take effect.

Note: It will ONLY take affect if Beryl is set as your current window manager.

You say you haven't got the beryl icon, open terminal and type

```

beryl-manager

```

That should load it for you... if not what happens?

If it loads then right click on it and choose Select Window Manager and make sure Beryl is the option selected.[/QUOT

When i did the above, I lost window borders, and the minimize, maximize and close buttons on the windows. Im running kubuntu 7.10. The theme i selected in emerald did not take effect.

---

### Post by war59312 on 2008-01-05
I prefer not to use beryl-manager but instead I use CompizConfig Settings Manager:

[http://packages.ubuntu.com/gutsy/source/compizconfig-settings-manager](http://packages.ubuntu.com/gutsy/source/compizconfig-settings-manager)

Or install from synaptic manager...

Then open it via System > Preferences > Advanced Desktop Effects Settings.

Next set a filter of Window and then click on Window Decoration, enable it by checking the box to the left and then add for command: emerald --replace .

Then run Emerald Theme Manager and pick your theme. All done. :D

---

### Post by MarimaX on 2008-01-09
You know I am somewhat new to linux...however I know my way around (ex PC slave)...I can't find where to change manager...I typed (beryl-manager) in Terminal but it gave me the bash error.  I am trying to get the Emerald theme manager to work...but it will not change anything when I try to use it.

---

### Post by MarimaX on 2008-01-09
I forgot to add that I do have the CompizConfig Settings Manager installed...if that helps any.

---

### Post by smartboyathome on 2008-01-09
No, since you are on Gutsy, you don't need Beryl. Compiz Fusion (which is what is included with Gutsy) is a fusion of Beryl and Compiz, so in other words Beryl and Compiz are both obsolete.

---

### Post by DaCeige on 2008-05-20
> **war59312 said:**
> I prefer not to use beryl-manager but instead I use CompizConfig Settings Manager:

[http://packages.ubuntu.com/gutsy/source/compizconfig-settings-manager](http://packages.ubuntu.com/gutsy/source/compizconfig-settings-manager)

Or install from synaptic manager...

Then open it via System > Preferences > Advanced Desktop Effects Settings.

Next set a filter of Window and then click on Window Decoration, enable it by checking the box to the left and then add for command: emerald --replace .

Then run Emerald Theme Manager and pick your theme. All done. :D

Worked like a champ.  Thanks!

Is this the preferred theme'r for Compiz Desktop Effects?

---

### Post by war59312 on 2008-05-20
Yes, seems most use it. I just installed again in Ubuntu 8.04 and still running wonderfully. :)

---

### Post by Earthen on 2008-11-02
typing "emerald --replace" in the terminal seems to have done the trick for me.

---

### Post by sharkbite1414 on 2009-01-27
This worked for me as well!

> **Earthen said:**
> typing "emerald --replace" in the terminal seems to have done the trick for me.

---

### Post by davidcyber00 on 2009-10-25
emerald --replace

---

### Post by davidcyber00 on 2009-10-25
hello i have been reading teese convos and have fallowed all stept but everytime i type in "beryl-manager" into my terminal it says "bash: beryl-manager: command not found"
could anyone please help me out

---

### Post by littlemisscrazy on 2009-12-02
but if you close the terminal it returns to the old theme- what can i do to change the theme constantly? thanks

ok sorry- adding emerald --replace to the startup applications BUT now the envelope icon for evolution and pidgin is missing in my panel...
what can i do?

---

### Post by sharkbite1414 on 2009-12-03
Take a look at this thread

[http://ubuntuforums.org/showthread.php?t=860527]("http://ubuntuforums.org/showthread.php?t=860527")

---

