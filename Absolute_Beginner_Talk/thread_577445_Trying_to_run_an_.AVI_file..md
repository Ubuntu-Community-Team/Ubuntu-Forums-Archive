---
title: "Trying to run an .AVI file."
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-10-16
Can't open .AVI file. Need a codec, can't find it. Pl0x help.

[img]http://img153.imageshack.us/img153/3254/screenshotfz8.png[/img]

---

### Post by Dr Small on 2007-10-16
Try installing VLC, as it is supposed to have alot of formats that it can play, as well as DVDs, WMAs, MP3s and such, out of the box.

Dr Small

---

### Post by Bloch on 2007-10-16
There is a sticky thread at the top of this page:
Enabling Multoimedia in Feisty (7.04) and you need to go through the instructions there.
The media player does not have all codecs built-in due to patent issues etc.

Some other players, like VLC, have load of codecs built-in to them. Make sure you always have either mplayer or VLC installed - they might work where the default player (Movie Player) fails.


I'm not sure about the error message you are getting about /etc/apt/sources.list

Try to install VLC or something using the Add/Remove menu (bottom of Applications menu) and see if it reports a problem

---

### Post by JustinAllen on 2007-10-16
You can also go into Add/Remove and do a search for all of the Gstreamer packs.  That's what got avi's working for me.

---

### Post by rbprogrammer on 2007-10-16
try running those commands in the terminal.
```
$ sudo apt-get update
```
wait for that to finish, then do:
```
$ sudo apt-get install -f
```
then try opening the [ .avi ] file and download the codecs.

that should work, but if it doesnt, we can go from there...

---

### Post by tarchy on 2007-10-16
It reports the same problem when I go into add/remove.

---

### Post by tarchy on 2007-10-16
> **rbprogrammer said:**
> try running those commands in the terminal.
```
$ sudo apt-get update
```
wait for that to finish, then do:
```
$ sudo apt-get install -f
```
then try opening the [ .avi ] file and download the codecs.

that should work, but if it doesnt, we can go from there...

I tried that before but it works now, thanks a lot man!

---

### Post by Dr Small on 2007-10-16
> **tarchy said:**
> It reports the same problem when I go into add/remove.
Run the commands that rbprogrammer gave you, to correct the problem.

Dr Small

---

### Post by TNakos on 2007-10-16
ubuntu comes with movie player, try that.

---

