---
title: "mpc help"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-01-21
I am trying to learn things the CLI way.  But I am having trouble figuring out how to work MPC.  I have already installed MPD.

How do I play individual songs?

I tried:
```
 mpc -play ~/path/to/file
```
But does not work.

I tried the example given in the manual:
```
 mpc ls | mpc add
```
But gets returned with something that has to do with localhost not responding.

Please help!

---

### Post by tbroderick on 2007-01-22
Did you setup mpd? You need to edit /etc/mpd.conf, then you can create your db. If you are looking for a simple console music player, try moc, mp3blaster, or cplay.

---

### Post by newbie22 on 2007-01-22
No, I did not configure it.  I did not know I had to.  From the looks of it, it might to be hard for newbies.

After reading more about the MPD/MPC thing, it looks like it was meant to be a remote mplayer.

I have looked at the screenshots of moc, mp3blaster, and cplay.  They look like audio players that will turn my console into a player.  What I am looking for is an audio player that can play in my console without turning it into a player.

You know how I can add the "&" at the end of a command to make it run as background and not have it occupy my console foreground?  I wish that can be done with mplayer, but it does not work.

I am looking for something like that will run in console, but not occupy and prevent me from doing other things in it.

Anyone know anything like that?

---

### Post by pistcivet on 2007-01-22
I've never tried it, but I think mpg321 would work.
Check out its man page.

---

### Post by tbroderick on 2007-01-22
> No, I did not configure it.  I did not know I had to.  From the looks of it, it might to be hard for newbies.

It's not too hard, but maybe not for newbies.

> After reading more about the MPD/MPC thing, it looks like it was meant to be a remote mplayer.

Yes and no. It's basically a daemon (MPD) that runs in the background of a computer. You can either remote play the music or locally with any number of frontends (mpc, ncmpc, gmpc, sonata). I use it as my desktop music player.

> You know how I can add the "&" at the end of a command to make it run as background and not have it occupy my console foreground?  I wish that can be done with mplayer, but it does not work.

Moc does that. If you are in a console or X terminal, you can press "q" and the interface will close but the music/playlist will still keep going and the console/terminal is free to use.  Moc is similar to mpd but isn't as hard to setup.

---

