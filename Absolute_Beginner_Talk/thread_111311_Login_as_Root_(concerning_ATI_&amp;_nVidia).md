---
title: "Login as Root (concerning ATI &amp; nVidia)"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-02
How do you log in as root.
I mean, logout and login as root, not through sudo. I'm trying to run some apps and one keeps saying,

"You need to run this installer as a super-user" and quits.

The other app posts in the terminal:

"ERROR: nvidia-installer must be run as root" and quits.

The Apps are the ATI and nVidia installers.Any other ways or Shortcuts Welcome.

:confused:h34r: Jaygo333 :confused:h34r:

---

### Post by mazelado on 2006-01-02
To install the ATI drivers, try this:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

For NVidia, try this:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by meborc on 2006-01-02
hmm... why dont you just install the **nvidia-gfx** via synaptic? ... for help on how to do that is in the **help **:rolleyes: menu... just go to ubuntu 5.10 starter guide from there and then try hardware... it has a good how to for nvidia drivers

---

### Post by Tuf on 2006-01-02
[QUOTE=mazelado]To install the ATI drivers, try this:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

For NVidia, try this:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)[/QUOTE]


Thanks for posting this info, I have been looking for good directions for installing ATI drivers :KS

---

### Post by DarkDancer on 2006-01-02
Hi!

I tried using the drivers from the ATI sight and the instructions from the Wiki, everything goes well until I get to this command:

sudo module-assistant build,install fglrx-kernel

a screen (module assistant, error message) comes up and tells me:

Bad luck, the kernel headers for the target kernel version could   
not be found and you did not specify other valid kernel headers to use. 

What do I do?

---

### Post by kaamos on 2006-01-02
You are most likely missing the kernel headers. Try this
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by phido on 2006-01-02
*sudo su* ist what ur looking for.

---

### Post by DarkDancer on 2006-01-02
Cool! Thanks! Seems to have worked! ;)

---

