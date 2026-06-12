---
title: "Limewire and Wine"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by TaiQui on 2007-10-08
I just installed limewire on my Ubuntu 7.10 it opens fine but once its up its just a big white screen.


Also, for Wine, I would really like to play a game called maplestory, anyone who plays this, do you know if big programs like it will work in wine?

---

### Post by dpar on 2007-10-08
I know this doesn't answer your Limewire question, but have you tried Frostwire?

---

### Post by TaiQui on 2007-10-08
Nah, but it uses the same dll's and stuff pretty much, its just a rip off of limewire, maybe more popular, so I'd just have the same problem

---

### Post by jfinkels on 2007-10-08
> **TaiQui said:**
> Nah, but it uses the same dll's and stuff pretty much, its just a rip off of limewire, maybe more popular, so I'd just have the same problem

Frostwire runs natively on Linux, you should give this a try before trying to use the wine application layer to run a program native to Windows. [http://www.frostwire.com](http://www.frostwire.com)

---

### Post by TaiQui on 2007-10-08
Ah, ok. And with wine, I didn't mean that. I just meant I wanted to know if big files, maplestory is 1.5 GB would work on wine.

---

### Post by Steveway on 2007-10-08
Yes even big programs run with wine.
But afaik maplestory doesn't work.
You should check wine's webpage first before posting.
[www.winehq.org](www.winehq.org)
It has a Garbage rating, meaning it doesn't work, it seems to not work because this thing gameguard is not avaiable or workable.

---

### Post by TaiQui on 2007-10-08
Aww, ok.

And, Awesome! Frostwire works perfectly!

---

### Post by Malibu Illusion on 2007-10-08
> **jfinkels said:**
> Frostwire runs natively on Linux, you should give this a try before trying to use the wine application layer to run a program native to Windows. [http://www.frostwire.com](http://www.frostwire.com)

Limewire isn't "native" to anything.  It's written in Java.  Java, as a language, was developed for its platform independence; Java code is executed within the JavaVM which is part of the Java Run Time Environment.  JREs are available for both Windows and Linux.

I don't think the OP was trying to run LimeWire with WINE anyway.  If he was though, there's no need.  It'll run in Linux using the installed JRE just fine.

---

### Post by dpar on 2007-10-08
> **Malibu Illusion said:**
> Limewire isn't "native" to anything.  It's written in Java.  Java, as a language, was developed for its platform independence; Java code is executed within the JavaVM which is part of the Java Run Time Environment.  JREs are available for both Windows and Linux.

I don't think the OP was trying to run LimeWire with WINE anyway.  If he was though, there's no need.  It'll run in Linux using the installed JRE just fine.

You're right! I didn't know that, but now I do.....thanks

---

### Post by macogw on 2007-10-08
If LimeWire or FrostWire opens as a white box, it's because you have Desktop Effects enabled.  Java's slightly broken.  You need to put ```
# Make Java and Beryl play nice
export AWT_TOOLKIT=MToolkit

``` in your ~/.bashrc

---

### Post by jfinkels on 2007-10-08
> **Malibu Illusion said:**
> Limewire isn't "native" to anything.  It's written in Java.  Java, as a language, was developed for its platform independence; Java code is executed within the JavaVM which is part of the Java Run Time Environment.  JREs are available for both Windows and Linux.

You're right of course, I'm so sorry! Momentary lapse of sanity.

---

### Post by steveneddy on 2007-10-08
Limewire sometimes will show a blank screen when starting up and Beryl/Compiz-Fusion/Compiz turned on.

---

