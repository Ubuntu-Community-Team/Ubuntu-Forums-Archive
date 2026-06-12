---
title: "Suspend and soundcard"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Mular on 2008-01-07
Trying hard to get this suspend / hibernate to work on my desktop PC..

I have a dell dimension 8400 and it has a Soundblaster Audigy card. It comes up as snd_ca0106 or something simular <not infront of computer right now>

I read about using the whitelist in ACPI to remove sound before suspend and put it back after - this doesn't work at all.

Also when I try to use modprobe -r snd_ca0106  it says soundcard is in use.. When i turned off gnome volume control I was able to unload the soundcard.

After I suspend though, I still have no sound. If I try to mess with the volume or play any videos the programs freeze after a couple seconds. Only rebooting brings back the volume. Also says the sound module is in use..

I read about a script you can put in, by this guy Mark S - forget the last name and I can't seem to find the post. But he had a script that you load up in like /etc/init.d/suspend and another in resume. Basically the point was to force all apps using the soundcard to be removed and then unload the module correctly... and bring them all back when you resume. I couldn't get to work though =/

Any ideas here? One of the only things that I can't get working right. It resumes ok from suspend just no sound..! I did all the typical searching / googleing and I am out of suggestions. Thanks!

Mular

**edit** snd-ca0106 thats the module lol found it via google

---

### Post by Mular on 2008-01-07
Found this
[http://bbs.archlinux.org/viewtopic.php?pid=314225]("http://bbs.archlinux.org/viewtopic.php?pid=314225")

This isn't ubuntu but maybe its a simular issue? Can anyone help me a pply this to ubuntu?

---

