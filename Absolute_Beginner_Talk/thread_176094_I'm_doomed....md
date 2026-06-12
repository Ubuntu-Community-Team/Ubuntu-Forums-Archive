---
title: "I'm doomed..."
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-05-14
ahhh...!
I've recently done a format to my computer, installed ubuntu breezy again. I've installed KDE, Fluxbox, and removed Gnome. and then upgraded to dapper.

Now I tried to reinstall Gnome, but the apt-get stopped in the middle, it couldn't install evolution, and ubuntu-desktop depends on evolution, so it stopped. great.

I restarted my computer, and Gnome appeared in the session menu, I logged on to gnome, fine.

Now everything is weird.
Windows dissapear, the taskbar is not working, synaptics doesn't load, add/remove starts and the crashes, everything is really slow, the screen has even gone grey for a few seconds and then back to normal.
And I think a lot off apps don't exist, I guess that's logical, but how do I fix it?
I did a normal sudo apt-get -f install, but that just tried to install evolution, which didn't work.

I tried to install a random app, just to see if it's only a problem with evolution, and it brings me back to the fact that there is a broken package, but I can't fix it...

This is REALLY weird...

Maybe I shouldn't have tried to upgrade to dapper *again*...

Now what do I do?

Thanks,
Josh:) ](*,) :-k :confused: ](*,) ](*,) ](*,) l

---

### Post by Sef on 2006-05-14
In Gnome, open the terminal (Applications > Accessories > Terminal)

then type this (push enter after each line)

sudo apt-get update 

once it finishes, type this

sudo apt-get install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

---

### Post by Caligula on 2006-05-14
I tried it,
It didn't do all the update, one failed...
I tried the line after that but it still says I've got the broken package...
baa...

---

### Post by kelsey23 on 2006-05-14
[QUOTE=Caligula]ahhh...!
I've recently done a format to my computer, installed ubuntu breezy again. I've installed KDE, Fluxbox, and removed Gnome. and then upgraded to dapper.

Now I tried to reinstall Gnome, but the apt-get stopped in the middle, it couldn't install evolution, and ubuntu-desktop depends on evolution, so it stopped. great.

I restarted my computer, and Gnome appeared in the session menu, I logged on to gnome, fine.

Now everything is weird.
Windows dissapear, the taskbar is not working, synaptics doesn't load, add/remove starts and the crashes, everything is really slow, the screen has even gone grey for a few seconds and then back to normal.
And I think a lot off apps don't exist, I guess that's logical, but how do I fix it?
I did a normal sudo apt-get -f install, but that just tried to install evolution, which didn't work.

I tried to install a random app, just to see if it's only a problem with evolution, and it brings me back to the fact that there is a broken package, but I can't fix it...

This is REALLY weird...

Maybe I shouldn't have tried to upgrade to dapper *again*...

Now what do I do?

Thanks,
Josh:) ](*,) :-k :confused: ](*,) ](*,) ](*,) l[/QUOTE]

Ubuntu doesn't really like having KDE and GNOME on the same system. If you want them both enviroments on the same system I would recommend upgrading to something like Fedora Core4 which is more powerful and better than Ubuntu anyway.

---

### Post by aysiu on 2006-05-14
It sounds as if you have conflicting repositories. Go to a terminal in KDE (since Gnome isn't working, apparently) and paste these commands in: ```
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo mv breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` [quote=kelsey23]Ubuntu doesn't really like having KDE and GNOME on the same system.[/quote] Sure it does. > If you want them both enviroments on the same system I would recommend upgrading to something like Fedora Core4 which is more powerful and better than Ubuntu anyway. When you claim one popular Linux distro is "better than" another popular Linux distro "anyway," your credibility goes out the window. Sorry.

---

### Post by edifuzzy on 2006-05-14
[QUOTE=kelsey23]Ubuntu doesn't really like having KDE and GNOME on the same system. If you want them both enviroments on the same system I would recommend upgrading to something like Fedora Core4 which is more powerful and better than Ubuntu anyway.[/QUOTE]

Nice thought...but I am a total linux noob and am running Dapper with both Gnome and KDE quite happily. I just select the session that I want to use before logging in....easy as pie. haven't had any issues. (YET!!)

.. To the Original Poster.... If you were doing a format and Re-install, why didn't you just download a proper Dapper ISO, burn it and use it to install? Surely would have been easier than installing Breezy and upgrading!

---

