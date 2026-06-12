---
title: "Touchpad in Intrepid"
date: 2008-11-01
forum: Apple Hardware Users
---

### Post by spencercarran on 2008-11-01
Using a Macboook 3,1 Santa Rosa with Ubuntu 8.10.

I followed the instructions at [https://wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa") to try to get double-fingered scrolling and right-clicking but to no avail. 

I typed "sudo gedit /etc/hal/fdi/policy/appletouch.fdi" and then copy-and-pasted the text in their box into that file, then logged out and in but still do not have two finger scrolling or two-tap right click. 

Any suggestions? Did I manage to do something wrong here?

---

### Post by xerosis on 2008-11-01
Logging out and and in won't have restarted X so you'll need to restart it with ctrl+alt+backspace.

---

### Post by parkerhiggins on 2008-11-01
I've followed the same steps as spencercarran, and I'm having the same problem.  After creating that file (and adding the relevant text), I've restarted x, but I still have no two-finger scroll or anything.

---

### Post by kosumi68 on 2008-11-01
Do you have old settings in /etc/X11/xorg.conf? Those will interfere in a bad way with the fdi settings.

---

### Post by spencercarran on 2008-11-01
> **kosumi68 said:**
> Do you have old settings in /etc/X11/xorg.conf? Those will interfere in a bad way with the fdi settings.

No such file seems to exist on my machine.

I have changed nothing since my OP other than being booted up in OSX for a while, and now I have two-fingered scrolling and right-clicking but I no longer have single-clicking on the touchpad. How do I fix that?

---

### Post by spencercarran on 2008-11-01
> **parkerhiggins said:**
> I've followed the same steps as spencercarran, and I'm having the same problem.  After creating that file (and adding the relevant text), I've restarted x, but I still have no two-finger scroll or anything.
For some reason (on my machine at least) the "restart" option only logs you out. It might work better to shut the computer off and then start again.

---

### Post by parkerhiggins on 2008-11-01
> **spencercarran said:**
> For some reason (on my machine at least) the "restart" option only logs you out. It might work better to shut the computer off and then start again.

Well, that worked for me too.  Woohoo!

---

### Post by spencercarran on 2008-11-01
> **parkerhiggins said:**
> Well, that worked for me too.  Woohoo!

Do you still have single-finger tap click on yours?

---

### Post by parkerhiggins on 2008-11-02
I guess I don't, but it bugs me anyway, so I usually turn it off.  Now getting it though should just be a question of finding the setting that would have done it in your xorg.conf back in the day (you can find pages of people's xorg.confs, and figure out which parameter enables tap-clicking) and then modify it per your link at the top of this thread for your appletouch file.  You wanna try that?

---

### Post by elazullizard on 2008-12-03
I did follow the parameters, and got both two-fingered scrolling and right-clicking by tapping with two fingers, but now it took away single-finger tap clicks, which is a real pain since I hate using the buttons. However, if I try to fix it, the word processor says it cannot save since I am not logged into the root. How would I be able to log into root temporarily so that I can fix my fdi?

---

### Post by cyberdork33 on 2008-12-03
> **elazullizard said:**
> I did follow the parameters, and got both two-fingered scrolling and right-clicking by tapping with two fingers, but now it took away single-finger tap clicks, which is a real pain since I hate using the buttons. However, if I try to fix it, the word processor says it cannot save since I am not logged into the root. How would I be able to log into root temporarily so that I can fix my fdi?

you have to open config files with sudo. Example:
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by elazullizard on 2008-12-04
Oh duh. Thank you!

---

