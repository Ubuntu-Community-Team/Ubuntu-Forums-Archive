---
title: "Complete newbie and fluxbox"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by ains on 2007-09-18
Hi everyone.
I'm completely new to the whole linux thing, so you'll have to bear with me!

In an attempt to install and use fluxbox, I followed word for word this guide:
[http://ubuntuforums.org/showthread.php?t=116759&highlight=installing+fluxbox](http://ubuntuforums.org/showthread.php?t=116759&highlight=installing+fluxbox)

Yet when I log on and attempt to load the fluxbox session,  I get a message telling me:
Unable to launch "/home/ains/.fluxbox/startup" X session because it's not found
Or something along those lines..

Does anyone have any ideas how I could of gone wrong?
You're talking to a complete newbie remember so lamens terms are appreciated.

Thanks in advance,
Ains

---

### Post by kerry_s on 2007-09-18
just use the one in the repo's.

[B]sudo apt-get install fluxbox
sudo update-menus[/B]

log out select fluxbox and log in

you should learn fluxbox first, before you try compiling your own were you have to set it all up.

---

### Post by ains on 2007-09-18
It says that it's already at the newest version.
I've tried updating the menus but I still get the same error when choosing it :(

Thanks for trying though!
Ains

---

### Post by ains on 2007-09-18
Well I tried removing fluxbox and reinstalling using the one from repos but I still get the the same problem (cannot be found).
Weird :)

All help appreciated!

---

### Post by RedSquirrel on 2007-09-18
Did you remove the /usr/share/xsessions/fluxbox.desktop file before you installed fluxbox from the repositories? I would start from scratch, like this:

1. I would remove the fluxbox you have.

2. Then remove the ~/.fluxbox directory tree (there may not be one, but just in case):

```
rm -rf ~/.fluxbox
```3. Remove the /usr/share/xsessions/fluxbox.desktop file:

```

cd /usr/share/xsessions
sudo rm fluxbox.desktop
cd ~
```

4. Then install fluxbox again using the instructions kerry_s gave above.


[COLOR=Blue]** EDIT**[/COLOR]

The guide you linked to hasn't been updated in a while and could use a rewrite.

The important thing is that Fluxbox should be started by running the script **startfluxbox**.

For the version from repositories, once you install it, you will note the file /usr/share/xsessions/fluxbox.desktop has an Exec line like this:

```
Exec=/usr/bin/startfluxbox
```So, if it some point you decide to remove the version from the repositories and go with your own compiled version, you need to change the Exec line in /usr/share/xsessions/fluxbox.desktop:

```
Exec=/usr/local/bin/startfluxbox
```

---

