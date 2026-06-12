---
title: "No sound"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by dodgerwv on 2007-12-09
Just installed 7.10 on a Dell Optiplex 320.  Had to use the alternate install with Lilo to work.  Everything is smooth except I have no sound.  Any ideas on how to get the soundcard recognized?

---

### Post by nikoPSK on 2007-12-09
You can try as follows:

```
asoundconf list
```That'll list all sound output devices recognized.

```
asoundconf set-default-card XXX
```In my case it was "Audigy". I also had to play around in alsa mixer a bit.

---

### Post by gfd_2 on 2007-12-09
I have an acer laptop (7720) and tried about every fix suggested with no luck.  This worked:
[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html) 

I did have to edit the alsa-base file as was mentioned but after that i have in Amarok, DVD player and when streaming from CNN.com.

---

