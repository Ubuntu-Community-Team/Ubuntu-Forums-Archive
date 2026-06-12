---
title: "desktop link?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by phoenix5002 on 2008-04-12
I don't know what I did, but for some reason my desktop is displaying the contents of my home folder.  If I delete something from my desktop it's deleted from my home folder and vice versa.
same goes with adding and moving things.  How can I get it back to normal?

---

### Post by wormser on 2008-04-12
Applications> Accessories> Terminal

```
gconf-editor
```Navigate to apps> nautilus> preferences and uncheck desktop_is_home_dir

---

### Post by llamakc on 2008-04-12
The easiest way to get an answer is to always provide relevant details. In this case, which Desktop Environment are you using? GNOME? KDE? Other? And which version of Ubuntu did you install?

EDIT: Wormser's post answers your question if you're using GNOME.

---

### Post by phoenix5002 on 2008-04-12
I am using GNOME.  I installed 7.10 Gutsy Gibbon, and recently upgraded to 8.04 Hardy Heron.

the only things that are available for me to edit are:

[b]computer_icon_name     <no value>
computer_icon_visible        UNCHECKED
home_icon_name           <no value>
home_icon_visible          UNCHECKED
network_icon_name         <no value>
network_icon_visible           UNCHECKED
trash_icon_name             <no value>
trash_icon_visible            UNCHECKED
volumes_visible               *CHECKED*
[/b]

thats it... nothing that seems like it would fix my problem.

---

### Post by llamakc on 2008-04-12
The correct change in gconf-editor is

/apps/nautilus/preferences and uncheck desktop_is_home_dir

---

### Post by phoenix5002 on 2008-04-12
ok so I went there and it was already unchecked.
tried checking and then unchecking again.... no go.

---

### Post by llamakc on 2008-04-12
Make sure it is unchecked and log out / log back in. If you get the same results please attach a screenshot of your desktop and also the output of this command in a terminal:

```


cd && ls


```

---

### Post by phoenix5002 on 2008-04-12
I will post a screenshot if you really need one, but I don't see how it would help.  Everything looks completely normal except I see all the same folders and files that are in my home folder, on the desktop.  The output of that command gives the same files and folders that are on the desktop.

also, the "Desktop" folder inside my home folder (or on desktop itself) has the original contents of my desktop, but I don't see it on my actual desktop.  If I change something in either home folder or desktop it changes on both.  Here is the output anyway...

```
99-hdd-spin-fix.sh  dev        Examples  Pictures  temp
Desktop             Documents  Music     Public    Templates
```

---

### Post by llamakc on 2008-04-12
Good luck. I asked you to log out and back in but you didn't say whether or not you did.

If I were you I would temporarily rename my .gconf and .gconfd folders, LOG BACK OUT AND LOG BACK IN. See if there's any change.

---

### Post by phoenix5002 on 2008-04-12
believe me, if you ask me to do something and I don't, I will say so.  So, yes I logged back in, and it didn't work I even tried a full restart.  As for modifying the those folders, I found something online mentioning to just delete them to restore you GNOME back to new.  So I did, I deleted:
.gconf
.gconfd
.gnome
.gnome2
.metacity

all the settings were set back to normal after restart, even wallpaper and power settings.  Litterally everything got reset EXCEPT my problem.  just my luck....


well, it's not too big of a deal I guess, because I was planning on doing a fresh install of Hardy Heron when it is officially released anyway, so if we can't fix this then I can wait until then.  only 12 days.

---

