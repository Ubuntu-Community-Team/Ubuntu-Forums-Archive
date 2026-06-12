---
title: "Amarok quit playing"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by sarsippius on 2007-05-16
Hey,

I just recently started using Ubuntu 6.10.  I installed Amarok, with mp3 support, and it was playing...

I have a Creative Audigy2 sound card, and an onboard sound card.  I tried doing this:

To get 5.1 Surround Sound I edited ~/asoundrc with gedit.  I added at the end of the file:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

Then I did:
asoundconf list

which gave me:
ICH5
Audigy2

So typed:
asoundconf set-default-card Audigy2

Now Amarok is not playing trough the Audigy2 card, and when I go to System -> Preferences -> Sound, the default sound card will let me change it to Audigy 2 ZS, but when I hit Close and go back to see if the change took effect, it goes back to Intel ICH5.

Rhythm Box plays fine, but without the 5.1 Surround.

Can someone please help?

Any advice is greatly appreciated!!!

---

### Post by sarsippius on 2007-05-16
Once I removed the changes to ~/.asoundrc and restarted my computer, I got sound back to Amarok.  But I still don't have 5.1 working.

Anybody have a fix for that?

Thanks for any help!

---

