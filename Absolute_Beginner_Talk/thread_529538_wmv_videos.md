---
title: "wmv videos?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2007-08-19
I'm trying to play a wmv video ([this one]("http://www.movies.war-rvr.net/files/bright_wizard_teaser.wmv")). And all I can get is sound.  I've tried using xine, totem, gxine, and mplayer, and no dice.

I'm usng the w32codecs from medibuntu.  I also have both bad and ugly gstreamer packages (as well as their multiverse variants) And I have also installed ubuntu restricted extras as described on the restricted formats page of the community docs.  If anyone has any knowledge of how to get this playing, please let me know.

Oh, and I'm able to convert them to avi with iriverter and then view them just fine (but this is kind of a hassle)

Thanks.

---

### Post by sailor2001 on 2007-08-19
I think you may have downloaded an encrypted file....

---

### Post by ajgreeny on 2007-08-19
vlc is another video player worth looking at.  It seems to play almost anything and comes with codecs already installed.

---

### Post by philinux on 2007-08-19
Plays fine on my mplayer so it's not encrypted? Can you play any wmv file with mplayer?

Under video in preferences my driver is set to X11

---

### Post by ekravche on 2007-08-19
Doesn't work for me either... I can play wmv files, but I can't play this file :(

---

### Post by mysticmatrix on 2007-08-19
The codec of this file is 
Windows Media Video 9 Advanced Profile (VC-1 AP)

I would try to find out how it can be played under Linux.

---

### Post by mysticmatrix on 2007-08-22
I am able to run the same trailer just fine by installing mplayer and w32codecs packages.

---

### Post by WebSiteGuru on 2007-08-22
I think that the problem I am currently running into.

---

### Post by WebSiteGuru on 2007-08-22
> **ajgreeny said:**
> vlc is another video player worth looking at.  It seems to play almost anything and comes with codecs already installed.

How do you default the vlc to be the plugin?

---

### Post by chrome307 on 2007-08-22
I didn't see any video but heard the audio track :(

---

### Post by logos34 on 2007-08-22
> **WebSiteGuru said:**
> How do you default the vlc to be the plugin?

If you're using Firefox browser you can get the MediaPlayerConnnectivity addon, or change it via edit>prefs>content>manage file types

---

### Post by WebSiteGuru on 2007-08-22
> **logos34 said:**
> If you're using Firefox browser you can get the MediaPlayerConnnectivity addon, or change it via edit>prefs>content>manage file types


What do I put in as manage file types?

---

### Post by mysticmatrix on 2007-08-22
> **chrome307 said:**
> I didn't see any video but heard the audio track :(

did you try that with Mplayer?

---

### Post by logos34 on 2007-08-22
> **WebSiteGuru said:**
> What do I put in as manage file types?

select wmv and change action by pointing it to VLC player (/usr/bin/X11/vlc ?)

---

### Post by chrome307 on 2007-08-23
[IMG]http://img353.imageshack.us/img353/3505/samplebs3.jpg[/IMG]

---

### Post by mysticmatrix on 2007-09-11
> **chrome307 said:**
> [IMG]http://img353.imageshack.us/img353/3505/samplebs3.jpg[/IMG]

Open Mplayer, right click and then select Preferences.

In that swicth to Video tab and then select either X11 or Xv as your video output module.
This will fix this error. Please report back.

---

### Post by u-slayer on 2007-09-11
ummm, I just opened that file in VLC. It's totally encrypted buddy.

---

### Post by chrome307 on 2007-09-12
I changed the settings as suggested for Mplayer but it did not work for me again :confused:

This is what it looks like in VLC

[IMG]http://i18.tinypic.com/4q6yscj.png[/IMG]

---

