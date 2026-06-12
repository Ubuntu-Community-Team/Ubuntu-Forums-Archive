---
title: "[SOLVED] A few ubuntu and openbox questions"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by sunv on 2008-01-07
Hi I was wondering if you guys could help me with a few problems i've been having.  I use ubuntu Gutsy Gibbon with openbox as the DE:

I recently added mpd to use with conky.  It is great, I like using ncmpc.  One time while the song Too Long by Daft Punk was playing, I logged out.  And for some reason the song was still playing at the login screen.  So I logged back in and typed 'sudo killall mpd' and it stopped.

However now whenever I turn on my computer from cold, at the login screen the song can be heard playing and it always begins at the same place.  I have to login in and do sudo killall mpd first thing when I get in, and then after restart conky because killing mpd seems to kill conky too.

I was wondering what is causing this problem.  I think some initialization file saved that mpd was doing this task at the time I logged off, so when i start the computer again, it keeps going.  This is embarassing as I could be using my laptop in the library and when I turn it on it just starts playing music.

Another problem is that nautilus seems to consume large amounts of my CPU.  I have heard this is a bug.  How different is Thunar compared to nautilus?  Exactly the same?

Another problem: How do I make VLC player the default movie player instead of Totem player?  I have to download special codecs for Totem when I play my videos and I dont want to do that, because VLC can play them.  I looked at Preferred applications but that has only for multimedia which was like music files.  I want to be able to just press Enter on a video file and VLC plays it instead of Totem.  Not having to right-click and choose VLC.

Thanks!
---------------------------------------
Another problem now.  I tried reinstall mpd following this guide: [http://ubuntuforums.org/archive/index.php/t-31763.html](http://ubuntuforums.org/archive/index.php/t-31763.html)
But now I can't even install mpd, it just hangs at "Starting Music Daemon Player:"

Please help!

---

### Post by sunv on 2008-01-07
Ok I read up some more on this
it seems it is normal for mpd to keep playing after one has logged out.  It runs its own session apparently.

How do I make it so it gets killed when I log out, and starts again when I log in.
I know there is autostart.sh that defines the startup sessions, is there a similar logout script?

---

### Post by urukrama on 2008-01-07
Regarding mpd: to stop it before shutting down, use the following command:

```
mpc stop
```

If you want a shut down script, have a look [here]("http://urukrama.wordpress.com/2007/12/03/confirm-to-shut-down-reboot-or-log-out-in-openbox/"). To add the mpd thing to it, add the above line (mpc stop) before the command you want to link it with. So if you want to stop mpd when shutting down, make sure 4) in the script in the above link looks like this:

```
4)
	mpc stop
	sudo shutdown -h now;;
```

This should work.

EDIT: I always use [this]("http://ubuntuforums.org/showthread.php?t=320469") guide to set up mpd. I haven't looked closely at the one you linked to, but that one is rather old (2005). 

> **sunv said:**
> Another problem is that nautilus seems to consume large amounts of my CPU.  I have heard this is a bug.  How different is Thunar compared to nautilus?  Exactly the same?

Thunar is great, and has some features that make me like it more than Nautilus (the custom actions, restore from trash). I believe it isn't good for network browsing, but if you rarely have to do that, Thunar is probably much better for you. It runs a lot lighter. Why don't you install it and try it out?

> **sunv said:**
> Another problem: How do I make VLC player the default movie player instead of Totem player?  I have to download special codecs for Totem when I play my videos and I dont want to do that, because VLC can play them.  I looked at Preferred applications but that has only for multimedia which was like music files.  I want to be able to just press Enter on a video file and VLC plays it instead of Totem.  Not having to right-click and choose VLC.

If you use Thunar, right click on a file of the type you want to associate with VLC, click Properties. You'll see that under the file name it says 'Kind' and under that 'Open with'. Select the program you want (VLC) and that file type will be associated with VLC. You might have to restart Thunar.

---

### Post by sunv on 2008-01-07
Thanks alot
ur info solved my problems

---

