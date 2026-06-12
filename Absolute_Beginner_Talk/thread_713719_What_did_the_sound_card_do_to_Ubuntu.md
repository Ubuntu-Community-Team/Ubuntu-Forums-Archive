---
title: "What did the sound card do to Ubuntu?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-03-03
Earlier I was hooking my speakers up to my pc because I had them on another one for awhile but for some reason when I hooked them back up I could not get any sound. So I tried every single port on the sound card and on one connection I can get the login sound to play but not the sound it makes when the desktop comes on. So I tried to set the default soundcard using asoundconf set-default-*mysoundcard* and when I rebooted it gets half way into starting Ubuntu then the screen just goes blank. So now I can't boot into Ubuntu. What did the sound card do to my system?? I'm using the livecd to boot into Ubuntu but I really don't want to reinstall as I have files saved that I can't lose.

Thanks

---

### Post by Crafty Kisses on 2008-03-03
> **psam3 said:**
> Earlier I was hooking my speakers up to my pc because I had them on another one for awhile but for some reason when I hooked them back up I could not get any sound. So I tried every single port on the sound card and on one connection I can get the login sound to play but not the sound it makes when the desktop comes on. So I tried to set the default soundcard using asoundconf set-default-*mysoundcard* and when I rebooted it gets half way into starting Ubuntu then the screen just goes blank. So now I can't boot into Ubuntu. What did the sound card do to my system?? I'm using the livecd to boot into Ubuntu but I really don't want to reinstall as I have files saved that I can't lose.

Thanks

I'm not sure, but check alsamixer.
```
sudo apt-get install alsamixer
```

---

### Post by psam3 on 2008-03-03
I already have alsamixer and everything is turned up. It is also displaying my old soundcard even though I changed the default to the new one.

---

### Post by superprash2003 on 2008-03-03
is it an external sound card?? if so try removing it and booting...

---

