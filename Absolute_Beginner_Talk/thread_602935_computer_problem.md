---
title: "computer problem"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by IISpII on 2007-11-04
Ive had a problem with my computer ever since i got it.  (then it can preloaded with vista)  I have switched to Ubuntu since then, this made my problem less prominent, but it still occurs every so often.  what happens is then i am running something win a large interface, like a video game or something, my computer will just shut down, withought warning.  My computer is a sony VGN-SZ491N. (now known as 'VGN-SZ491N/x' )  it is a very good computer and i know it is up to par.  It currently runs Ubuntu 7.10 + compiz fusion + awn.  I have a warranty were if absolutely anything goes wrong with the computer it can be exchanged, so cost is not a factor.  i just wanted to see if there was anything i could do before i talked to sony, again.

-Best regards, Graham

---

### Post by Fred_E _krugar on 2007-11-04
Alot of times when the power usage is high the PSU could be the problem

---

### Post by celticbhoy on 2007-11-04
Could be a memory problem. Try running memtest from grub and see if any errors flag up

---

### Post by Pumalite on 2007-11-04
I'd guess memory problems. Or need larger /swap?

---

### Post by IISpII on 2007-11-04
what is memtest??

---

### Post by amingv on 2007-11-04
Hello,

When running heavy applications? This sounds to me like a temperature problem: your pc is overheating.

You can check the temperature of your processor in the BIOS settings, when your computer reaches critical heat it's automatically turned off to prevent damage.
Since you still have your warranty I don't recommend opening it yourself, as not to void it; rather take it to your dealer, it's most likely a simple problem that can be solved in half an hour.

---

### Post by celticbhoy on 2007-11-04
When you first boot your PC a menu should appear, with

Ubuntu,
Ubuntu Recovery
Memtest

Any other OS's

move to memtest and press enter

---

### Post by Maestro23 on 2007-11-04
> **amingv said:**
> Hello,

**When running heavy applications? This sounds to me like a temperature problem: your pc is overheating.**

You can check the temperature of your processor in the BIOS settings, when your computer reaches critical heat it's automatically turned off to prevent damage.
Since you still have your warranty I don't recommend opening it yourself, as not to void it; rather take it to your dealer, it's most likely a simple problem that can be solved in half an hour.

My guess also.  See this a lot when playing games.  Video card churning hard, not enough airflow, things start to get heated inside, etc... System's last resort is to shutdown.

---

### Post by jordank on 2007-11-04
sounds like a heating issue to me.
the same thing happened to me on my last box, improper cooling of the video card.  The fan wasn't running.
Check your video card fan.

---

### Post by IISpII on 2007-11-04
i dont see memtest on my startup, how would i be able to acces it with the OS running??

---

### Post by celticbhoy on 2007-11-04
from terminal

sudo gedit /boot/grub/menu.lst.
check timeout set high enough no of secs (10 or so)

move down file to
## ## End Default Options ##

Check you can see something like

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

If it is there re-boot and you should have enough time to select it.

---

### Post by amingv on 2007-11-04
> i dont see memtest on my startup, how would i be able to acces it with the OS running??

I think there is such a thing in the repositories, try:

```
sudo apt-get install memtester
```

Never used it before though, and thus I can not give instructions on it's usage (but you run it as "memtest", not "memtester".)
I don't think it's a memory issue, but it's not bad to discard it.

---

### Post by DarkN00b on 2007-11-04
When your computer is booting, do you see something that says to press ESC for boot options (or something like that...)? if so, press ESC and use the down arrow to highlight memtest86. It comes installed on _all_ ubuntu systems. Press the Enter key to start the test. The test is on an infinite loop so you'll have to stop it after it goes through its tests.

---

