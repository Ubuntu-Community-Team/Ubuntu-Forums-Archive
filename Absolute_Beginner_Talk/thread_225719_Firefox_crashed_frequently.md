---
title: "Firefox crashed frequently"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by satimis on 2006-07-30
Hi folks,

Ubuntu-6.06 amd_64
Browser - Firefox version 1.5.0.3

the blowser crashed frequently.  I got the same problem fixed on FC5_64 but unfortunately I forgot its remendy.

Please advise.  TIA

B.R.
stimis

---

### Post by rowanparker on 2006-07-30
Does it crash when you go on sites with, for instace with heavy graphics?

---

### Post by satimis on 2006-07-30
Hi rowanparker

> Does it crash when you go on sites with, for instace with heavy graphics?No.

Sometimes I left it standing on desktop.  It crashed without my notice.

Tks.

B.R.
satimis

---

### Post by rickmans on 2006-07-30
Did you monitor your javascript console? Sometimes it is an extension which is bothering.

---

### Post by satimis on 2006-07-30
Hi rickmans,

> Did you monitor your javascript console? Sometimes it is an extension which is bothering.
I think no javascript was running.  Actually I was not browsing.  Firefox only stood on the desktop.  Suddenly it crashed disappearing without a sign.

Tks

Remark: It just crashed on hitting [Submit]

B.R.
satimis

---

### Post by rickmans on 2006-07-30
> **satimis said:**
> Hi rickmans,


I think no javascript was running.  Actually I was not browsing.  Firefox only stood on the desktop.  Suddenly it crashed disappearing without a sign.

Tks

B.R.
satimis As far as I know all plugins of FF use some bit of javascript. I used to have an issue with e.g. the google toolbar which created an javascript every second in my console. The result was that my firefox crashed. Since I deinstalled that particular extension I have had no crashes anymore.

So it does not depends on the page you are visiting but on th extention you installed.

---

### Post by dmizer on 2006-07-30
find out why it's crashing first of all.  instead of running firefox from the link in applications, open it from the terminal by typing "firefox" and leave the terminal open.

then, when it crashes, post the output of the crash message.

---

### Post by satimis on 2006-07-30
Hi dmizer

> open it from the terminal by typing "firefox" and leave the terminal open.

then, when it crashes, post the output of the crash message.
~$ firefox

(firefox-bin:10200): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

What did it indicate?  TIA

B.R.
satimis

---

### Post by dmizer on 2006-07-30
looks like a language problem.

i did a bit of a google search for "firefox, Locale not supported by C library" and there's lots of hits.

i'll keep looking, but i haven't found anything specific yet.

---

