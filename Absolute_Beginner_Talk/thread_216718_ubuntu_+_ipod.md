---
title: "ubuntu + ipod"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-07-15
anyone know how to transfer music to an ipod using ubuntu. when i had xp i just used itunes. now i only have ubuntu, what should i do?

---

### Post by T700 on 2006-07-15
I use Amarok (a KDE app, but it will run nicely under Gnome).  Works like a charm.

Paul

---

### Post by da1nonlymikeo on 2006-07-15
awesome thanks paul ill give it a try.

---

### Post by catlett on 2006-07-15
The easiest app is gtkpod. It works just like Itunes in that it auto detects and updates when you plug it in.
you can install it with ```
sudo apt-get install gtkpod
``` or use synaptic package manager to install. System<Administration<Synaptic Package Mnager.
This is synaptics description 
> manage songs and playlists on an Apple iPod
gtkpod is a platform independent GUI for Apple's iPod using GTK2. It
allows you to upload songs and playlists to your iPod. It supports ID3
tag editing, multiple charsets for ID3 tags, detects duplicate songs,
allows offline modification of the database with later synchronisation,
and more.

---

### Post by TheRingmaster on 2006-07-15
> **catlett said:**
> The easiest app is gtkpod. It works just like Itunes in that it auto detects and updates when you plug it in.
you can install it with ```
sudo apt-get install gtkpod
``` or use synaptic package manager to install. System<Administration<Synaptic Package Mnager.
This is synaptics description
what he said

---

### Post by da1nonlymikeo on 2006-07-15
thanks guys, i just dowloaded amarok and it seems pretty simple, but is it in any way possible to copy the music from my ipod and store it onto hard disk. like in my home folder/shared music.

---

### Post by 3rdalbum on 2006-07-16
Just do it in the normal way.

The iPod will be mounted on your desktop as an ordinary hard disk. Just open that up, find the iTunes_Music folder, and drag the files to your home directory. You will need to do some reorganisation of them, unfortunately; Apple obviously thought it was a good idea to split your music up into hundreds of unnamed folders, which is why I bought a Teac MP-20G ;-)

---

