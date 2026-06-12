---
title: "gdm not found?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by chriscrutch on 2006-10-16
I installed Kubuntu (6.06.1) with the alternative install CD and started it up for the first time.  After all the startup functions began, and X started (or didn't?), my monitor went into powersave mode and I had to ctrl-alt-f1 to login in text mode.  So, I did:

sudo dpkg-reconfigure -phigh xserver-xorg

Then I went to do:

sudo /etc/init.d/gdm restart

and I got a message saying that gdm was not found.

Pardon the noob.  What do I do now?  Thanks in advance.

--chriscrutch

---

### Post by jordanmthomas on 2006-10-16
The alternate CD does not use X or gdm, it is a text-based installer.

Note that it will install X and gdm, just like the normal LiveCD, but the installer is entirely text-based.

Hope this clarifies things

---

### Post by chriscrutch on 2006-10-16
> **jordanmthomas said:**
> The alternate CD does not use X or gdm, it is a text-based installer.

Note that it will install X and gdm, just like the normal LiveCD, but the installer is entirely text-based.

Hope this clarifies things

I realize the installer is text-based.  I downloaded the alternative CD because I had the same trouble using the Live CD that I'm having now:  as soon as X starts, I lose video.  It's like I've unplugged the monitor cable.  It goes into powersave mode like it does when it has no input.

Using the alternative CD, I got Kubuntu installed.  Now, trying to boot into it, I have troubles.  One of those troubles is that gdm is apparently either not installed or not functioning properly, as the "command not found" error shows.

--chriscrutch

---

### Post by jordanmthomas on 2006-10-16
I see.  I didn't know you had finished installing.
Kubuntu uses kdm instead of gdm.  To start it, run
```
sudo kdm
```
To stop it
```
sudo /etc/init.d/kdm stop
```

---

### Post by chriscrutch on 2006-10-17
Thank you.  All is well now.

Now, onward to get my wireless adapter working....

--chriscrutch

---

