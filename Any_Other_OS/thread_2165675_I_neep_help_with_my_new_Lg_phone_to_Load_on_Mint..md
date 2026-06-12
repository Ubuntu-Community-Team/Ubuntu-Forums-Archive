---
title: "I neep help with my new Lg phone to Load on Mint."
date: 2013-08-05
forum: Any Other OS
---

### Post by lucas3 on 2013-08-05
So recently got a new phone, the lg optimus. i have my old sandics sd card from my old phone that has music on it, witch plays fine on my new phone. But i can not get new music on my new phone. I plug it in and get: 
Unable to Mount LGE mobile
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending.

I was just wondering if there was something i could do to fix it, or whatever.
I am running Liunx Mint 13 Maya.
Any help would be greatly appricated.

---

### Post by BBQdave on 2013-08-05
> **lucas3 said:**
> ...i can not get new music on my new phone. I am running Liunx Mint 13 Maya.

I am running Ubuntu Unity 12.04LTS, what Maya is based on. I use Rhythmbox, and I believe Maya has Banshee, but the following information helps with mounting and reading portable devices:

*If Rhythmbox Music Player does not detect your device as a portable audio player, you can create an empty file named* **.is_audio_player** *at the top level hierarchy of the filesystem of your player.*

I did this with a Sansa Clip+ set to **MSC** mode, and I can mount the portable device with Nautilus or use Rhythmbox to sync playlists.

---

### Post by Cheesemill on 2013-08-06
*Thread moved to **Other OS/Distro Support**.*

---

