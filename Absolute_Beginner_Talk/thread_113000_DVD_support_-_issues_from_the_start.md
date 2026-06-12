---
title: "DVD support - issues from the start"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by buckley on 2006-01-05
Hello everyone, 

I am very new to linux and Ubuntu in general, but i learn quick!

I am having alot of trouble using the ubuntuguide to install DVD support.. I need to be able to play, rip, copy, and burn DVD's ASAP - cant keep netflix waiting :o   I am using 5.10 Breezy and i know the guide is only tested with 5.04, i dont know if these issues will be resolved or not.

I have done the extra repositories by uncommenting and adding the backports url's to the list, and i go down to DVD support, and the command is:

sudo apt-get install libdvdcss2

and i get a LONG list of errors, all seeming to be network issues on ther server side... have i missed something?  or are there mirrors to these sites that i could try?

Thank you all, 

~buckley

---

### Post by gitfiddler on 2006-01-05
I suggest installing Automatix, see information here:

[http://www.ubuntuforums.org/showthread.php?t=80295]("http://www.ubuntuforums.org/showthread.php?t=80295")

Besides the DVD issues, it makes short work of many other configuration problems for a new install.

---

### Post by Zelut on 2006-01-05
Ok.  This is my suggestion.  For all the DVD, mp3, etc needs that I have I created a custom sources.list where I know I can find everything.  Try [source-o-matic]("http://www.ubuntulinux.nl")  I'd suggest the ubuntu stuff, backports, cipherphunk & PLF..

This'll make sure you have dvd support and then you can go on to the DVD copying (I use [xdvdshrink]("http://xdvdshrink.sf.net"), but it doesn't get EVERY DVD for some reason)

---

### Post by buckley on 2006-01-05
thanks for the suggestions, ill get on them after dinner. :D

---

### Post by Joeb on 2006-01-05
[QUOTE=kuyaedz]Ok.  This is my suggestion.  For all the DVD, mp3, etc needs that I have I created a custom sources.list where I know I can find everything.  Try [source-o-matic]("http://www.ubuntulinux.nl")  I'd suggest the ubuntu stuff, backports, cipherphunk & PLF..

This'll make sure you have dvd support and then you can go on to the DVD copying (I use [xdvdshrink]("http://xdvdshrink.sf.net"), but it doesn't get EVERY DVD for some reason)[/QUOTE]


The link for source-o-matic should be [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by buckley on 2006-01-05
wow...

thanks guys.  the sourc-o-matic worked wonders, and not just for dvd support.  i was having trouble with other things, and this worked out really well.

I tried playing a DVD using xine, and its really choppy.  is this becuase im screwed with an ATI card?  i havent installed the fglrx driver b/c i gave up after an hour of frustration. 

i read somewhere here that i use alien to convert it from an rpm to a deb, but i couldnt get the it to recognize the file... im pretty sure that i was in the right directory and that my syntax was correct.  

I dont know, but im really excited about this!

---

### Post by Zelut on 2006-01-05
nah, choppy video play is usually due to DMA not being turned on.  Give this a try and you should be set on that..

[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

that should fix you right up.

---

### Post by buckley on 2006-01-06
[QUOTE=kuyaedz]nah, choppy video play is usually due to DMA not being turned on.  Give this a try and you should be set on that..

[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

that should fix you right up.[/QUOTE]
Thank you for this, i should have seen this, ive been looking at the guide enough lately...  It has improved the playback quality but it's still choppy at times.

Now, someone above mentioned automatix?  i have been trying and trying again all day to get the first line of code to work, and i always get a "permission denied" error when it tries to download the deb.  Anyone know wtf is up with that?

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=buckley]
Now, someone above mentioned automatix?  i have been trying and trying again all day to get the first line of code to work, and i always get a "permission denied" error when it tries to download the deb.  Anyone know wtf is up with that?[/QUOTE]

The first line is just saving Automatix to your hard drive. Click on this link and download to your home folder and skip to the second line:

[http://beerorkid.com/automatix/automatix-ubuntu_4.3-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.3-1_i386.deb)

---

### Post by Joeb on 2006-01-06
[QUOTE=buckley]Thank you for this, i should have seen this, ive been looking at the guide enough lately...  It has improved the playback quality but it's still choppy at times.
[/QUOTE]

You're DVD drive wouldn't be on the same IDE channel as your hard drive, would it?  If so, IDE can only talk to one drive at a time and if your playing a DVD and something needs to hit the hard drive, it will pause.  Same goes for burning CDs and DVDs.  They burner should be on a different IDE channel than the hard drive that contains the image file to be burned.

If your drive is on a separate channel, you might want to see what else you have running.  If you have something eating up cpu cycles, then that could produce choppy playback, too.

Joeb

---

### Post by handy on 2006-01-06
I just reinstalled my system on 32bit, the firefox 1.5 install guide trashed firefox, so I used it as an excuse to see what 32bit Breezy was like.

Anyway I used Automatix, it does work better in 32bit, installed Wine, for only one application, DVD Shrink, which works beautifully :KS :KS :KS 

Highly recomended, theres next to nothing it can't handle.

handy

---

