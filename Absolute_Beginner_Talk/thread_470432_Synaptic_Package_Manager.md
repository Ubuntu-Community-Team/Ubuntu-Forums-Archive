---
title: "Synaptic Package Manager"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Buhcy on 2007-06-11
Don't really know what's going on, this is my first time using Ubuntu and all. 
I open up the Package manager and the first thing I see is:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report"

I don't know what to do, and I think to myself, I've been hearing all this stuff about terminal, so I go to my terminal and type it in.

and I get this crap from terminal saying:
"dpkg: requested operation requires superuser privilege"

I don't know what this means. So I sit in my chair and cry a couple of minutes... not really but I get kinda frustrated cause I don't know what to do.

So, I think to myself... There's a large community of people who are willing to help me out with my problem on Ubuntu Forums.

So, I come to you gracious people and ask you the simple question: How do I fix this?

Excuse my n00bness :(

Did, I mention I'm loving Ubuntu? *looks up at his post*, No... well I do!

---

### Post by reidms on 2007-06-11
Hello and welcome to the Ubuntu Forums Buhcy!

all you need to do is run the command as superuser(or root)

you can do this in Ubuntu, per command by typing sudo

So-

```
sudo dpkg --configure -a
```

Hope this helps!

---

### Post by FuturePilot on 2007-06-11
Type that same command with sudo in front of it like so
```
sudo dpkg --configure -a
```
You'll be promted to enter your password. When you do, you won't see anything showing up in the terminal. This is normal. Just keep typing your password then hit enter.

---

### Post by Buhcy on 2007-06-11
I appreciate it much,  thank you o ubuntu masters

---

