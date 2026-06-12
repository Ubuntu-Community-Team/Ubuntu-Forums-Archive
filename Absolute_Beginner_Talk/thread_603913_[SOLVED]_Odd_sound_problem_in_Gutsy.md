---
title: "[SOLVED] Odd sound problem in Gutsy"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by emarkd on 2007-11-05
On my Gutsy box, I'm experiencing a strange sound problem.  Sound works fine for my login, the one created at installation, but for every other user I add, there is no sound.  I've checked the 'Users and Groups' GUI and they're all allowed sound.  I even hit the terminal and did 'id <user>' for each of them and they're all in the audio group (number 29).  It's driving me crazy.  

In the Volume Control applet, there are three devices listed:
   Intel ICH6 (alsa mixer)
   ESS ES1938 (Solo-1) (ala mixer)
   Analog Devices AD1980 (OSS mixer)

I don't know what all of those are because I've only got the onboard sound card.  My login, the one that works, has the Intel ICH6 selected, so I made sure the others did as well, but nothing.  There aren't even any error messages - there's just no sound.  Video works fine for movies but there's no sound.  If I play an mp3 or something, totem does it's visualization thing so I know it's reading the file, but there's no sound.

I just don't see why it would work for my login but not for anyone else's.  I just created a new user just to try it again, and nothing.

Thanks for reading and please help if you can!

---

### Post by Randomwkh on 2007-11-05
Same problem here... i get the login sound but after that every sound an app tries to make like error messages makes an annoying sound from my PC

meh im a noob nevermind  went into system > preferences > sound and under the Sounds tab i saw i only had Login and Logout sounds. Also i turned system bleep off

---

### Post by emarkd on 2007-11-05
I wish my problem were so easy.  I get full sounds from my login, both the sounds that ubuntu makes and sound from video or audio files, web sites, etc, but other logins get nothing at all - no weird noises, just nothing

---

### Post by emarkd on 2007-11-05
If anyone else stumbles on this thread, I've found a solution to get it to work.  Turns out 'autodetect' doesn't autodetect, at least not always.  For each user that didn't have sound, I went under System - Preferences - Sound and tried each entry for every field until it worked.  One of the entries worked fine, but autodetect did not.  Good luck to all.  I'll be very happy when these little bugs get worked out, because they certainly put a blemish on an otherwise excellent product.

Thanks to all who read my post.

---

