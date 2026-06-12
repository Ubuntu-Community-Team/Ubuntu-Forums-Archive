---
title: "how do i uninstall.."
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-15
vlc
azureus
bittornado

vlc doesnt work for me i got it from synaptic so i will try to install it thru automatix and i have no use for the other 2 since they keep asking me to open some port and ktorrent works just fine for me.

---

### Post by loell on 2006-06-15
uncheck it in synaptic and click update

---

### Post by fluffington on 2006-06-15
```
sudo apt-get --purge remove vlc azureus bittornado
```

The --purge removes config files, which you may or may not want to do. Or you could locate the packages in Synaptic and remove from there.

---

### Post by u.b.u.n.t.u on 2006-06-15
[QUOTE=maddbaron]vlc
azureus
bittornado

vlc doesnt work for me i got it from synaptic so i will try to install it thru automatix and i have no use for the other 2 since they keep asking me to open some port and ktorrent works just fine for me.[/QUOTE]

How does VLC from synaptic not work if I may ask? Have you installed all the gstreamer codecs?

---

### Post by fluffington on 2006-06-15
[QUOTE=u.b.u.n.t.u]Have you installed all the gstreamer codecs?[/QUOTE]

I'm pretty sure VLC doesn't use gstreamer.

---

### Post by maddbaron on 2006-06-15
vlc doesnt work on video. i have no idea why. it wont open the video. i can hear the sound just fine but the video doesnt open at all on any file. i dont know what it is. i've tried adding all the codecs from automatix and still nothing...its all very odd.

---

### Post by maddbaron on 2006-06-15
ok got vlc and bittornado off with synaptic but azureus doesnt show as installed there even tho it is i even opened it from the applications menu. with that purge really mess me up i only want azureus gone now.

---

### Post by fluffington on 2006-06-15
[QUOTE=maddbaron]ok got vlc and bittornado off with synaptic but azureus doesnt show as installed there even tho it is i even opened it from the applications menu. with that purge really mess me up i only want azureus gone now.[/QUOTE]

Did you install Azureus through Synaptic/apt-get/aptitude, or did you download it from somewhere else?

---

### Post by maddbaron on 2006-06-15
got it from automatix just like bittornado.

---

### Post by fluffington on 2006-06-15
[QUOTE=maddbaron]got it from automatix just like bittornado.[/QUOTE]

I dug through the source of Automatix, and it appears to install Azureus from sourceforge rather than going through the repos. You'll have to delete /usr/share/applications/azureus.desktop and /opt/azureus.

```

sudo rm /usr/share/applications/azureus.desktop
sudo rm -R /opt/azureus

```

And do make sure you type that last one correctly. Using rm -R is very dangerous when one is prone to making typos.

---

### Post by maddbaron on 2006-06-15
well that worked thank you.

i reinstalled vlc and still has same problem. can listen but cant view videos...

---

### Post by fluffington on 2006-06-16
[QUOTE=maddbaron]well that worked thank you.[/QUOTE]

Yay.

[QUOTE=maddbaron]i reinstalled vlc and still has same problem. can listen but cant view videos...[/QUOTE]

I don't know how to fix this, but I've been digging through the Automatix source. Here's the list of packages Automatix uses to install VLC; hopefully it will help somebody else figure out what's wrong:

[list]
[*]vlc
[*]vlc-plugin-arts
[*]vlc-plugin-esd
[*]wxvlc
[/list]

---

### Post by fluffington on 2006-06-16
[QUOTE=maddbaron]i reinstalled vlc and still has same problem. can listen but cant view videos...[/QUOTE]

Do you mean to say that you can listen to audio files, but can't get anything from video files at all? Or you can get sound but no picture from video files?

What format are the videos you are trying to watch (wmv, mpeg, etc)?

What architecture is your system (x86, amd64, etc.)?

Which Ubuntu are you using (Breezy, Dapper, etc.)?

Which desktop are you using (GNOME, KDE, etc.)?

EDIT: Oops. Meant to have that all in one post. Oh well.

---

### Post by maddbaron on 2006-06-16
[QUOTE=fluffington]Do you mean to say that you can listen to audio files, but can't get anything from video files at all? Or you can get sound but no picture from video files?

What format are the videos you are trying to watch (wmv, mpeg, etc)?

What architecture is your system (x86, amd64, etc.)?

Which Ubuntu are you using (Breezy, Dapper, etc.)?

Which desktop are you using (GNOME, KDE, etc.)?

EDIT: Oops. Meant to have that all in one post. Oh well.[/QUOTE]

trying to view all thw video files but mostly wmv and avi

i have all those plugins.

my system is an amd sempron...i think amd64 not too sure.

dapper ubuntu

gnome with kde software and gnome software.

---

