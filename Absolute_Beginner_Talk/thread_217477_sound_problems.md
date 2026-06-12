---
title: "sound problems"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by vincentvee on 2006-07-17
does anyone know:
why the sound has stopped working on my computer? (it was working fine until today, or yesterday)
how can i fix it?

this really annoys me, as i use my computer for music a lot.
i'm workin on it but i haven't got anywhere yet

---

### Post by HereInOz on 2006-07-17
Have you got a Default sound card showing up in System > Preferences > Sound?

What have you done to diagnose this so far.  Your question is a bit vague, as you really don't give us much to go on.  Bit like asking why your foot hurts, without telling us what you have been doing.

---

### Post by vincentvee on 2006-07-17
the message i get is:
This is an audio-only file, and there is no audio output available.
that happens with all my sound files, and there are no system sounds either.
yes i have a default sound card, and i haven't done a lot to diagnose as yet, i got a heap on my plate, so i thought i'd post something and see if anyone else had a similar problem and maybe a solution

---

### Post by HereInOz on 2006-07-17
There has been a previous post on this problem, but it didn't come up with anything vaguely useful at all.  The ones who answered the previous post seemed to feel that it was a codec problem, and referred the poster to the Restricted Formats page in the Wiki - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I tend to feel it goes deeper than that. It is a listed Xine error message, but unfortunately I cannot find anything about it. I have never had this message so I cannot assist with a solution.  I will keep looking and post back if I find something for you. In the meantime, all I could suggest is to have a ponder on what you did over the last couple of days and see if you can think of what, if anything you changed.

Sorry I can't be of more assistance.

---

### Post by Apple 101 on 2006-07-17
This happened to me.  The volume was (for some strange reason) muted, after being at normal levels ever since the install.

---

### Post by HereInOz on 2006-07-17
It is possible that it relates to your sound deamon, which is probably esound.  Go in to Synaptic and search for esound, then mark all the packages that are installed for re-install.  This is a long shot and will probably not work, but it is all I can think of.

---

### Post by Apple 101 on 2006-07-17
Also, check for your default sound card.
System --> Preferences --> Sound

---

### Post by vincentvee on 2006-07-18
yeah got it sorted
don't know what the problem was exactly, but i had sound when i rebooted, which doesn't get done much around here.
thanks for all the help anyways

---

