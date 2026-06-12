---
title: "Audio player - Minimalist like Winamp with tray icon"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Green_biri on 2007-11-24
Hi everyone. As said in the title, I'd like you to suggest an audio player (only audio player, because I already got VLC to play movies) really minimalist, **without library** and with an option to put it to a tray icon.

I've already tried XMMS with the docklet plugin, but there was a bug (which consisted of showing a balloon with the title information and you had to click it to disappear)

I tried Beep and Audacious but couldn't find any tray icons for them.

Sugestions, please?

Thank you.

---

### Post by philinux on 2007-11-24
Try amarok

---

### Post by Green_biri on 2007-11-24
> **philinux said:**
> Try amarok

It has a library, doesn't it?

---

### Post by philinux on 2007-11-24
It boots straight to the system tray.

---

### Post by Green_biri on 2007-11-24
> **philinux said:**
> It boots straight to the system tray.

Can the library be disabled?

---

### Post by jordanmthomas on 2007-11-24
Audacious DOES have a tray icon.  Go to its preferences, then to the plugins.  Go to the General tab and enable the "status icon" plugin.

---

### Post by Green_biri on 2007-11-24
> **jordanmthomas said:**
> Audacious DOES have a tray icon.  Go to its preferences, then to the plugins.  Go to the General tab and enable the "status icon" plugin.

Uh... I don't see anything there...:confused:

---

### Post by jordanmthomas on 2007-11-24
hmmm, is there maybe an audacious-plugins package you didn't install.
I ask because it's definitely there for me.

Try installing audacious-plugins and audacious-plugins-extra
```
sudo apt-get install audacious-plugins audacious-plugins-extra
```

---

### Post by Green_biri on 2007-11-24
> **jordanmthomas said:**
> hmmm, is there maybe an audacious-plugins package you didn't install.
I ask because it's definitely there for me.

Try installing audacious-plugins and audacious-plugins-extra
```
sudo apt-get install audacious-plugins audacious-plugins-extra
```

Well, I installed that but it didn't install that plugin... what a luck...:(

---

### Post by markharding557 on 2007-11-24
listen music player has a library and a tray icon

---

### Post by sc30317 on 2007-11-24
exaile can minimize to system tray

---

### Post by jordanmthomas on 2007-11-24
> **markharding557 said:**
> listen music player has a library and a tray icon

> **sc30317 said:**
> exaile can minimize to system tray

He wants a player without a library feature though.

---

### Post by Green_biri on 2007-11-25
> **jordanmthomas said:**
> He wants a player without a library feature though.

Correct...:)

---

### Post by Paulmd on 2007-11-25
> **Green_biri said:**
> Hi everyone. As said in the title, I'd like you to suggest an audio player (only audio player, because I already got VLC to play movies) really minimalist, **without library** and with an option to put it to a tray icon.

I've already tried XMMS with the docklet plugin, but there was a bug (which consisted of showing a balloon with the title information and you had to click it to disappear)

I tried Beep and Audacious but couldn't find any tray icons for them.

Sugestions, please?

Thank you.

XMMS really is one of the best audio players for linux. It doesn't go down to a tray icon, but it shrinks to about 10 pixels tall by 100 wide. I never used the docklet plugin.

There is a command-line only audio player for linux, but I have forgot its name. (I never really wanted to use it)

---

### Post by jordanmthomas on 2007-11-25
> **Paulmd said:**
> 
There is a command-line only audio player for linux, but I have forgot its name. (I never really wanted to use it)

There's a bunch.  You can use mplayer, mpd + ncmpc (a personal favorite, but mpd uses playlists / library, which op doesn't want.  With mpd you can also have a GUI client like Sonata), herrie, mpg123, the list can go on.

---

### Post by SaltyCrak on 2007-11-25
i would like the new winamp 5.5 (i think) to run on ubuntu. i've got it on my office PC and it's sorted!

---

### Post by Green_biri on 2007-11-25
> **SaltyCrak said:**
> i would like the new winamp 5.5 (i think) to run on ubuntu. i've got it on my office PC and it's sorted!

Oh, but that version is like multimedia, and I'd like it simple and without library...:(

---

### Post by jordanmthomas on 2007-11-25
I still say you should try to get audacious working.
According to the ubuntu package search, the package audacious-plugins has the file you need for the status icon plugin.

I have taken the liberty of extracting the library so you can put it where it belongs manually:
Save the file attached to your Desktop.
Right click it and go to "extract here"
open a terminal and type this:
```
cd Desktop
sudo cp libstatusicon.so usr/lib/audacious/General/libstatusicon.so
```

Next time you start audacious it should be able to find this plugin.

---

### Post by Green_biri on 2007-11-25
Ok, I decided to install Audacious... but I got a problem:

The last version in the repositories is 1.2.2-4, which doesn't has the tray plugin, so I'd like some help to install the most recent version, please...

Thanks for your help :)

---

### Post by rsambuca on 2007-11-25
Mind if I ask why you DON'T need a library?  It isn't like you have to look at it all the time or anything.

---

### Post by jordanmthomas on 2007-11-25
aha!  So that's why you don't have the plugin.
Unfortunately, I don't know of any way to get a newer version other than going to audacious's website and downloading it from there.

You could try getting the Gutsy version from Ubuntu package search, but I would think that could lead to problems.

---

### Post by jordanmthomas on 2007-11-25
> **rsambuca said:**
> Mind if I ask why you DON'T need a library?  It isn't like you have to look at it all the time or anything.

That's true, and even if a program HAS a library you don't have to use it if you don't want.

---

### Post by Green_biri on 2007-11-25
> **rsambuca said:**
> Mind if I ask why you DON'T need a library?  It isn't like you have to look at it all the time or anything.

Cause I don't like the library to search my files and then when I delete or add something I need to actualize it... not to mention the Author and Title and all that stuff categories, which bother me a lot...

---

### Post by Green_biri on 2007-11-25
> **jordanmthomas said:**
> aha!  So that's why you don't have the plugin.
Unfortunately, I don't know of any way to get a newer version other than going to audacious's website and downloading it from there.

You could try getting the Gutsy version from Ubuntu package search, but I would think that could lead to problems.

Hum... serious problems?:-k

---

### Post by Taboo Mirage on 2007-11-25
Could I recommend a program called alltray, which is in the universe repositories. You can minimize basically any program to the system tray if you use it.

```
alltray gedit
``` 

That, for instance, will drop the text editor to the system tray, with an icon.  It can be very useful for applications that you want in the tray but do not natively minimize to it.

Take care.

---

### Post by Green_biri on 2007-11-25
> **Taboo Mirage said:**
> Could I recommend a program called alltray, which is in the universe repositories. You can minimize basically any program to the system tray if you use it.

```
alltray gedit
``` 

That, for instance, will drop the text editor to the system tray, with an icon.  It can be very useful for applications that you want in the tray but do not natively minimize to it.

Take care.

Thank you very much. And thanks to the others, of course...=D>

---

