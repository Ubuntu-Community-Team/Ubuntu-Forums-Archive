---
title: "Removing Home Icon form Desktop"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-11-02
I know it's might be just a small annoyance but it's doing my head in. 

Currently I have on my desktop an icon that opens my Home directory. How it came there? Well, I think when I was fooling around with Gdesklets, I made it on my desktop in the hope I could drag it to that launcher. I tried many things that day. The icon has been there since then. AND I CAN'T GET RID OF IT. 

This is what I have tried up to now:

Right Click - Move to Garbage Bin (Greyed out)
Selecting - Delete (and Shift+Delete) Doesn't work
Dragging it to the Garbage bin Doesn't Work
Via File Manager - Manipulating it there Doesn't Work
Even after turning on Hidden Files
Via Command Line - /home/belgatom/Desktop It's not there
Via Command Line - /root/Desktop It's not there
No idea how to make hidden files visible when I use the ls command. 

I really am a Zen kinda person so I want to get my desktop empty and sereen. Help please...

---

### Post by theicyj on 2006-11-02
Go to Applications -> System Tools -> Configuration Editor -> apps -> nautilus -> desktop -> and uncheck home_icon_visible

---

### Post by lazyart on 2006-11-02
Run gconf-editor

Drill down to /apps/nautilus/desktop and have your way with it.  It feels a lot like Windows registry.

---

### Post by Belgatom on 2006-11-02
Thank, peace and serenity have taking over again. 

May the seeds of your loins be fruitful in the belly of your women.

---

### Post by Lord Illidan on 2006-11-02
> **Belgatom said:**
> Thank, peace and serenity have taking over again. 

May the seeds of your loins be fruitful in the belly of your women.

Lovely parting comment!

---

### Post by motang on 2006-11-05
> **theicyj said:**
> Go to Applications -> System Tools -> Configuration Editor -> apps -> nautilus -> desktop -> and uncheck home_icon_visible

Thanks it worked great.

---

