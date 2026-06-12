---
title: "Mac Mini audio"
date: 2009-09-30
forum: Apple Hardware Users
---

### Post by DigiAngel on 2009-09-30
Hey all.

For the life of me I just cannot seem to get anything at all with my Mac Mini (older Core Duo 1.83) to work with Alsa.  Here's what I have:

lspci:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I've tried loading and unloading snd-hda-intel a number of times and different options, but in the end I get:

aplay -l:

aplay: device_list:217: no soundcards found...

Anyone have any hints on what to do next?  Thanks.

James

---

