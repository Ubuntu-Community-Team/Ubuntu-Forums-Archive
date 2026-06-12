---
title: "Crash on startup compiz/beryl related"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-04-05
My ssystem was working fine with edgy & beryl

But.

My screen is locking up when the desktop loads. I know why, its because i selected compiz from the beryl manager menu to see what it did. It froze my screen with the mouse wait wheel spinning forever.

I made the mistake of adding beryl manager to the session's startup list before i tried this and now I cannot boot into gnome as it crashes just before i have enough time to switch it off.

Please could someone tell me how to remove the beryl manager from my sessions list using terminal?

(or tell me if im barking up the wrong tree :)

---

### Post by dbbolton on 2007-04-05
did you try logging in to a failsafe gnome session ?

---

### Post by tonyr1988 on 2007-04-05
When you get to a console:

> cd ~/.config/autostart
ls

You should see some *.desktop files. There should be one called beryl-manager.desktop.

> rm beryl-manager.desktop

will remove it. However, if you just want to disable it from auto-starting (if you think you may want to enable it again later), this *may* work (I haven't tried it):

> nano beryl-manager.desktop

Edit the last line (X-GNOME-Autostart-enabled=true) to false. If that doesn't work, deleting the file should.

---

### Post by dgrafix on 2007-04-05
Fixed it, in the end i used:

cp /usr/bin/compiz /usr/bin/compiz.backup

then rebooted.

Now its gone of beryl's list of renderers, never to be used again :)

---

### Post by Mr. Nefarius on 2007-04-06
many thanx to **[COLOR="Red"]tonyr1988[/COLOR]**:KS 

i had a very similar issue w/beryl (i enabled a critical param on the *advanced settings menu* which locked up my gnome session as soon as the beryl-manager loaded).

-i disabled it from the console prior to startup
-logged in to gnome
-reset my NVIDIA server settings
-reset beryl's incorrect setting
-logged out of gnome
-enabled the beryl-manager
-gnome started up just as before

:guitar:

---

