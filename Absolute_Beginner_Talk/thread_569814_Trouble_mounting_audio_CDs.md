---
title: "Trouble mounting audio CDs"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by elanor_of_valinor on 2007-10-07
I'm quite new to all this, a friend installed xubuntu for me a few weeks ago.

I had xgine installed, but this laptop is quite old, and so the program had problems loading properly. So, as I am (vaguely) familiar with Amarok, I decided to install it, but it could not play wma or mp3, so I decided to uninstall that and try another multimedia program.

Only problem now is that no audio CD will mount now. It says "Unknown error", and then says "Invalid mount option when attempting to mount volume"

Although I have used ubuntu before, I just used it "out the box" once my friend set it up for me.



Can anyone help me with this?

---

### Post by -grubby on 2007-10-07
what model of CDROM drive?

---

### Post by raja on 2007-10-07
First thing, 
The reason amarok did not play mp3 when you tried was not a problem with amarok but with the fact that the mp3 codec is not installed by default in Ubuntu since it is not open source. 

About the problem with mounting cds, can you post the output of ```
cat /etc/fstab
```?

---

