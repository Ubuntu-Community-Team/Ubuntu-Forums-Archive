---
title: "player to watch shared movie on network with subtitle?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2007-09-27
Hi,
Does anyone know of a movie player which can play movie from a shared folder on a network with subtitle?
With totem, I get the error "Internal data flow error." when there is a subtitle file with the same name. If I rename the file, then It'll play, without subtitle. If I copy both the movie and the subtitle files to a local drive, then It'll play fine. There was only one time, by chance or luck, it played with subtitle from the network. JUST ONCE, the 2nd time, the same error occurred.
Any ideas?

---

### Post by justleen on 2007-09-27
try VLC

---

### Post by designwiz on 2007-09-27
sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc

    * In order to stream video via vlc, you also need to install the following packages. 

sudo apt-get install avahi-daemon
sudo apt-get install avahi-utils

---

### Post by lian1238 on 2007-09-27
I've tried VLC, it just ignores the subtitle file, I think.

---

### Post by hyper_ch on 2007-09-27
vlc plays subtitles for me when I want it...

---

### Post by lian1238 on 2007-09-27
> **hyper_ch said:**
> vlc plays subtitles for me when I want it...

across the network? from a shared folder?

---

### Post by notwen on 2007-09-27
I use VLC to watch anime from a shared NFS drive and it plays files w/ subtitles w/o issue.

---

