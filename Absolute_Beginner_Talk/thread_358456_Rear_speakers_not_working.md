---
title: "Rear speakers not working"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by pensador82 on 2007-02-10
Hi,

I have an audio system with 4 speakers (front R&L and rear R&L) and a subwoofer, but I cannot get the rear speakers to work. I've played the alsamixer utility by unmuting all controls and setting to the maximum volume, but nothing. On Windows, it works if I set the sound to "4 speakers". How can I do the same on Ubuntu?

---

### Post by pensador82 on 2007-02-11
Anyone?

---

### Post by PoopyTheJ on 2008-04-04
At least I'm not the only one having this issue. Can you tell me how to use the alsamixer? I didn't even know it existed I was looking for a utility to allow me to work with the sound card.

---

### Post by Whiffle on 2008-04-04
What sound card do you have?  The output of "lspci -v" should tell.  YOu can run alsamixer by going to the terminal and running "alsamixer".  Once its running, the left and right arrows switch from channel to channel, M mutes/unmutes, and up/down changes volume.  Theres other controls too but  I don't know them off the top of my head.

---

### Post by herbster on 2008-04-04
If you want help with your sound, it would be sensible to please indicate what your sound card is.

Do what Whiffle has posted, and if the mixer levels in your alsamixer are all full, try in a terminal:

```
speaker-test -twav -Ddefault -c5
```

Hit CTRL+C to stop it after it's run the test once through. Do you hear the voice in all channels? Try it also with "c4" and "c6".

---

### Post by PoopyTheJ on 2008-04-09
Sorry onboard HDA Intel as listed in Preferences-Sound, it the sound on an Asus p5kse mobo, ummm... Realtek ALC883 8-channel High Definition Audio CODEC, thanks for the input, we found mold in our hosue so I've spent the past week trying to stay up to date with school work and cleaning the house in between work and school, uggh

---

