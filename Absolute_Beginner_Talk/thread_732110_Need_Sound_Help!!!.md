---
title: "Need Sound Help!!!"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by psavy86 on 2008-03-22
Alright here's the deal I have been searching like mad for any documentation that can help me out but none of it is directed to my motherboard or sound card.  

I am running Xubuntu 7.10 on a VIA 8233 motherboard with AC97 audio controller.  I have sound coming through the speakers, able to turn that volume up and down using Gnome Alsa mixer but I can not get my mic to work for the life of me!  

I need to be able to use Skype, it's my only phone.  Whatever information I need to gather I will gladly do that if you are able to provide the commands.  I am a total noob.  I know how to use the terminal, run commands, update and all that.  I tried installing Alsa utilities and driver but I don't think I did it properly.   Thanks!!

---

### Post by keratos on 2008-03-22
post the output of these two commands

```

grep Codec /proc/asound/card0/codec#*
uname -a

```

(two commands in a terminal)

---

### Post by psavy86 on 2008-03-22
root@pats-desktop:/home/pat# grep Codec /proc/asound/card0/codec#*
grep: /proc/asound/card0/codec#*: No such file or directory
root@pats-desktop:/home/pat# uname -a
Linux pats-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by keratos on 2008-03-22
strange!

run alsaconf from a terminal window, as root user:

```

# alsaconf

```

is your audio detected?

---

### Post by psavy86 on 2008-03-22
lol that didn't do much of anything either, in fact ubuntu doesn't even recognize it as a command.  Here is what happened when I ran the command.

root@pats-desktop:/home/pat# alsaconf
bash: alsaconf: command not found

---

### Post by keratos on 2008-03-23
Hi

Use the Package Manager (synaptic) to find all packages beginning with "alsa" (or with the word alsa in!) and install them all.

---

