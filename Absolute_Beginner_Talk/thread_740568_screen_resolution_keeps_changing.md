---
title: "screen resolution keeps changing"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by skrap on 2008-03-30
every other time I boot my scree res defaults back to 1280 x1024 how can I stop this?

---

### Post by marine63 on 2008-03-30
same thing happens to me :(

---

### Post by New2Linux0319 on 2008-03-30
hey, i had same problem.
i have "fixed" it and set as default size/ apply new settings   numerous times...  kind of annoying huh..

---

### Post by aborigine on 2008-03-30
Happened to me too
I have an old nvidiia graphics card which it recognizes and then goes funny.
I think its the driver - not only do I get resolution problems but the whole thing is offset to the right....
evrything worked when I tried Kubuntu but I didn't like the gimmicks and bugs in the interface (and the restricted driver installed like a dream without problems too.
Need an expert here !!

---

### Post by skrap on 2008-03-31
I ran  

sudo dpkg xconfig-xorg last night and it seems to be ok now

---

### Post by skrap on 2008-04-02
Thought I had it fixed but I keep getting a different resolution everytime I reboot.
Is this a bug?  What to do?

---

### Post by aborigine on 2008-04-26
I've been away for a while but I got mine sorted - thing is I don't quite know how, it's a bit confused ! I know that the nvidia legacy package was a disaster, so I disinstalled that and installed the "modern one" instead - the I used nvidia-settings (or something like that) after backing up x-config. Eventually it worked... Oh, and I don't remember using the restricted drivers manager, I worked through the console
Pretty useless but there may be hints in there to help...

---

