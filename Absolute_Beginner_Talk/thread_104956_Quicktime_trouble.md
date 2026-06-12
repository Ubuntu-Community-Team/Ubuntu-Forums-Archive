---
title: "Quicktime trouble"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by Minyaliel on 2005-12-17
I've done all the instructions in the restricted formats page in the wiki, but I still can't view embedded quicktime movies in FF. Help...

---

### Post by aysiu on 2005-12-17
[QUOTE=Minyaliel]I still can't view embedded quicktime movies in FF.[/QUOTE] Can you be more specific? When you try to view the embedded Quicktime movies, what happens?

---

### Post by Minyaliel on 2005-12-17
Nothing, it just displays a black square where the movie should be, with a <no image> thing displayed inside.

---

### Post by aysiu on 2005-12-17
Do you know if you're trying to use a Totem plug-in or an Mplayer plug-in to play it? Are you using Firefox 1.5 or 1.0.7?

---

### Post by Minyaliel on 2005-12-17
I use the totem plug- in. As for which FF... the one that comes default with breezy? Honestly, I've got no idea :P

---

### Post by aysiu on 2005-12-17
You might want to try the mplayer plugin instead.
See the first link of my sig and this one: [http://www.ubuntuguide.org/#mplayer](http://www.ubuntuguide.org/#mplayer)

---

### Post by Minyaliel on 2005-12-17
lol you've got no links in your sig... but I'll check the other one ;)

Edit: still nothing.

---

### Post by aysiu on 2005-12-17
> **Minyaliel]lol you've got no links in your sig... but I'll check the other one  said:**
>  Actually, I do--they just made it so that the link shows up only once per page. See my first post in this thread. If you were able to do the other link, you don't need the link in my sig, though.

[quote]
Edit: still nothing. Try this: Close Firefox. Then, ```
Alt-F2
``` ```
gksudo nautilus
``` Go to /usr/lib/mozilla-firefox/plugins and delete everything with the word "totem" in it. Open Firefox again.

---

### Post by Minyaliel on 2005-12-17
It says I don't have access to delete them. I tried logging in as the superuser (I can in the terminal, so I figured I might just aswell try it from the log- in screen) but it wouldn't let me, so the files are still on my puter.

---

### Post by aysiu on 2005-12-17
You have to do Alt-F2 and ```
gksudo nautilus
``` before going to /usr/lib/mozilla-firefox/plugins.

Do not just go to /usr/lib/mozilla-firefox/plugins as you normally would.

If you prefer to do it through the terminal, type this command ```
sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla* ~/.Trash
```

---

### Post by Minyaliel on 2005-12-17
*sigh* still nothing. I tried it through the terminal, and well...

minyaliel@minyaliel:~$ sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla* ~/.Trash
Password:
minyaliel@minyaliel:~$

so nothing really happened...

---

### Post by aysiu on 2005-12-17
[QUOTE=Minyaliel]*sigh* still nothing. I tried it through the terminal, and well...

minyaliel@minyaliel:~$ sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla* ~/.Trash
Password:
minyaliel@minyaliel:~$

so nothing really happened...[/QUOTE] Actually, something really happened. The Totem plugins moved to the trash. So launch up Firefox again. Any luck? For more details, check [this HowTo](http://ubuntuforums.org/showthread.php?t=76946) out.

---

### Post by Minyaliel on 2005-12-18
Well, it still won't play quicktime movies, I've tried it on several sites now. Anyway, thanks for your help, I'll have a look at that howto.

---

### Post by aysiu on 2005-12-18
[QUOTE=Minyaliel]Well, it still won't play quicktime movies, I've tried it on several sites now. Anyway, thanks for your help, I'll have a look at that howto.[/QUOTE] Did you install the w32codecs package?

---

