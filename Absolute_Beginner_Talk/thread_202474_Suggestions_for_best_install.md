---
title: "Suggestions for best install?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by ButteBlues on 2006-06-23
I have an old PC that originally came loaded with Windows 98. I want to format it and make it into a purely Linux machine.

I was thinking that the Xubuntu Alternative installer would be best.

I'm looking for some feedback/comments regarding this.

---

### Post by aysiu on 2006-06-23
Yes, Xubuntu alternate would probably be your best bet.

---

### Post by bruce89 on 2006-06-23
If you have less than 128MB, use the alternate, if you have more than that, then you can use the Desktop CD.

---

### Post by ButteBlues on 2006-06-23
[QUOTE=bruce89]If you have less than 128MB, use the alternate, if you have more than that, then you can use the Desktop CD.[/QUOTE]
It's got a 400 MHz PII processor, and 64 MB RAM.

I'm downloading the alternate installer. :)

---

### Post by aysiu on 2006-06-23
Xubuntu might run a little slowly on 64 MB of RAM.

Consider doing this instead--select the server install and then when you log in, type ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
sudo /etc/init.d/gdm start
```

---

### Post by ButteBlues on 2006-06-23
[QUOTE=aysiu]Xubuntu might run a little slowly on 64 MB of RAM.

Consider doing this instead--select the server install and then when you log in, type ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
sudo /etc/init.d/gdm start
```[/QUOTE]
That old PC isn't able to connect through my current internet connection (its USB ports are dead and it lacks an ethernet connection).

I'm alright with it running a little slowly though - considering Windows 98 flatout runs pretty 'meh' on it in general.

I intend to use that old PC mainly for word processing and such though, so it's not like I'll be doing too many memory intensive things.

---

### Post by aysiu on 2006-06-23
Maybe consider getting Damn Small Linux, which runs quite fast on 64 MB of RAM and uses Fluxbox instead of XFCE.

---

### Post by ButteBlues on 2006-06-23
[QUOTE=aysiu]Maybe consider getting Damn Small Linux, which runs quite fast on 64 MB of RAM and uses Fluxbox instead of XFCE.[/QUOTE]
Sure thing.

Since Xubuntu is about half-downloaded, I'll give it a run on the old PC first, and if it's pretty laggy or anything, I'll give DSL a shot. :)

---

### Post by ButteBlues on 2006-06-23
[QUOTE=rwscold]I love Ubuntu! ... That is all[/QUOTE]

I apologize for the double post.

At any rate, my monitor is stuck on a 600*800 resolution. When I insert the disc that came with this particular monitor, however, whenever I try to run an .exe, it says I lack the necessary permissions to do so.

Help? :)

---

### Post by aysiu on 2006-06-23
Well a Windows driver isn't going to help you, unfortunately.

[One of these solutions](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) may help you, though.

---

