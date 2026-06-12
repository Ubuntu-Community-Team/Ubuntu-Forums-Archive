---
title: "sound server error"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by loanrangie on 2007-03-15
I  have just installed the KDE desktop enviroment to Ubuntu 6.1 and as soon as ive logged in i get an error message - ´sound server error, cpu overload´. This is without any programs running and i dont have any sound and the message keps popping up freezing my system ?

---

### Post by loanrangie on 2007-03-16
Does anyone have any ideas ? I have got no sound and its driving me nuts, also is there an equivelant to device manager so i can check my hardware status ?

---

### Post by jetpeach on 2007-03-24
you could check out
[https://launchpad.net/ubuntu/+source/arts/+bug/66982](https://launchpad.net/ubuntu/+source/arts/+bug/66982)
typing this command and reboot fixed it for me, maybe it help you as well
echo "options snd-via82xx dxs_support=2" |sudo tee -a /etc/modprobe.d/alsa-base

---

