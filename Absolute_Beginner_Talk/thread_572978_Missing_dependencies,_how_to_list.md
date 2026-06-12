---
title: "Missing dependencies, how to list?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by obsidience on 2007-10-11
Hey guys and gals,

I'm running ./configure on the latest ajuntu.  I'm finding a lot of missing dependencies so I run it, find one then go to synaptic and install it.  Rinse and repeat, rinse and repeat etc.

Is there a way to run ./configure and have it list all failures all at once?  I  searched the forums and the ./configure --help and found nothing.

Best regards,

Obsidience

---

### Post by RomeReactor on 2007-10-11
Hi. I couldn't find much information regarding Ajuntu. Is it an IDE for C or C++? If so, you might want to try [Anjuta]("http://en.wikipedia.org/wiki/Anjuta"); it's in the repositories, so you can find it through Synaptic. Otherwise, try searching the page you downloaded Ajuntu from, and see if they specify the dependencies. Have you tried finding a list of dependencies in the readme's included with your download?

---

### Post by expatCM on 2007-10-11
I have found in many programs that a readme is included with the directory when you unpack.  Often the readme will tell you how to download most of the dependencies through APT as one or two events.

---

### Post by FranMichaels on 2007-10-11
Hello there,

It might be possible, but you'd need a nice script to filter out what's missing, probably involving sed and grep and other neat stuff.

If the app is anjuta, and you are just building a newer one than Ubuntu provides, if the dependencies haven't changed much:

```
sudo apt-get build-dep anjuta
```

Will install everything you need to build it :KS

---

### Post by obsidience on 2007-10-11
Yeah I was trying to compile the latest Anjuta sorry for the confusion.  I'm using Gutsy and the Anjuta from Synaptic has an error that crashes the IDE when viewing a glade file.

So I thought I'd try to build the latest stable version from source.  What I had wanted was a way to ./configure and have it list out all errors including missing dependencies.  FranMichael's response seems to be the only optionce.

I'm actually a .NET programmer anxious to start developing in Linux and help the cause.  I might look into a way to do this to help simplify source builds.

Best regards,

Obsidience

---

