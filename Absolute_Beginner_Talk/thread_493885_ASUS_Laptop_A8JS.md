---
title: "ASUS Laptop A8JS"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by LUNITIC on 2007-07-06
New to LINUX. Haven't had much success running different distros. I used a friends UBUNTU disc and it's the best thing that I've seen that runs most of my drivers. 

I tried using the live disc but I can't get sound to work. My Laptop uses Sound Max Integrated Digital HD Audio. 

Any suggestions?

---

### Post by r4ik on 2007-07-06
You could try,

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by kwacka on 2007-07-06
On my laptop, Ubuntu installed the sound system OK, but set "external amp" as the default,  check that its not 'checked'setting in alsa mixer.

---

### Post by LUNITIC on 2007-07-07
KWACKA - What is the make and model of your laptop?

Also, guys thanks for the quick help.

---

### Post by maharaja on 2007-07-07
I have the same laptop and got sound working. You need to tell us which Ubuntu distro you're using. Pre-Feisty Fawn I did the following:

Go to the terminal and write

```
sudo gedit /etc/modprobe.d/alsa-base
```

Scroll to the bottom and add the following line:

```
"options snd-hda-intel position_fix=1 model=3stack"
```

That should do the trick.

> **LUNITIC said:**
> New to LINUX. Haven't had much success running different distros. I used a friends UBUNTU disc and it's the best thing that I've seen that runs most of my drivers. 

I tried using the live disc but I can't get sound to work. My Laptop uses Sound Max Integrated Digital HD Audio. 

Any suggestions?

---

### Post by LUNITIC on 2007-07-07
> **maharaja said:**
> I have the same laptop and got sound working. You need to tell us which Ubuntu distro you're using. Pre-Feisty Fawn I did the following:


The version of UBUNTU 7.04 (not sure of the name), a disc I purchased with a magazine in Gydnia Poland 07/07.  I'm setting up to switch from Vista completely just getting my ducks in one row.

Question? Were you able to get all of your features to work, i.e video, usb etc?

Thanks in advance

---

### Post by maharaja on 2007-07-08
Well ... most of the stuff I care about works perfectly (like the Wireless, Nvidia Card, Dual Monitors, external USB keyboard and mouse, etc). If you do a search on the forum, there are a couple of threads with tips on how to get most of the hardware to function under Ubuntu.

Here's a couple of threads you should check out:
[http://ubuntuforums.org/showthread.php?t=328788]("http://ubuntuforums.org/showthread.php?t=328788")
[http://www.rothlaender.net/a8js.html]("http://www.rothlaender.net/a8js.html")

---

