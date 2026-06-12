---
title: "Installing Kiba-dock on AMD64"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Alteranous on 2007-06-18
Hi :o
Im a newbie to linux, and im trying to get kiba-dock working for the 64bit version of ubuntu. Im following the guide on the kiba wiki, however, when i try and run the autogen.sh script i get the following error:

...
...
checking pkg-config is at least version 0.9.0... yes
checking for AKAMARU... yes
checking for GLIB... yes
checking for PANGO... yes
checking for GTK... yes
checking for GNOME_DESKTOP... configure: error: Package requirements (gnome-desktop-2.0 >= 2.8) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_CFLAGS
and GNOME_DESKTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Can anyone help out?

---

### Post by Alex&amp;Linux on 2007-06-19
Heyo

I had Kiba-dock running some time ago, found it to be considerably buggy, so I ditched it, now using Avant-window-navigator.

I would make sure that everything is up to date before attempting install.
Im sure its part of the instruction in the wiki, however:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Then restart and try again!

Again, not too familiar with it, but if youre interested in a little AWN action, this thread can take you through it:

[http://ubuntuforums.org/showthread.php?t=385981&highlight=install+kiba+dock](http://ubuntuforums.org/showthread.php?t=385981&highlight=install+kiba+dock)

Additionally, if youre using a 64-bit distro, you can go to the following link to download the deb:

[http://ubuntuforums.org/showthread.php?t=354009](http://ubuntuforums.org/showthread.php?t=354009)

Look for Tommaso's post, the link is there!

Good luck!

---

### Post by ferronica on 2007-06-19
yes ALEX&LINUX is 100% right KIBA-DOCK is buggy, use AWN its nice and easy to use and i am using it :) :)

---

### Post by Golyadkin on 2007-06-19
Well, if AWN didn't require Beryl, I would use it too. But I am not going to run Beryl just for AWN... I don't understand why it is a requirement. An application like AWN should work on any display manager.

---

### Post by Alex&amp;Linux on 2007-06-19
First off, thats a really cool picture, and I want it!
Secondly, sorry! I had assumed you were using beryl....I dont know too many people that arent these days!

Kiba was pretty cool, if you dont use any of the animations, or the physics, it wasnt too taxing of computer resources, and it didnt seem to crash any more than AWN does from time to time, however, AWN is hands down more useful, so if you can, I would use beryl ( you dont have to get too fancy, allowing it to run on a lower-powered system if that is the circumstance required)

Regarding Kiba, as I said, it has been a looong time, Ill look up some info for you!

---

### Post by Golyadkin on 2007-06-20
What? My picture? I just found it on the internet somewhere. I don't have the original anymore I think, but you can take mine [from here]("http://ubuntuforums.org/customavatars/avatar287860_1.gif").

---

### Post by Spike-X on 2007-06-20
I tried installing it on 64-bit and gave up. The deb didn't have the plugins, and when I tried to build the plugins from source I got errors, and it just wasn't worth it. Hopefully things will improve and it will be more easily available for us 64-bit users at some stage.

---

