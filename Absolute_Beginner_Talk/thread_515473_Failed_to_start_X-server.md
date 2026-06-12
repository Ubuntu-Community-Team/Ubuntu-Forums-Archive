---
title: "Failed to start X-server"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by shakujou on 2007-08-02
Hi, I just freshly installed Ubuntu tonight, and I've already coming up with problems.  Keep in mind that this would be the first time I've ever used Linux, or anything except Windows.

I downloaded the 64-bit version, which from what I read, supports both intel and AMD x86, right?  From there, I took the usual steps, and pressed the install icon from the Live CD.  Everything went smoothly during the install, everything finished up within 10-15 minutes easily.  Then I had to restart my computer, which is what I did, and from here is when my problems start.

It loads for a bit, and then it displays this exact message:
[quote=my computer]Failed to start X server (your graphical
interface).  It is likely that it is not set
up correctly.  Would you like to view the X
server output to diagnose the problem?[/quote]

I click yes, and this is where my brain starts to fry.  It displays a bunch of system information that I'm more or less supposed to except, since I can't decipher any of it.  Eventually, I get to a screen that asks for my user name and password.  I type those in, and then it asks me to use commands using sudo, which is next to a completely new idea for me.  This is where my brain oozes out of my head, and I can no longer comprehend what I am even doing.

If for any reason I have just downloaded the wrong version, here is my system information:

40gb HD 
Pentium 4 HT, 3.0ghz, 800 fsb, 2mb L2 cache
1gb DDR400
Gigabyte mATX MB
nVIDIA FX 5500

---

### Post by Mark_in_Hollywood on 2007-08-02
First) I'm no expert. Period.

Try holding down both the ctrl and alt keys with your left hand's finger. With the right hand, press the backsp. key. 

If, after a few moments, you see

root@yourcomputername:>~

or something similar

type

sudo startx

if you get a screens full of question after question, press enter or select the most common or the default. When done (I'm having to recall this from memory) try

sudo startx again. If that doesn't work. Please do a reinstall. Something truly minor could have gone wrong and a re-install could be the _easiest_ fix.

---

### Post by shakujou on 2007-08-02
I typed in sudo startx, but I got this message:

Fatal server error:
no screens found
XIO:   fatal IO error 104 (Connection reset by peer) on X server ":O.O"
          after 0 reuests (0 known processed) with 0 events remaining.

I just redid it, and above the mentioned error, it says it could not load the module nvidea, because drivers do not exist.  I'm guessing it doesn't like my graphics card?

---

### Post by avik on 2007-08-02
Type in:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Pick the defaults.

---

