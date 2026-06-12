---
title: "Rar"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by simukas on 2006-08-12
What is the easiset wat to get my rar open.. i can't do it with 7z.

---

### Post by MikeMLP on 2006-08-12
If you are using Ubuntu (rather than Kubuntu or Xubuntu), Try right clicking on the archive and selecting "Open with Archive Manager" and then clicking Extract.  I believe .rar support is built right in, however if it is not, you may need to install some packages, and I'll have to do a little digging to find out which ones, but first try what I suggested above, and let me know if it works or not.

---

### Post by simukas on 2006-08-12
that didn't work.. can u say packages that i should use

---

### Post by _simon_ on 2006-08-12
Download the latest rar [http://rarlabs.com/rar/rarlinux-3.6.b6.tar.gz](http://rarlabs.com/rar/rarlinux-3.6.b6.tar.gz)

Extract the contents.

Then copy the file "rar" to /usr/bin

Note - you ONLY need that one file.

You will now find that the archive manager can open rar files :)

---

### Post by MikeMLP on 2006-08-12
I believe I achieved .rar support by using the Automatix script.  I would try that if you havn't already, as it installs the necessary packages to do other things, like play mp3s.  

Alternatively, you could try this:
I opened up Synaptic Package Manager, and searched for "rar" and I found the package "rar" was installed (version 3.30-2ubuntu2).  If it isn't showing up, make sure you have the universe and multiverse repositories enabled (settings, repositories, edit the "dapper 6.06 LTS" entry).  

The package description says, "This program is shareware and you must register it after 40 days of use."  Although this restriction seems a bit bothersome, it is, nonetheless the package I have installed, and I am easily able to "unrar" using the method I talked about in my last post.  Try installing that and see if it works for you.

---

### Post by Pawka on 2006-08-12
Just type in terminal:

[FONT="Courier New"]**sudo apg-get install rar**[/FONT]

But looks like default sources.list doesn't have rar package. I got it after Automatix sources.list update.

---

