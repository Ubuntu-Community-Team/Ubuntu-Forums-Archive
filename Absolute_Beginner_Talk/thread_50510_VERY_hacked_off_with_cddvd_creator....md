---
title: "VERY hacked off with cd/dvd creator..."
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-20
I am trying to burn my mp3's to dvd. So far I have had 3 goes. Each time after a 10 minute wait while it builds a cd image (why, oh why, does it think I want this to happen) it comes back and says the files won't fit. I started off at 4.6gb and I am down to 4.2gb now...exactly how much space does ubuntu think I need to keep free on a dvd-r???

---

### Post by Kyral on 2005-07-20
Uhhh. what program are you using?

Try GnomeBaker or K3B

---

### Post by gammyhand on 2005-07-20
[QUOTE=Kyral]Uhhh. what program are you using?

Try GnomeBaker or K3B[/QUOTE]
 gnomebaker crashes like a whiny little bitch if I try to open a directory containing more than 3 files and I have never heard of K3B...either way. What is the point of the CD/DVD creator if it doesn't create anything?

And for the love of mary, is there any way to stop ubuntu making an image of the stuff to be written before writing it?

---

### Post by TravisNewman on 2005-07-20
what program are you using?

---

### Post by gammyhand on 2005-07-20
[QUOTE=panickedthumb]what program are you using?[/QUOTE]
 I am using the CD/DVD creator window that pops up when you insert a blank media. Not through choice. But because the baking tool crashes.

---

### Post by Kyral on 2005-07-20
K3B is the best CD/DVD burning software on Linux, IMO.

sudo apt-get install k3b cdrdao

Its gonna pull in some KDE libs though..

---

### Post by gammyhand on 2005-07-20
[QUOTE=Kyral]K3B is the best CD/DVD burning software on Linux, IMO.

sudo apt-get install k3b cdrdao

Its gonna pull in some KDE libs though..[/QUOTE]
 Will pulling in some KDE libs cause a problem?

---

### Post by Nequeo on 2005-07-20
[QUOTE=gammyhand]Will pulling in some KDE libs cause a problem?[/QUOTE]
 Nope - it'll just increase the size of your download somewhat.

Cheers,

---

### Post by gammyhand on 2005-07-20
[QUOTE=Nequeo]Nope - it'll just increase the size of your download somewhat.

Cheers,[/QUOTE]
 Ah, I can cope with that :) My band is quite broad.

---

### Post by MetalMusicAddict on 2005-07-20
I do agree that K3B is the best right now but if you would like to try Gnomebaker .4 ubuntp has been kind enough to make a .deb. Thread [HERE](http://www.ubuntuforums.org/showthread.php?t=49373). Post #12. Info for Gnomebaker .4 is [HERE](http://biddell.co.uk/gnomebaker.php).

If you have trouble installing .debs here are 2 links:

For [Gnome](http://www.ubuntuforums.org/showthread.php?t=33584&highlight=install+click) .
For [KDE](http://www.ubuntuforums.org/showthread.php?t=33440&highlight=install+click) .

---

### Post by poofyhairguy on 2005-07-20
K3B is the answer. The nautilus burner sucks. Start k3b this way:

gksudo k3b

and be sure to install cdrdao as well

---

### Post by gammyhand on 2005-07-21
[QUOTE=poofyhairguy]K3B is the answer. The nautilus burner sucks. Start k3b this way:

gksudo k3b

and be sure to install cdrdao as well[/QUOTE]
 Thanks guys :)

---

