---
title: "Removing KDE"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by V-600 on 2006-12-22
I run Ubuntu 6.10 (with gnome)

I thought i'd try KDE for a change so opened synaptic and selected Kubuntu-Desktop. This installed KDE and all associated files (187 packages) as well as providing the option to swap between KDE and Gnome at start up.

However it has the unfortunate consequence of leaving a rather untidy menu system (in both gnome and kde) where i can see and run apps from both desktop environments.

I would like to know how to remove the recently installed KDE addition (as it was meant as a bit of fun, not to disrupt my main version - gnome) without removing each (of 187) package one at a time. To install i simply selected Kubuntu-desktop and it selected everything else. Is there any equivalent easy way to remove it.

Many thanks.

---

### Post by meng on 2006-12-22
Not as easy as that, but still fairly easy:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
It sounds like you'll need to use the long command. If you install software with aptitude rather than apt-get (or package manager) then you can undo the installation more comprehensively.

---

### Post by Pobega on 2006-12-22
Try this, I used this when I had a splashscreen problem:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

**Edit:** He beat me.

---

### Post by bodhi.zazen on 2006-12-22
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by meng on 2006-12-22
It's like a barbershop quartet!

---

### Post by aysiu on 2006-12-22
> **meng said:**
> It's like a barbershop quartet!
Or a trio...

---

### Post by V-600 on 2006-12-22
Thanks for that. I hope I don't need to do that three times. lol

Will also use that aptitude thing in future (when i find out what it is)

---

### Post by aysiu on 2006-12-22
> **V-600 said:**
> Thanks for that. I hope I don't need to do that three times. lol

Will also use that aptitude thing in future (when i find out what it is)
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by bodhi.zazen on 2006-12-22
LOL :lol:

Aptitude: [http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

---

### Post by V-600 on 2006-12-22
Thanks again. one further thing if y'all would be so kind

Now i know how to remove KDE if things go wrong i will prob leave in and have a play about with it. However Will changes i make In either Gnome or KDE affect the other i.e. if i change something like network settings in KDE will it affect the same settings in Gnome or are the two completely seperate.

I did notice that firefox remembers history in both, but that is not a system program (is it?)

---

### Post by aysiu on 2006-12-22
> **V-600 said:**
> Thanks again. one further thing if y'all would be so kind

Now i know how to remove KDE if things go wrong i will prob leave in and have a play about with it. However Will changes i make In either Gnome or KDE affect the other i.e. if i change something like network settings in KDE will it affect the same settings in Gnome or are the two completely seperate.

I did notice that firefox remembers history in both, but that is not a system program (is it?)
I think your intuition is correct--if they're just two different interfaces for the same system-wide process, the process should be affected regardless of whether you're using KDE or you're using Gnome. If it is a specific application with its own settings, only that application will be affected.

---

