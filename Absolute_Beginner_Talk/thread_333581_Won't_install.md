---
title: "Won't install"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by reabralop on 2007-01-07
I am trying to install this on another computer and the main Ubuntu screen appears but when I select it it then reboots the computer and starts over. I noticed that there is a brief screen that says "unknown interrupt or failure..." before it restarts. I didn't notice this on the other computers. The HD was formatted and the computer takes the MS restore disk just fine but not the Ubuntu disk. It's a late model Compaq. How can I get past this point?

Thank you

---

### Post by mahy on 2007-01-07
have you tried the alternate installation cd as well? it's well worth trying...

---

### Post by reabralop on 2007-01-07
Alternate CD?

---

### Post by reabralop on 2007-01-07
The disk I used works fine on two other machines but just reboots the third. (If that matters)

---

### Post by kebes on 2007-01-07
Having the exact specs of the computer (and the Ubuntu version you're trying to install) would help.

mahy's suggestion of using the alternate CD is a good one--often it will help in these kinds of situations. Another thing to try is to pass "boot parameters" to kernel before boot. At the install screen, before hitting enter for install, press the key for "other options" (I think it's F6). Then add the boot flags and see if it loads up properly.

In particular, perhaps the "irqpoll" flag will fix whatever is stopping the boot from working (just a guess). There are tons of other boot flags, but figuring out what to use depends on hardware and errors. You can see the error messages by pressing Ctrl+Alt+F1 (and Ctrl+Alt+F2, etc.). Write down any error messages you see: they will help to figure out what's going on.

---

### Post by kebes on 2007-01-07
> **reabralop said:**
> Alternate CD?

The alternate CD is an "alternate" installer that doesn't have the graphical Live CD session (text-based install). It is "simpler" so it works better on quirky hardware. The install you get out of it is full-featured and has a GUI, though, so don't worry about that.


See here:
[http://mirror.phy.olemiss.edu/mirror/ubuntu/edgy/](http://mirror.phy.olemiss.edu/mirror/ubuntu/edgy/)

...and go down to the bottom. You can download the CD image there.

---

### Post by reabralop on 2007-01-13
Thanks for following up but I can't seem to get that link to work. I don't know if the site is down or what. Is there another way to get that version? I will also look around the forums to see if there is another site available.

---

### Post by rai4shu2 on 2007-01-13
Try one of the links on this page:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

---

### Post by kebes on 2007-01-13
> **reabralop said:**
> Thanks for following up but I can't seem to get that link to work. I don't know if the site is down or what. Is there another way to get that version? I will also look around the forums to see if there is another site available.

The link I gave was just one one possible mirror. As rai4shu2 says, go to the general download page:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Pick a mirror close to you, but instead of picking "CD image for desktop", select "Other installation options". You should see a link for "Alternate install CD" and you can select the one appropriate for your computer (probably "PC x86").

---

### Post by reabralop on 2007-01-13
Thanks, I'll try that and let you know if it's successful.

---

