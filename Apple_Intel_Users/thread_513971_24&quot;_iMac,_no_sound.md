---
title: "24&quot; iMac, no sound"
date: 2007-07-31
forum: Apple Intel Users
---

### Post by ripdog on 2007-07-31
I have been unable to get sound working in Kubuntu, despite repeated attempts using the instructions at [this thread.]("http://ubuntuforums.org/showpost.php?p=2978364&postcount=41")  These instructions have worked twice for me, and i am at a loss as to why they didn't this time.

All operations completed with no error.

---

### Post by joselin on 2007-07-31
Donwload the [latest alsa drivers]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/") and compile it.

```
./configure
make
sudo make install-modules
```Then remove the old module and insert the new one.


```
sudo rmmod snd_hda_intel
sudo rmmod snd_hda_codec
sudo modprobe snd_hda_intel
```This works for me on same computer.

Regards,
Jose

---

### Post by ripdog on 2007-07-31
I'll try that, thanks. do those instructions work for headphones and speakers?

EDIT: Hmm, i can't get rid of the old modules as they are in use. How can i disable the sound hardware temporarily?

---

### Post by joselin on 2007-07-31
> **ripdog said:**
> I'll try that, thanks. do those instructions work for headphones and speakers?

Never tryed it before you ask, but seems that does not work with my headfones. Is not a problem for me, i never use it, but i will have a look

> **ripdog said:**
> EDIT: Hmm, i can't get rid of the old modules as they are in use. How can i disable the sound hardware temporarily?

Did you try it after a reboot? Did you kill all ESD and Alsa related tasks?

---

### Post by ripdog on 2007-07-31
There don't seem to be ANY alsa or ESD related tasks running.

Do you want my "ps -e" output? It's rather large :P

---

