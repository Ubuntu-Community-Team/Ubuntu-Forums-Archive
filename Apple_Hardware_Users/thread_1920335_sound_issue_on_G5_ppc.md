---
title: "sound issue on G5 ppc"
date: 2012-02-04
forum: Apple Hardware Users
---

### Post by teripittman on 2012-02-04
I am trying to work through a few issues with my G5 running 11.10. It has just the system soundcard. Looks like this should use the Snapper soundcard, but when I run cat /proc/asound/cards, it shows no soundcards. Could someone point me in the right direction for documentation on troubleshooting this? Thanks for the help.

---

### Post by rsavage on 2012-02-04
[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

---

### Post by teripittman on 2012-02-04
Thanks! I've worked my way though that and it is showing a sound card now. Seems to be using the snd-aoa-fabric-layout. I still can't get it to play even system sounds. I'm going to pick up a set of working speakers to test further.

---

