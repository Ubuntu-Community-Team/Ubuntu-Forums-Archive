---
title: "[SOLVED] Places menu not working in Gutsy"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by st0nes on 2007-10-21
Hi all,

I have just upgraded to Gutsy.  When I tried to access my home folder from the "Places" menu, nothing happened.  I checked in ~/.config/menus and the places.menu file is missing.  It is also missing from /etc/xdg/menus.  Any ideas on how I can restore the files?

---

### Post by Beggar on 2007-10-21
Interesting, don't think Ive ever seen that, more or less a shot in the dark, but what about ```
sudo dpkg-reconfigure gnome-menus
```

---

### Post by st0nes on 2007-10-21
Thanks beggar, but that didn't work.

---

### Post by Beggar on 2007-10-21
From a partially related issue, [http://ubuntuforums.org/showthread.php?t=572961&page=2](http://ubuntuforums.org/showthread.php?t=572961&page=2), it seems that if you delete your .gnome*, .gconf* and .config* folder they should get generated automagically on startup. might be worth a try. Although admittadly, I dont know every effect that could have on your system.

---

### Post by st0nes on 2007-10-21
Thanks Beggar.  I did as you suggested, after backing up ~/.gconf and ~/.config I deleted the directories and restarted.  As promised, the directories were recreated on start up and all the menus worked.  Unfortunately, the nauseating Gutsy wallpaper and window borders replaced my (far more tasteful) custom setup.  I copied all the backed up files and sub-directories except the "Menus" directory back into .config and now everything is as it should be.  Incidentally, it was not necessary to delete the .gconfig file at all; it wasn't modified on restart.

Thanks again for the help; I can mark this one as resolved.

---

### Post by Beggar on 2007-10-21
Awesome, good call on mentioning backing those directories up, you seemed like a smart enough user that I didnt need to give specific directions, but if someone with less experience read the thread they might not have thought of that. Guess I should take my own advice about making threads reusable...

---

### Post by Noncyc on 2008-01-19
I'm a total noob to Ubuntu, and Linux in general, but am really liking Ubuntu.

I've got the same problem with my places menu, and understand the concept of removig the folders and having the OS recreate them - but I don't know how to do it.

Could someone provide some absolute base level step by step instructions?

---

### Post by doorknob60 on 2008-01-19
Open your home folder (if you can't get to it from the menu press Alt-F2 and type nautilus) and then press Ctrl+H and you should be able to see the hidden files and then do what beggar said and delete the .gnome .gconf and .config folders by just right clicking and pressing delete. I'd back them up to your desktop or something first though.

---

### Post by Noncyc on 2008-01-19
Thanks doorknob60, however, after pressing Alt+F2, typing nautilus and clicking the Run button - nothing happens!

---

### Post by doorknob60 on 2008-01-19
Try opening a terminal and typing nautilus then, I have no clue why it didn't open though.

---

### Post by Noncyc on 2008-01-19
Again, nothing!

Although I did notice that when I tried to run nautilus from Run, if all other apps (Firefox) were minimized (ie, showing desktop), then an application frame appeared then dissappeared...

I'm going to reboot and try nautilus again.

---

### Post by Noncyc on 2008-01-19
OK, on restart, I got the following error message, and all of my Appearance customizations have been reset to the defaults.

The Places menu is working again!

Obviously, there's an issues with customized Appearances.

Here's the error message:

[INDENT][COLOR="Blue"]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-tjUCIwmaZd: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.[/COLOR][/INDENT]

---

### Post by doorknob60 on 2008-01-19
Hmm that happens to me every once in a while and restarting fixes it and I have no problems after that.

---

