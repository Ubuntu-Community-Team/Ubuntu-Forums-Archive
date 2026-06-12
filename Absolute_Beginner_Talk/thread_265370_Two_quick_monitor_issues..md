---
title: "Two quick monitor issues."
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-09-25
Hey, it's me again.

Since installing Ubuntu a few days ago I've:

a) Fixed the internet
b) Broke my on-board sound card
c) Bought a new sound card
d) Become angry at Gaim
e) Figured out I had no reason to be angry with Gaim

I'm finally getting myself where I want to be but I have two more issues (which I understand are common):

a) My screen resolution is well too low, and it doesn't give me the option to make it higher, and
b) My second monitor is just staring at me with a black screen.

Now I've been through numerous threads that deal with this problem, and I've not been able to understand what to do about it. Are there very simplistic, step-by-step walkthroughs for these? The only experience I have with the command terminal was from setting up my internet, so I need to be told when to enter "sudo" and everything. Can anyone help, please?

---

### Post by henriquemaia on 2006-09-25
As for the low resolution of your monitor, open a terminal and type:

```
sudo dpkg-reconfigure xserver-xorg
```

Then, you'll have a step by step configuration utility to change the settings of your X. Answer most of the questions by the default values (change only what you understand). When it comes to the resolution question, check the ones you want to use.

---

### Post by theknave on 2006-09-25
> **henriquemaia said:**
> As for the low resolution of your monitor, open a terminal and type:

```
sudo dpkg-reconfigure xserver-xorg
```

Then, you'll have a step by step configuration utility to change the settings of your X. Answer most of the questions by the default values (change only what you understand). When it comes to the resolution question, check the ones you want to use.

When I did that, my desired resolution was already checked off, as well as several others that the "screen resolution" thing won't let me choose. :confused:

---

### Post by jcrnan on 2006-09-25
Whats your gfx card?

---

### Post by theknave on 2006-09-25
ATI Technoligies, Inc. 3D Rage I/II 215 GT [Mach64 GT]

---

### Post by henriquemaia on 2006-09-25
> **theknave said:**
> ATI Technoligies, Inc. 3D Rage I/II 215 GT [Mach64 GT]

Is that an old card? If yes, please check your colour depth and reduce it. After that you'll be able to use the resolution you want. I had a similar issue some time ago with an old card and that solved.

---

### Post by theknave on 2006-09-25
> **henriquemaia said:**
> Is that an old card? If yes, please check your colour depth and reduce it. After that you'll be able to use the resolution you want. I had a similar issue some time ago with an old card and that solved.

It's probably an old card - it's definitely not a good one. Standard with the PC a couple years ago. I'll give that a go, thanks.

---

### Post by theknave on 2006-09-26
Thank you, henrique, that fixed it.

Any idea on a simple way to set up dual-monitors?

---

### Post by henriquemaia on 2006-09-26
Try this thread:

[**HowTo: Xinerara / Dual Head with TWO cards**]("http://ubuntuforums.org/showthread.php?t=31686")

It's an HowTo I wrote a year ago, when I had two cards on my computer, one of which was pretty old.

---

### Post by bodhi.zazen on 2006-09-26
[Xcinerama how to](https://help.ubuntu.com/community/XineramaHowTo)

[How to Dual monitor Twinview](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

[Mine](http://ubuntuforums.org/showthread.php?t=240150)

My how-to starts with a working twinview, but gives separate monitors......

---

