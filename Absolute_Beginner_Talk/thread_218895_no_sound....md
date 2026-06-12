---
title: "no sound..."
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by hellsgate on 2006-07-19
:confused:  i just installed the brand new version of Skype ang give's me a issues with getting sound.  problem with sound device... i am desparately looking for drivers that work for a SB 24bit live card in order to make the thing work and some help on how to install it... does anyone have some tips for me...? i am not completely unfamilair with Linux, it has been a while and could use a helping hand with this...

thanx...

Rickus aka Hellsgate

---

### Post by dmizer on 2006-07-19
after you installed skype:

1) did you make sure that alsa was selected in the audio properties?
2) did you make sure that your correct sound device was selected?

also, are you able to hear sounds in other applications (music etc)?

---

### Post by hellsgate on 2006-07-19
it goes automaticly to alsa, for as far as i can see...

about the sound device, i'm not sure...

there is no sound at all at this time...

but i'm back online now, so if you like to help out, i'm here...

---

### Post by Rumor on 2006-07-19
I'd check to see if your SB is the default sound device. If your motherboard has on-board sound, it may have defaulted to that instead.
System > Preferences > Sound
See what is listed as the default sound device.

---

### Post by hellsgate on 2006-07-19
it says ca0106, standard divice... so how do i change this into sb? it does not say it has a SB card...

---

### Post by Klemik on 2006-07-19
Try closing all sound-related applications, then type "sudo killall esd" in terminal and try to run Skype again.
Also post lspci and lsmod output.

---

### Post by OU812 on 2006-07-20
I have an sb live card. It works fine. But I have my onboard soundcard disabled using the bios settings. You might want to do the same.

john

P.S. Very few os's can handle multiple sound cards.

---

