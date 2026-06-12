---
title: "Enlightenment 17 Help!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-06-20
I'm about to reinstall Ubuntu, and I want to know how I can install in either Edgy or Feisty without internet. Is there a place where I can download a .deb or some other file and install it? Please help! :p

---

### Post by raul_ on 2007-06-20
You should search here in the forums for a thread called "How to build E17 from CVS" or something like that, and ask if there is any flag that makes the script download only the sources, and don't build them. After that, i think they get stored in a folder, and you can back it up

---

### Post by shamushand on 2007-06-20
Umm.... What? I found the thread, but I don't get it. :(

---

### Post by raul_ on 2007-06-20
:) ok

That thread is about a script that once you run it, downloads all the source code necessary, and compiles it. That script however, can receive some flags like --update-only (i made this one up) and possibly --download-only 

Hopefully, this saves the source code in a folder, something like /opt/e17/ or something like that. You can save that folder, and then use the Makefile script to build the source code you already have. I'm not sure how to do this though, since i didn't make the script, so you'll have to ask in the thread, or PM thescript author. 

I think this is the easiest way, since there are a lot of .debs to download, if you found a repository, and i'm also not sure of which ones are needed

---

### Post by shamushand on 2007-06-23
Bah, I'll just make this easier and connect it to the internet. ;)

---

