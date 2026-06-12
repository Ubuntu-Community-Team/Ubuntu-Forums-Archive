---
title: "Guide me through this (installing synthedit through wine)"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by i3ear on 2008-01-19
Synthedit
[http://www.synthedit.com/](http://www.synthedit.com/)

Alright so its non-free, so sue me. But its alot more powerfull than these other modular synths that are for linux.

But anyway, I am teh leenoox n00b and I come right from XP

I have Wine installed from the "Add/Remove program" thing
I have the install file on my desktop

I tried just double clicking the ******, but nothing happened really.

I haven't tried using the Terminal, but only because I couldn't tell a delete command from my *******

So help? What the **** do I do?

---

### Post by smartboyathome on 2008-01-19
Try right clicking on the file on your desktop and selecting "open with wine".

---

### Post by i3ear on 2008-01-19
> **smartboyathome said:**
> Try right clicking on the file on your desktop and selecting "open with wine".

Got nothing

---

### Post by i3ear on 2008-01-19
Bump for some halp

---

### Post by cryptoguru on 2008-01-30
type the following in a terminal

cd ~/Desktop

that should take you to the directory folder.
Now type this:-

msiexec /a XE_SP.msi

That should install it!
(obviously replace XE_SP.msi with the filename you saved it as on your desktop)

---

### Post by cryptoguru on 2008-01-30
hmmm ... it installs fine!

But it crashes and closes after it's opened up.

If it didn't you'll probably still have big problems with audio drivers anyway.

---

