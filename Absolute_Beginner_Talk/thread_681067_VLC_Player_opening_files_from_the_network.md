---
title: "VLC Player opening files from the network"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by appwraith on 2008-01-28
Hi Everyone,

I'm a complete newbie to Ubuntu, or even to Linux, so please forgive me if I ask something obvious :)

I have an HP NC6400 notebook as a hardware, and I'm attempting to play .mkv files in 720p, stored on a Windows based server. The default media player (Totem as I recall) opens them form the network perfectly, however playback of the file is very choppy. I have already figured out, that the hardware is probably too weak to decode in this resolution. In Windows, using CoreAVC as a codec, or VLC player on this very same notebook however results in perfect performance with minimal CPU overhead, so I installed VLC player on Ubuntu. I was partially successful: if the file is on a dvd, or the local hard drive, it plays the file perfectly, without a glitch. If I try to open files from the server however (by right clicking the file, choosing 'Open with a different command' and choosing VLC player), the player starts, but nothing happens. If I click File > Open file in the player, the shortcut I previously placed on the desktop pointing to the share does not appear. As you probably know, in windows you can map a network drive, and access it from My Computer. I'm sure, that a solution like that exists in Linux, but I have absolutely no idea where to find it, or if it will solve my problem.

Again, please excuse me for being so long, and asking a probably dumb question. :)

Thanks in advance!

---

### Post by appwraith on 2008-01-28
Sorry, I forgot to mention, that the file is coded in x264...

---

### Post by h0ax on 2008-01-28
Do you want to share movies from the Windows machine and play them on the linux machine?
Set up the share on Windows, Map the drive on Linux.
Then play from that mapped drive.

Is that what you're doing now?

---

### Post by wankel on 2008-01-28
> **h0ax said:**
> Do you want to share movies from the Windows machine and play them on the linux machine?
Set up the share on Windows, Map the drive on Linux.
Then play from that mapped drive.

Is that what you're doing now?


I hope I do not misinterpret many things here, but I guess that that indeed is something like that is what appwraith likes to do. Reading from his post, I guess that "map the share on Linux" is to "dense" for him.

Unfortunately I am do not know how to do the mapping correctly: whenever I use samba for playing media, it caches the whole file (not handy for watching a movie like "now" and clumsy for an ogg or flac playlist as well).

I end up not watching movies so often, and listening music over sshfs (as long as it keeps accessible)

All in all, I am interested as well :-)

---

### Post by appwraith on 2008-01-29
Hi All,

Fortunately, after some reading, I have managed to do what I intended using a program called Smb4K. As far as I understand, it browses Windows shares, and makes them appear in your Home folder. VLC now actually thinks, that the file is on the local hard disk, as it accesses the path as \home\smb4k\(SERVERNAME).

Thanks for your replies.

appwraith

---

