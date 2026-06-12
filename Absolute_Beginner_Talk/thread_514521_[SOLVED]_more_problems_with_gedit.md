---
title: "[SOLVED] more problems with gedit"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-07-31
in opening sudo gedit I can't get the highlighting preferences to stay on php. When I open regular gedit and go to preferences>syntax highlighting php is selected, with sudo gedit, its html. I know this is a small thing but it's frusterating and I want to know why...

---

### Post by aysiu on 2007-07-31
Open a [terminal](http://www.psychocats.net/ubuntu/terminal) and type ```
gedit
``` Highlight the error messages that appear and paste them into this thread.

---

### Post by woodsonoversoul on 2007-07-31
No error messages. Just trying to understand why the sudo version of gedit is different than the regular version and why sudo's highlighting is inconsistent

---

### Post by woodsonoversoul on 2007-07-31
Actually, it might be giving me a pop-up window saying "mount: block device /dev/fd0 is write-protected, mounting read-only

mount: i could not determine the filesystem type, and none was specified
"

However I'm not sure those two things are directly related

---

### Post by nitro_n2o on 2007-07-31
i have no idea... but use Vim :) and save yourself all these troubles

---

### Post by aysiu on 2007-07-31
Don't do *sudo gedit*. It may be too late already, but *sudo* should not be used with graphical applications. ```
gksudo gedit
``` is the proper way to invoke the command. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by woodsonoversoul on 2007-07-31
Alright I closed out gedit and reopened it with gksudo and I have the same problem

---

### Post by aysiu on 2007-07-31
I'm trying to understand what the problem is.

So you have syntax highlighting set to default to PHP ordinarily, but when you open up the same file with root privileges, the highlighting is HTML? Is that the problem?

---

### Post by woodsonoversoul on 2007-07-31
yes, and I can't get it to stay on what I need it to (php). So I end up with a lot of plain text or text text with jumbled colors, which is very confusing when you're trying to learn

---

### Post by aysiu on 2007-07-31
Hm. I don't know what's wrong. I just tested it out with a .php file in both *gedit* and *gksudo gedit* and, in both cases, Gedit guessed the right syntax highlighting.

You're definitely working with the same file in both cases?

---

### Post by woodsonoversoul on 2007-07-31
No I'm working with a different file. I tried opening the same file I usualy open with regular gedit and is saved with the php highlighting preference under gksudo gedit and it switched it to html too.

---

### Post by woodsonoversoul on 2007-07-31
is there maybe some config file that I could alter to make php the default highlighting?

---

### Post by aysiu on 2007-07-31
I think Gedit tries to guess the syntax highlighting and then you can override that guess through the preferences.

---

### Post by woodsonoversoul on 2007-07-31
Well it guesses wrong and won't let me change it

---

### Post by woodsonoversoul on 2007-07-31
anyone else have any ideas?

---

### Post by woodsonoversoul on 2007-07-31
Just solved it! Go to View and change the highlight mode from there! Awesome. Problem solved

---

