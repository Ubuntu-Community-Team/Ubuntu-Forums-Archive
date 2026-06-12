---
title: "Gnome-Desktop and KDE?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Depressed Man on 2007-07-18
I'm trying to install the latest Kiba-dock but when I try to install I get this error. 

```
checking for GNOME_DESKTOP... configure: error: Package requirements (gnome-desktop-2.0 >= 2.8) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_CFLAGS
and GNOME_DESKTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I thought I already had this? In fact when I try to install AWN it gives me a similar error. But there's no package as far as I know called gnome-desktop-2.0 in the repositories. 

Oh and I installed the entire kubuntu to try it out (I've been using gnome mainly). And it installed it..well except now everything in gnome and KDE are in the same menu. Which is kinda good I guess (I can access programs from one in another). It's just.. kinda distracting with both's entries in the menu. Any idea of how to make gnome show mostly gnome apps (perhaps editting the menu would work to hide all KDE entries?).

---

### Post by Papi-KB7VGW on 2007-07-18
I found gnome-desktop-data in the repos and it is for gnome2.  maybe that would help.  I tried KDE and ended up uninstalling it because of toooo many menu items.  I prefer the simplicity of Gnome

---

### Post by Depressed Man on 2007-07-18
Odd, when I use sudo apt-get install gnome-desktop-data it says I have the latest version already..

---

### Post by user1397 on 2007-07-18
hmm maybe try to use aptitude instead of apt-get, as in "sudo aptitude install kiba-dock" or whatever the package name is for kiba dock.

to edit the menus, simply right click on the menu itself, and select "edit menu"

you can also do that in kde

---

### Post by Depressed Man on 2007-07-18
I'm trying to make the latest SVN since the ones in repos are outdated.

---

### Post by coolen on 2007-07-18
> **Depressed Man said:**
> I'm trying to install the latest Kiba-dock but when I try to install I get this error. 

```
checking for GNOME_DESKTOP... configure: error: Package requirements (gnome-desktop-2.0 >= 2.8) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_CFLAGS
and GNOME_DESKTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I thought I already had this? In fact when I try to install AWN it gives me a similar error. But there's no package as far as I know called gnome-desktop-2.0 in the repositories. 

Oh and I installed the entire kubuntu to try it out (I've been using gnome mainly). And it installed it..well except now everything in gnome and KDE are in the same menu. Which is kinda good I guess (I can access programs from one in another). It's just.. kinda distracting with both's entries in the menu. Any idea of how to make gnome show mostly gnome apps (perhaps editting the menu would work to hide all KDE entries?).

Sounds to me like a name mismatch. Where are you trying to install from? Try getting it from Trevino's repository. I got kiba-dock installed fine from there (but for the fact that I can't add launchers...).

---

### Post by coolen on 2007-07-18
Oh, sorry, I see you were using SVN.
Trevino usually uses the latest releases anyway. Should be fairly recent, and keeping things within apt is a god idea.

---

### Post by Depressed Man on 2007-07-18
Well I'm not really trying to install gnome-desktop (I would assume it's already installed if I was using it lol). But I'm trying to build Kiba Dock from SVN. And this is the output after the make command. 

And I do have the one from Trevino's repository. It's just that the one in there is outdated and has issues like the launcher not being added from drag and drop. Also I want the ability to have my windows go in the space where the dock is (which is not present in the version in the repository).

---

### Post by Ptero-4 on 2007-08-02
What you need is the libgnome-desktop-dev package

---

### Post by coolen on 2007-08-02
> **Depressed Man said:**
> Well I'm not really trying to install gnome-desktop (I would assume it's already installed if I was using it lol). But I'm trying to build Kiba Dock from SVN. And this is the output after the make command. 

And I do have the one from Trevino's repository. It's just that the one in there is outdated and has issues like the launcher not being added from drag and drop. Also I want the ability to have my windows go in the space where the dock is (which is not present in the version in the repository).

Ahh, I see. I kind of dismissed it for the time being, as something fun, but not yet useful.
I kind of fear to tread outside of apt, for the most part. I just hate disorganisation...I once spent three days straight organising my music collection, finding albums for the random songs, deleting duplicates, using correct capitlisation...
I don't trust myself to keep things tidy.

---

