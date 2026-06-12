---
title: "Flash player problems?"
date: 2011-08-05
forum: Any Other OS
---

### Post by adamhum3 on 2011-08-05
I've been trying to install Flash player on Elementary OS, however even though it's installed in the software centre, it still says I don't have it or it needs upgrading when on YouTube. I've tried downloading it from the Adobe website however I can't install the packages - which I also tried when in Fedora 15, and even when I installed them it said they were already installed.

I had no problems with this in Ubuntu, but I'm on Elementary OS now, so :\

Can anyone help?


Cheers,

Adam

---

### Post by rokytnji on 2011-08-05
When upgrading Flash Like I do in Puppy Linux. I download the tar.gz from Adobe. Extract the libflashplayer.so. I then open my file manager as root (rox file manager in puppy).

I navigate to /usr/lib/mozilla/plugins folder and with my other rox window drag and drop and overwrite old libflashplayer.so. I don't run elementary Linux. So Cut and paste might be your way to place libflashplayer.so into plugins folder. I also don't know if elementary Linux has a /usr/lib/mozilla/plugins folder also. If not. Try looking in ~/.mozilla/plugins folder for libflashplayer.so there.

---

