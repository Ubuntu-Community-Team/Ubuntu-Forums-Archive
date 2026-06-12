---
title: "mp3"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-02-20
I wanted to listen to some mp3 files, but rhythmbox tells me, that she doesn't know this format "this file is not an audio stream". Can someone tell me which program is appropriate to listen to mp3 files?

---

### Post by purdy hate machine on 2006-02-20
Rhythmbox works fine for MP3 playback.. Have you installed the relevant codec&#8217;s? [Link]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs")

---

### Post by xmastree on 2006-02-20
It'll be a codec problem. I use rhythmbox to listen to mp3s all the time.
What version of ubuntu so you have?
This site:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)
will give you an idea, but it's for 5.04 which isn't the latest version.

---

### Post by gagatz on 2006-02-20
When i start synaptic package manager ubuntu tells me


W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

Do i have to remove "gb.archive.ubuntu.com" from the list of servers? How can i do it?

---

### Post by nik on 2006-02-20
Just comment out the line (put # in front of the line, then the program wont read it).

But first, try removing the country code from the line (gb). Others have reported problems with various country codes. Or just try later, it might be that the server was down or overloaded.

EDIT: I suppose the space between bin and ary is not in the real file? It's not supposed to anyway...

---

