---
title: "n00b browser issue"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by wharfrat1490 on 2007-09-14
Solved: Firefox keeps closing itself just after the graphics load.  I installed Epiphany and it did the same thing.  Everything was working fine until I tried to install a plugin.  

The first thing I want to do is uninstall the plugin but I can't even get it to launch in safe mode: I get the message "bus error (core dumped).  I also tried uninstalling Firefox so I could reinstall it, but the system said it would have to uninstall a bunch of other stuff as well.  Not being entirely sure what they all were, I decided to err on the side of good judgment and ask here first.

---

### Post by Maestro23 on 2007-09-14
What was the plugin?

---

### Post by wharfrat1490 on 2007-09-14
...er, Rhapsody.  The music service, not the IRC client.

---

### Post by Dr Small on 2007-09-14
Go to nautilus, press CTRL + H, which shows hidden files and folders. Find .mozilla, and rename it to something else, then try opening Firefox.

Dr Small

---

### Post by wharfrat1490 on 2007-09-14
Ok, I understood all that except what's a nautilus?

---

### Post by Maestro23 on 2007-09-14
> **Dr Small said:**
> Go to nautilus, press CTRL + H, which shows hidden files and folders. Find .mozilla, and rename it to something else, then try opening Firefox.

Dr Small

Hey Doc,

Couldn't he just open a terminal and delete the plugin?

> cd ~/.mozilla/plugins

ls (should see plugins listed)

then

rm filename


---

### Post by Tyke91 on 2007-09-14
nautilus is the file browser

you know when you open up a box and all the files are inside? that is nautilus :)

in windows it's called windows explorer

[[IMG]http://images7.pictiger.com/thumbs/7c/38d4d6ba40199e4eb06f8b98389bc47c.th.jpg[/IMG]](http://server7.pictiger.com/img/638044/picture-hosting/-home-mykola-desktop-screenshot-.php)

nautilus also somewhat controls your desktop. it is responsible for the background and icons. Thus, if you disable nautilus to do something funky to your desktop, you wont have desktop icons untill you re-enable

---

### Post by g2g591 on 2007-09-14
Unless your using Kubuntu, then its called konqueror, and does the same things (except also doubles as a rather clunky web browser)

---

### Post by wharfrat1490 on 2007-09-14
Right.  A quick Googe-ing told me what nautilus was.  I did that & still couldn't find .mozillla.  Tried searching, no good either.

---

### Post by Maestro23 on 2007-09-14
> **wharfrat1490 said:**
> Right.  A quick Googe-ing told me what nautilus was.  I did that & still couldn't find .mozillla.  Tried searching, no good either.

Open a terminal and type what I posted earlier.  Tell me if you see a file: **nprhapengine.so**

---

### Post by wharfrat1490 on 2007-09-14
Yup Maestro, that was it all right.  I removed it and all is well now.  I see quite a few people have trouble with firefox plugins; I guess that one's a no-no.

Thanks everyone for all your help!

---

### Post by Maestro23 on 2007-09-14
> **wharfrat1490 said:**
> Yup Maestro, that was it all right.  I removed it and all is well now.  I see quite a few people have trouble with firefox plugins; I guess that one's a no-no.

Thanks everyone for all your help!

Good deal man.  Glad to help.  Make sure to go back to your 1st post in this thread and mark it SOLVED.  You will have to edit it.

Again, glad we could help ya. :smile:

---

