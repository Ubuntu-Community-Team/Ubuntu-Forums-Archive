---
title: "Upgraded to 7.10 &amp; lost all sound"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Gobbie on 2007-11-22
Subject says it all....I've got no sound!  Everything else seems ok since upgrade to 7.10.  No idea what to do!  Please help!!!

---

### Post by Hayden on 2007-11-22
```
sudo asoundconf list

Names of available sound cards:
Live
V8237

sudo asoundconf set-default-card Live
```

In the above example, I set the default to "Live".

---

### Post by Gobbie on 2007-11-22
Thanks, but what I do with this code?  I really don't know my way around this thing!

---

### Post by Gobbie on 2007-11-22
OK, I found 'terminal'.  this is what I got.........
desktop:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

How do I get round that?

---

### Post by Hayden on 2007-11-22
Did it list your available sound cards? Here's the output from my terminal,

```
hayden@pamela:~$ sudo asoundconf list
[sudo] password forhayden:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
V8237
CMI8738MC6

hayden@pamela:~$ sudo asoundconf set-default-card CMI8738MC6
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

hayden@pamela:~$
```

---

### Post by Gobbie on 2007-11-22
Nope, this is it.........


owen@owens-desktop:~$ sudo asoundconf list
[sudo] password for owen:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

owen@owens-desktop:~$

---

### Post by Benbow on 2007-11-22
You should have got something resembling this:
~$ sudo asoundconf list
[sudo] password for benbow:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
CMI8738
Intel

- but with different sound card(s). What you do with it I can't tell you. However, if you click on System then Preferences and then go down the list to Sound, your sound preferences will pop up and you can then test your system for the best combination.
Bonne chance!

---

### Post by Gobbie on 2007-11-22
I had tried that already and just get an error when I hit any of the test buttons, like this......

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

---

### Post by Benbow on 2007-11-22
Sorry, thats my limit, I'm not that techie. Needs someone to delve deeper. I suppose you had sound prior to upgrading?

---

### Post by Gobbie on 2007-11-22
Thanks for the help anyway.  Yeah, sound was fine before.  In fact, the main purpose of this pc is music!

Anyone got any ideas?!

---

### Post by Hayden on 2007-11-22
Sorry, That's my limit also. :(

---

### Post by Gobbie on 2007-11-22
I need a techie!!!  Anyone?!

---

### Post by stinger30au on 2007-11-22
> **Gobbie said:**
> Subject says it all....I've got no sound!  Everything else seems ok since upgrade to 7.10.  No idea what to do!  Please help!!!

i had the same thing.
i had an easy fix .

double click the speaker on your tool bar.
there is a volume labelled PCM

mine was turned off, set it o on and try.
thats how i fixed mine.hope it works for u

---

### Post by spiderbatdad on 2007-11-22
[http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825)
this thread might help.

---

### Post by ayenack on 2007-11-22
Have you got two sound cards in the system? If so turn off the on board sound from BIOS and that may well solve it.

---

### Post by Gobbie on 2007-12-06
It's fixed now!  I had to install this package "linux-ubuntu-modules-2.6.22-14-386", reboot and it worked!  You can install this package using synaptic (System menu --> Administration --> Synaptic Package Manager).  I've got no idea what it does or how anyone would know to look for it, but it did the job.  It's just a pity that it's so hard to find these fixes if you're a newbie.  Anyway, hopefully the fix might help someone else.

---

