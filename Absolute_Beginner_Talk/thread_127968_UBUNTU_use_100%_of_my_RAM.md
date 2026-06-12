---
title: "UBUNTU use 100% of my RAM"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-02-10
I added the system monitor to my panel and i see that UBUNTU use 100% of my memory. Should i be worried about this? I have 512 MB RAM.

---

### Post by frodon on 2006-02-10
Which apps is eating so much RAM : xorg, metacity ?

---

### Post by Blagomir on 2006-02-10
Evolution data server 1.4 - 63.9 MB
evolution alarm notify - 55.8 MB
gnome cups icon - 36.8 MB

and more 7-10 which use 18 to 20 MB

Can i stop some unused processes to free some memory?

WOW my Firefox-bin use 116.9 MB !

---

### Post by theturner on 2006-02-10
Don't worry, Linux memory management is different from Windows. As long as there's free RAM, the kernels stores often-used things from hard-disk in there, so that they load faster. So with caches, RAM usage is always 100%, and this is a good thing, because it makes things load faster. As soon as a running program needs memory, cache is freed, so there's no downside here. What do you need 512 MB of RAM for when it's unused? With resources & cache, it does some good.
The RAM that's really used by running programs is labeled "User Memory" or "in use by programs". It's the *dark green* bar in the system monitor applet.

---

### Post by Blagomir on 2006-02-10
[QUOTE=theturner]What do you need 512 MB of RAM for when it's unused? With resources & cache, it does some good.[/QUOTE]

That's right! Thank you!

---

### Post by theturner on 2006-02-10
[QUOTE=Blagomir]Evolution data server 1.4 - 63.9 MB
evolution alarm notify - 55.8 MB
gnome cups icon - 36.8 MB

and more 7-10 which use 18 to 20 MB

Can i stop some unused processes to free some memory?

WOW my Firefox-bin use 116.9 MB ![/QUOTE]
What you're looking at is virtual memory. The real RAM usage is "shared memory". You'll notice these numbers are substantially lower. If you're interested in this, google "linux memory management", there are many in-depth articles explaining this topic.

---

