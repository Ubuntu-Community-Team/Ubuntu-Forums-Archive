---
title: "make &amp; make install?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by CBondra on 2006-08-29
Everytime I try to use "make" and "make install" on **anything** it never works.

```
make
make: ***No targets specified and no makefile found. Stop.
make install
make: ***No rule to make target `install'. Stop.
```

I'm new to the whole Linux, so it's probably something really easy that I don't know about yet.


???

---

### Post by muep on 2006-08-29
Are you sure you are trying to do that in the correct directory? There should be a file named Makefile or makefile in it. Have you extracted the package?

On the other hand, what are you trying to do? Most of the stuff is available precompiled in the repositories, so you usually don't need to compile anything.

---

### Post by helmet on 2006-08-29
did you run ./configure first?

the standar is:

./configure
make
sudo make install

./configure generates the makefile. always read the INSTALL or README file to learn about the options and whatnot you might have to specify as well

---

### Post by CBondra on 2006-08-29
I really _don't_ know what i'm doing right now. I'm trying to install my sound card driver (because it mysteriously stopped working.) It worked when I first installed Ubuntu, but now it doesn't. Does this happen often?

And yes, I do try it in the folder that has the MAKEFILE and INSTALL (install-sh too) in it.

It always happens, not just with this attempt, but when I tried to install other stuff too.

---

### Post by deadgobby on 2006-08-29
What is your soundcard? Did you disable the onborad sound in the BIOS? 
Gobby

---

### Post by CBondra on 2006-08-29
It came with the computer, I think it's built in. I would've known if I had wrote the names down before I swiped it but all I see now is

Intel ICH6 Playback Device

I'm pretty sure it's AC'97 
HP Compaq dc5100


My video driver is built in i810 so my sound is probably i810 too.

---

### Post by CBondra on 2006-08-29
???

---

### Post by mlind on 2006-08-29
> **CBondra said:**
> I really _don't_ know what i'm doing right now. I'm trying to install my sound card driver (because it mysteriously stopped working.) It worked when I first installed Ubuntu, but now it doesn't. Does this happen often?

And yes, I do try it in the folder that has the MAKEFILE and INSTALL (install-sh too) in it.

It always happens, not just with this attempt, but when I tried to install other stuff too.

Why are you running make and make install if you don't know what you're doing? You should probably explain what was the last thing you did before sound stopped working and check that there's no volume channels muted.

---

### Post by CBondra on 2006-08-29
I was following the step by step to install the driver, because I never installed a driver for it after the swipe. I just woke up and it wasn't working, it won't even detect the device, and when I click on volume control I get "No volume control Gstreamer plugins and/or devices found."

---

### Post by mlind on 2006-08-29
> **CBondra said:**
> I was following the step by step to install the driver, because I never installed a driver for it after the swipe. I just woke up and it wasn't working, it won't even detect the device, and when I click on volume control I get "No volume control Gstreamer plugins and/or devices found."

There's a good sound troubleshooting guide floating here on forums somewhere, try to search for it. It covers most of the problems and solutions.

[LIST]
[*]Does your user belong to **audio** group? (type groups on terminal)
[*]What does **gstreamer-properties** report?
[*]Does /proc/asound/cards exists (if it does, post the file contents)
[/LIST]

---

### Post by CBondra on 2006-08-29
Groups in terminal returns:
cj (my username) video admin

gstreamer-properties reports:
```

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'
```


/proc/asound/cards doesn't exist but there is a folder called "card0"

---

### Post by mlind on 2006-08-29
Add yourself to following groups:
```

adm dialout fax cdrom floppy tape **audio** dip video plugdev lpadmin scanner admin

```

Using:
```

sudo adduser *user* *group*

```

---

### Post by CBondra on 2006-08-29
I just did that.


Should I be able to use make now? Or...what happens now that i'm in the audio group?

---

### Post by mlind on 2006-08-29
> **CBondra said:**
> I just did that.


Should I be able to use make now? Or...what happens now that i'm in the audio group?

only users on audio group may use the sound device. Try to relogin and test if your audio works now. You should **not** compile soundcard drivers manually if those worked out fine before.

---

### Post by CBondra on 2006-08-29
**That worked!!!!!!!!!**


I thought it was weird (but didn't think of it at the time) that the sound worked at the login screen, but not when I was logged in.


Thank you so very much!!1 :D

---

### Post by kinematic on 2006-08-29
if you're not able to "make" you probably dont have the c compiler installed because make compiles source code into binarie code(your computer can't do anything with source code).
the package build-essential gives you everything you need to install from source code.

---

### Post by CBondra on 2006-08-29
Ok.
I heard I needed GCC G++ to use it, and I already have it :/

I will get the build-essential though.


*listens to music happily*

EDIT
Checked the package manager.
I have build-essential too. :/

---

