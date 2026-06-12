---
title: "Headphone Jack Issues on Macbook"
date: 2008-11-17
forum: Apple Hardware Users
---

### Post by wecannotbesaved on 2008-11-17
I've had 2 installations of ubuntu, and they both have the same issue.  For whatever reason there is no output through the headphone jack.  If I unplug the headphones then everything is fine and sound plays through the built in speakers.  I know the headphone jack is not broken for it still works under OS X.  I've tried the sound fixes on the wiki to no avail.  I'm using Ibex on the original macbook 1.1

---

### Post by untmdsprt on 2009-05-30
This is still an issue. I have a Macbook 2.1, with Ubuntu 9.04. I have to unplug my external speakers just to be able to hear any sound. Can anyone find out what the problem is, and how to fix it?

---

### Post by regebro on 2009-05-30
You might want to try do download the latest version of ALSA and compile it. There are fixes in Trunk for 4,1 Macbooks, and since they are also using Intel HDA those fixes may very well be valid for Macbooks 2,1 as well.

---

### Post by untmdsprt on 2009-05-30
> **regebro said:**
> You might want to try do download the latest version of ALSA and compile it. There are fixes in Trunk for 4,1 Macbooks, and since they are also using Intel HDA those fixes may very well be valid for Macbooks 2,1 as well.
 
I'll try that if you can point me in the right direction of where to find this trunk and compile instructions for it. I'm still a novice when it comes to using the terminal, etc.
 
Thanks for your reply!!!

---

### Post by tiagobt on 2009-05-31
The headphone jack works for me as long as the surround slider is loud enough (Kubuntu 9.04 + MacBook 2,1).

---

### Post by untmdsprt on 2009-05-31
> **tiagobt said:**
> The headphone jack works for me as long as the surround slider is loud enough (Kubuntu 9.04 + MacBook 2,1).

That worked for me too under Gnome. I went into the prefs and turned on all sliders until I found the one for the headphone jack. I believe it was the surround sound one.

---

### Post by snewton2 on 2009-07-01
yeah taking surround off mute using volume preferences worked for me.

---

