---
title: "config.log"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Station on 2008-01-18
Whats the best way to view config.log in ubuntu? or just the best way?

---

### Post by kellemes on 2008-01-18
What's config.log??

---

### Post by Station on 2008-01-18
> **kellemes said:**
> What's config.log??

I have to configure apache 2.2.6 to my computer. It does not want to configure to my computer. I was wondering what program to use to read the config.log, so I can track down the issue.  G edit seems to work fine. 

Now I have to figure out how to make apache configure to my 64 bit computer...

configure:3119: result: x86_64-unknown-linux-gnu

I found a patch for 64 bit platforms, but having troubles making that work properly.
I have been told that this is the run command
patch -p1 < apr-util_2.2.6.patch

but I get this

patch:*** strip count 1 is not a number

So at the moment I am kinda stuck

---

