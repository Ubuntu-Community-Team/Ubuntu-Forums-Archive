---
title: "AWN avant icon problem"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2008-02-07
I am having the same problem as this guy:
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=698&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=698&page=1&isLive=true)

Basicly, avant dont use my icon theme..  and the solution  should be to create a symbolic link to my icon theme, but from where?

---

### Post by nikoPSK on 2008-02-09
well, for launchers you could specify the icons... :):confused:

---

### Post by aktiwers on 2008-02-09
I know.. but more specifically I'm talking about the Applets and running programs in the launcher menu. Both the Trash and Terminal looks pretty ugly :(

---

### Post by nikoPSK on 2008-02-09
> **aktiwers said:**
> I know.. but more specifically I'm talking about the Applets and running programs in the launcher menu. Both the Trash and Terminal looks pretty ugly :(

Maybe in the .avant (or whatever it's called) folder you could try modifying. :|

---

### Post by seepage87 on 2008-02-09
I'm having the same problem and believe it runs a little deeper too.  I'm using the Mac4Lin icon theme, and it has some interesting and terrible consequences.

The most notable an applet that have custom icons that it uses won't be used.  In fact <i>nothing</i> will be used.  With the Last.fm applet (awesome btw), there are custom icons for the 'play', 'skip', 'love', 'ban' buttons, but they don't show up, making the buttons invisible and shrunken to perhaps 2 pixels wide.  Makes it near impossible to use.  If I switch to a system icon theme, the buttons appear again (but my desktop environment looks ugly).

Ideally it should just work, but is there a way to get the applets to use their custom icons (which sit in,e.g.,  ~/.config/awn/applets/lastfm/icons)?

---

### Post by denham2010 on 2008-02-09
See my post in this thread to solve the AWN - Mac4Lin icon problem.

[http://ubuntuforums.org/showthread.php?t=683534&highlight=mac4lin]("http://ubuntuforums.org/showthread.php?t=683534&highlight=mac4lin")

The post in this link will fix things like the LastFM applet.

As for AWN using the icon theme, this just happened automatically for me. But I did compile AWN from source rather than using the repositories.

Just slightly off topic, but still on themes, I found the Mac4Lin theme would not work on certain windows, such as Synaptic. My solution to this was to install the theme to /usr/themes as root instead of installing to ~/.themes.

Now all my apps are themed correctly.

---

### Post by seepage87 on 2008-02-14
That definitely worked for the last.fm problem.  thanks.

---

