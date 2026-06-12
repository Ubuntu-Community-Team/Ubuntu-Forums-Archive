---
title: "Get rid of desktop icons"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-04-19
hello,
just installed Fiesty, and after mounting some things, got a desktop like this:
How to to get rid of the destop icons, I already have them in "Places" ?????     :confused: 
Thanks :) :)

---

### Post by scxtt on 2007-04-19
AFAIK, the gconf editor can do that ... something like "desktop icons = off" ...

---

### Post by yabbadabbadont on 2007-04-19
Yes, use the gconf editor and expand the nautilus section under apps.  In the nautilus settings there is a key called something like "Show on desktop".  There are various options you can turn on and off.  However, if you disable the "mounted volumes" setting, not only will the icons you want removed be gone, but so will mounted CDs, DVDs, and USB drives...  Can't have one without the other in Gnome.  Now in KDE on the other hand...  ;)

---

### Post by Drakkor on 2007-04-19
Sorry:
godzilla@drakkor-desktop:~$ gcnfig
bash: gcnfig: command not found
godzilla@drakkor-desktop:~$ gconfig editor
bash: gconfig: command not found
godzilla@drakkor-desktop:~$ gconfig
bash: gconfig: command not found
godzilla@drakkor-desktop:~$

---

### Post by yabbadabbadont on 2007-04-19
```
gconf-editor
```

---

### Post by Drakkor on 2007-04-20
ok,that's nice what about my  problem ??? :confused:

---

### Post by haricharan on 2007-04-20
I believe this could help you....

[IMG]http://www.gabrielteratos.oi.com.br/gconf_desktoptrash.jpg[/IMG]

---

### Post by Drakkor on 2007-04-20
Thanks all !! Actually it was this:  Problem solved !!!

---

### Post by nitebum on 2007-04-20
Thanks for the fix guys. This should be an install option or something. Who wants that on the desktop, really.:)

---

### Post by maxwellcom on 2007-04-21
This option, which worked for me in Dapper and Edgy, does not have any effect on my Feisty installation.   I did

```
sudo gconf-editor
```

and set "/apps/nautilus/desktop/volumes_visible" to "false"

with no effect.  I've rebooted twice.  It's a fresh, unmodified installation.

Any suggestions?

---

### Post by maxwellcom on 2007-04-21
...to answer my own question, the problem was with how i started the Gnome Configuration Editor:

by using

```
sudo gconf-editor
```

I was editing the configuration for root, which of course had no effect on my desktop.  When I finally used plain old

```
gconf-editor
```

and made the same changes, it worked just fine.  Duh...

---

### Post by Drakkor on 2007-04-21
Hmmm...... I just put ```
gconf-editor
```

---

