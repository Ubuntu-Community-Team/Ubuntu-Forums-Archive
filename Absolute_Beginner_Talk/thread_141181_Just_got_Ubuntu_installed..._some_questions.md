---
title: "Just got Ubuntu installed... some questions"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by rorschach on 2006-03-07
OK, so, I just took the big step and converted my main Windows system over to Ubuntu. I just got everything installed (thanks to a fair amount of help from these forums, google, and a more experienced friend). Right now, I have a working system that is at the 'good enough' stage. Now I have some questions for some of the non-critical things I would like to get up and running again. 
This may more belong in another forum, heck, some of the various questions may belong in a number of forums.

Some background info:
This was a relatively decent gaming system, I have an ATI x800, Soundblaster Audigy 2, AMD-64 3.4Ghz, and 2GB RAM. I finally converted because I found I wasn't playing games hardly at all, and the games I do play are able to be played on my laptop (barely). I have both Gnome and KDE installed, because I want to play with both and make my decision on which to work with. Now, the Questions:

1. How can I play commercial DVDs on my computer? - Totem *tried* to launch when I put in the DVD, but, Totem crashes upon trying to open even without a file to play. I thought I could try and browse into the folders of the DVD and play the individual files. that was... challenging. I am not sure which files to play. I attempted to play it with VLC. The test DVD was Gladiator, I got the initial screen up to select the sound scheme, and then VLC crashed. Ideally, I would like to be able to use the DVDs as though they were in a DVD player, with the menus and subtitles, etc.

2. Anyone know of a good how-to on ripping DVDs to my HDD?

3. Is there a method for quickly switching users using the system without logging out? (ie pushing one session and its processes into the background, while allowing someone else on to work.) Basically like switching users in Windows XP. I found the New Login option in Gnome, but, when I tried it, the display wigged out and displayed a garbled picture, I could discern nothing on it and finally resorted to rebooting.

4. At some point, I want my system to make use of the 5.1 speaker system/Audigy that it has in it, what can I look at for maybe using the back speakers again?

5. On a purely 'it would be nice' basis - could someone point me at a good place to learn about customizing GAIM - the little chimes sound is getting on my nerves.

6. Just like the last question - could someone point me at a good place to learn about customizing KDE and Gnome - If I can, I would like to customize one of the two to work like Mac OSx, as the other user of the computer is coming from that environment (and I cannot afford a new Mac). For myself... I just like to muck around with the interface.

...erm, yeah, there's the little 'wish-list' as it stands right now. So far, I'm impressed, it has been relatively painless, just these little items.

---

### Post by rfruth on 2006-03-07
Congrats on the switch !  As for the DVD question [https://wiki.ubuntu.com/DVDRippingandEncoding?highlight=%28dvd%29]("https://wiki.ubuntu.com/DVDRippingandEncoding?highlight=%28dvd%29")
quickest way to use a different user is Ctrl-Alt-F1 (or F2 or F3 ...) that will put you at the login screen where someone else can login ... Ctrl-Alt-F7 gets you back ...

---

### Post by Sutekh on 2006-03-07
[QUOTE=rorschach]
1. How can I play commercial DVDs on my computer? - Totem *tried* to launch when I put in the DVD, but, Totem crashes upon trying to open even without a file to play. I thought I could try and browse into the folders of the DVD and play the individual files. that was... challenging. I am not sure which files to play. I attempted to play it with VLC. The test DVD was Gladiator, I got the initial screen up to select the sound scheme, and then VLC crashed. Ideally, I would like to be able to use the DVDs as though they were in a DVD player, with the menus and subtitles, etc.[/QUOTE]
All you need is here

[Ubuntu Wiki - Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats")


[QUOTE=rorscach]
2. Anyone know of a good how-to on ripping DVDs to my HDD?
[/QUOTE][DVD Rip]("http://packages.ubuntu.com/breezy/graphics/dvdrip") is a start

You need to enable the universe repository to install it, using this link

[http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

Then install it from a **Terminal** (In the Applications -> Accessories Menu) with
```
sudo apt-get update
sudo apt-get install dvdrip
```
When prompted for a password use your user's password.


[QUOTE=rorscach]
6. Just like the last question - could someone point me at a good place to learn about customizing KDE and Gnome - If I can, I would like to customize one of the two to work like Mac OSx, as the other user of the computer is coming from that environment (and I cannot afford a new Mac). For myself... I just like to muck around with the interface.[/QUOTE]
Go to the Customisation sub forum, there is HEAPS of stuff you can do!

[http://www.ubuntuforums.org/forumdisplay.php?f=100]("http://www.ubuntuforums.org/forumdisplay.php?f=100")

---

