---
title: "ripping speed"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by luckyd on 2007-06-02
Why does it take 30 minutes to rip a 23 minute cd in sound juicer? I have the same problem in Rhythmbox, and in both of them the maximum rip speed is 1.6X. Is this just something that all linux users have to live with, or is their a way to speed up the process?

This is a repost, since I think it might be a problem with my iBook. It has a Mashita CW-8123 cd reading and burning, plus dvd reading drive.

---

### Post by MetalMusicAddict on 2007-06-02
Does Sound Juicer use cd paranoia? That would slow things down.

---

### Post by jackocleebrown on 2007-06-02
Hi,

I think that this is a problem with cdparanoia.  Soundjuicer uses a library called cdparanoia to read the data from the CD. cdparanoia, as the name suggests, is really paranoid about getting the correct info from the CD - it will read sectors of the CD several times to make sure that it gets exactly the correct information from the disc. This is great if that is what you want but if you would prefer to have faster rips and not worry about the occasional error then I think you can turn this feature off by doing this:

1) launch a terminal (applications - accessories - terminal)
2) type "gconf-editor" and press enter
3) on the tree on the left navigate to "apps"-"soundjuicer"
4) find the entry in the list on the right named "paranoia" & adjust the setting by right clicking on it and choosing edit key. It looks like setting it to "0" completely disables paranoia.

I hope that this fixes your problem!

jack.

---

### Post by stmiller on 2007-06-03
Hey try using grip. It's great!

sudo apt-get install grip

---

