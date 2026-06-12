---
title: "new to ubuntu"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by mthemapc on 2008-01-26
i just installed ubuntu on my desktop and ran it and it went to a command line interface that looks like DOS, i was not expecting this, i was expecting the desktop version or whatever, can someone tell me how i can get out of the command line stuff and into the stuff that i can actually use(desktop version or GNOME i think its called)

thanks a lot for a beginner to ubuntu and linux =)

---

### Post by jamoo1980 on 2008-01-26
Did you install from CD, and if so are you sure you installed the Desktop edition and not Server? The server edition boots into a command prompt, but the desktop edition should boot straight into a graphical login prompt, then to the Gnome desktop...

---

### Post by JoshuaRL on 2008-01-26
Yeah, I agree.  What exact type of Ubuntu did you install?  And can you remember what choice at the CD menu you chose?

---

### Post by seventhc on 2008-01-26
if it is the server, can he just 
sudo apt-get install gnome-desktop  ???

---

### Post by JoshuaRL on 2008-01-26
> **seventhc said:**
> if it is the server, can he just 
sudo apt-get install gnome-desktop  ???

Kind of.  But it's just a little bit different.

Either try:

```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```

Or if he's in the recovery console and it has him as root he should just take off the "sudo."

---

### Post by seventhc on 2008-01-27
> **JoshuaRL said:**
> Kind of.  But it's just a little bit different.

Either try:

```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```Or if he's in the recovery console and it has him as root he should just take off the "sudo."
ahh, I should have double checked then ;)
thanks for the correction though. :)

---

