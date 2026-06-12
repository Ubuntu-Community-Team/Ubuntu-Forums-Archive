---
title: "Network Icon + Brain = Insanity"
date: 2006-05-22
forum: Art &amp; Design
---

### Post by deadlydeathcone on 2006-05-22
With today's art update the Dapper theme has finally started to look finished and perhaps even beautiful (gasp), with one exception... the horrible, horrible network icon, that was somehow made even worse. Like the title says, it and my brain are a bad combo.

The icon has been broken for a long time, so I decided to fix things somewhat. Take a look at the attachments for a before and after shot.

Installation:

Simply drag Human-Fix.tar.gz into the theme manager. If you want to install it for the root user, use the command:

```
sudo tar -xvvzf Human-Fix.tar.gz --directory /usr/share/icons/
```

after browsing to the directory that the file was downloaded to in the terminal. It won't overwrite the default icon theme, so reverting back in case you don't like it is easy.

Before:
[ATTACH]9867[/ATTACH]

After:
[ATTACH]9868[/ATTACH]

Scalable Version:

[ATTACH]9888[/ATTACH]

Static Version (shown in shot):

[ATTACH]9887[/ATTACH]

edit: If you downloaded the scalable version earlier, you want to re-download, as I uploaded a version that actually works.

---

### Post by mihai.ile on 2006-05-22
one more thing about this:
i mean my wireless signal is at 98% and the icon shows only 2 lines with lighten green. how is that possibile?

I noticed that your icon in the screnshot also shows only 2 lines...

---

### Post by deadlydeathcone on 2006-05-22
You should be okay, the icons are just a little confusing as the bottom square is always a pale green as a result of the transleucent look of the bar itself.

Hit Control-L in nautilus and paste this in to see the bar at various stages:

/usr/share/icons/Human-Fix/24x24/apps

---

### Post by depp on 2006-05-22
hi deadlydeathcone,
why did you remove the 48x48 ones?

---

### Post by deadlydeathcone on 2006-05-22
I added a scalable version with the larger icons (it's a smaller download as well since it inherits the base human theme). The reason that they were removed in the original is that they were always used in favor of the smaller icons, and they looked weird at 1024x768.

---

### Post by bionnaki on 2006-05-24
weird. I tried this, but the icon stays the same - even after killing gnome panel. any ideas?

---

### Post by depp on 2006-05-25
It's fixed with the latest update!

---

### Post by deadlydeathcone on 2006-05-25
Well, kind of... they got rid of the white space but kept the ping-pong network monitor. Still, it looks much better.

bionnaki - This may be a stupid question, but did you install the theme using the theme selector, then make sure it was the active icon theme?

---

