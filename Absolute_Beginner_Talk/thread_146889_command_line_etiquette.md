---
title: "command line etiquette"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by catlett on 2006-03-19
I do not know the proper etiquette for using the command line. For instance, I was given a link to a site that had a step by step guide to install the new Firefox version.This is where I'm confused. The procedure they wrote is
cd ~/.mozilla/firefox/*.default
 mkdir ~/Desktop/ffsettings
 cp bookmarks.html cert8.db cookies.txt formhistory.dat key3.db signons.txt history.dat  mimeTypes.rdf ~/Desktop/ffsettings
Do I hit enter after every line? Most "guides" I come upon have info like this but I have zero command line experience and I never know if I should be hitting enter everytime. Especially when the guide starts with "just cut and paste the command". Is their a guide to the command line. One that doesn't just list commands but gives step by step keystrokes for beginners?  Regards, Catlett

---

### Post by 5-HT on 2006-03-19
Depending on the source, every new line in a walkthrough will normally represent a new command(s), and as such is assuming that you'll be pressing enter at the end of the line.

In terms of the guide you were following, it looks like the guide on installing FF 1.5 from the wiki. That one is definitely formatted so that enter should be pressed at the end of every line.

As to a guide that explicitly describes the keystrokes, I'm not familiar with any and they most likely would be too much of a headache to write (as an extreme, but it depends on the degree).

Once you get used to some of the commands, you'll quickly get the hang of it and everything will start to come together.

A few tidbits:

If you press enter at the wrong time it'll be hard to miss as you'll usually get an error message from the terminal.

Also, if you prematurely press enter, a lot of the time the terminal will wait for you to complete the command and displays a prompt like this (on ubuntu): ```
 > 
``` instead of the normal ```
foo@bar:directory$
``` 

HTH

---

### Post by Sef on 2006-03-19
To compile you need build-essential.  Have you installed it?

sudo apt-get update

sudo apt-get install build-essential

---

### Post by Herman on 2006-03-19
Kryal's excellent '[terminal for beginners]("http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners")' would be a great help. It's a very informative thread, right here in this very subforum.
A good Linux on-line course: [Linux Online - Linux Courses]("http://www.linux.org/lessons/")
Those should be enough to get started with. Some guides do expect you to know quite a lot. :D (Herman)

---

