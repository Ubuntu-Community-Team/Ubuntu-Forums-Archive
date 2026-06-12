---
title: "Date in wrong format"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by PacifistWarMachine on 2007-03-28
I've been using Ubuntu for a few months now and I'm loving it.

One little annoyance has been that panel in the corner that tells you the time and date is in the wrong format. In Australia, the day always goes before the month. Can it be changed so it reads "29 March", instead of "Mar 29".

I know this is a pretty minor problem. Ubuntu's been pretty boring for me, unlike XP there is nothing I need to fix.

---

### Post by h0ax on 2007-03-28
I've just done a quick look through all of the options, and I can't see anything like it.
It's normal for Europe/Americas so maybe that's why it's that way..

Sorry I can't help more, hehe.

---

### Post by laidback on 2007-03-28
Must be possible because that's what I've got. Cannot remember just now how I got it, but I'll post again when I do.

[IMG]http://home/david/desktop/screenshot.png[/IMG]

---

### Post by eclark on 2007-03-28
don't listen to h0ax, he's a n00b himself :]

---

### Post by h0ax on 2007-03-28
Peebo
January 4th, 2007, 06:00 PM

To make a permanent change to your date format system wide edit /etc/environment

Look for the line that starts with
LANG="

For DDMMYYYY change it to

LANG="en_GB.UTF-8"

For the very stupid USA format    MMDDYYYY

LANG="en_US.UTF-8"

There are other formats e.g.      YYYYMMDD

LANG="en_DK.UTF-8"

Hope this helps

](*,)

Got it, enjoy.

---

### Post by oomingmak on 2007-03-28
> **h0ax said:**
> It's normal for Europe/Americas so maybe that's why it's that way...
No it's not.

Europe also uses Day **before **Month (increasing unit size from small to large , dd,mm,yyyy)

In fact I can't think of *any *other Country (apart from the Americas) that uses the bizarre Month first arrangement.

---

### Post by kittyhawk63 on 2007-03-28
[quote=PacifistWarMachine;2368495]I've been using Ubuntu for a few months now and I'm loving it.

In Australia, the day always goes before the month. Can it be changed so it reads "29 March", instead of "Mar 29".

That's b-cuz you are standing on yur head, Mate. lol
Come back on the upside of the equator.
kh

---

### Post by PacifistWarMachine on 2007-03-28
> **h0ax said:**
> 
To make a permanent change to your date format system wide edit /etc/environment

Look for the line that starts with
LANG="

For DDMMYYYY change it to

LANG="en_GB.UTF-8"


Yep, that fixed it.

And thanks for the fast reply. :)

---

