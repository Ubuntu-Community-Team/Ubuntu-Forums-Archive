---
title: "Playlist compatability questions - XMMS-Winamp"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-04-14
Hi.  All my MP3's are stored on a network storage device (HPMediavault).  I have mounted the device as a NFS mount onto my Linux Machines.  I enqued some songs into XMMS.  They play fine.  I saved the playlist onto the HPMediavault as playlisttest.m3u.  Both of my linux machines can open the playlist and play the songs.  However, when I use my windows machines, the playlist doesn't reference the correct locations.  It loads the list and titile information for the songs, but it treats them as missing files and just skips through the entire list.

It may be because the NFS is mounted in my filesystem and the playlist is referencing the filesystem location instead of the network location.  I tried going in with Samba and enqueing the files, but then XMMS won't play the songs.  

So I need a solution to this situation.  I want to make playlists, store them on the Network Storage Device, and play them on linux and windows.  Is there a program that will do this?  I'm willing to ditch XMMS if there is a player that will suit this task better.

---

### Post by energiya on 2007-04-14
Well, you could use [MPD]("http://musicpd.org/") if you have one computer started, it can act as a server and music could be controlled from all the others in the network. For me, it has replaced XMMS. I'm using ncmpc (for console) and gmpc (for X). For windows there are the web based clients.
> 
Music Player Daemon (MPD) allows remote access for playing music (MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files) and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It is also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.


---

