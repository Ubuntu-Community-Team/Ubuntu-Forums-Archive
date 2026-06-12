---
title: "Music Management"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-04-19
I'm looking for a way to switch over from managing my music in windows to linux, but I'm not exactly sure how to do it cleanly.

My Situation:
[LIST]
[*]I have an iPod.
[*]Until now, I have used Windows+iTunes for my music playing needs.
[*]My library consists of unprotected MP3 and AAC files.
[*]I now tend to use Linux more often on a day-to-day basis.
[/LIST]

Is there any way I can convert ratings/etc from iTunes and import them into Rhythmbox (or similar)?

Is there any way I can use Rhythmbox (or similar) to play and manage my library, yet be able to properly download to my iPod in linux (with ratings, album art, etc)?

Is there any way, for when I switch back to Windows for a bit, to let iTunes see and play the music without mucking around with Rhythmbox's settings and organization?

(Dupe of this unanswered post: [http://ubuntuforums.org/showthread.php?p=2486847#post2486847](http://ubuntuforums.org/showthread.php?p=2486847#post2486847))

---

### Post by userundefine on 2007-04-19
I don't think you can import ratings and such.

I'm not sure about rhythmbox's ipod support (and of course it'll depend on how old your ipod is), but there is also gtkpod for syncing.  Or, if you want to do it within your music prog, check out Amarok which is an excellent app (best for music on Linux, windows, or mac IMO).  It lets you sync the pod in itself.  There's also Exaile, which is an Amarok clone for gtk gnome desktops.  Not sure about its ipod support, however, because it's still pretty young.

As for playing from windows to linux, your music would have to be on a partition readable by both OSes.  There is an ext3 plugin or some such for Windows so you can read the ext3 filesystem (ubuntu default) in Windows, but I haven't had any experience with it.  That's what I'd recommend if you're only *reading*, not writing, to the files.  If you're doing that, maybe a FAT32 partition would be best (unless you can write to ext3 from within windows -- as I said, I don't have that much experience with it).

---

### Post by Raptor45 on 2007-04-20
I've already setup Windows with the ext3 plugin.

I was trying out Banshee, but Exaile sounds intriguing. Can anyone give a comparison?

Its too bad rhythmbox doesn't seem quite with it.

---

### Post by strabes on 2007-05-01
Use amaroK. It's far superior. It has built in ipod syncing abilities. While you're at it, you might as well just switch to KDE.

---

