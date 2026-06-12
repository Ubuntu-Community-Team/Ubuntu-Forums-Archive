---
title: "Idiot question, sorry. . ."
date: 2008-03-24
forum: Apple Intel Users
---

### Post by hackersmovie on 2008-03-24
New to Ubuntu and Linux, I've had a play with it on an old PPC mac and now am installing it on all my Intel's as well, dual boot. First issue is with the sound on my Macbook. Brand new, although not the newest, 2.0 Ghz, Core2Duo, I found this:

> To resolve, add the following to /etc/modprobe.d/options:

```
options snd_hda_intel model=mbp3 

```

what does it mean? Better yet, how do I do it? I tried a sudo command in Terminal, it said:

command not found

Where else do I "add the following" ?

Sorry for the stupid question. . .

---

### Post by girishv on 2008-03-24
You have to edit the file /etc/modprobe.d/options and the line at the end. If its just one line, an easy way to add this is
sudo echo "options snd_hda_intel model=mbp3" >> /etc/modprobe.d/options

or, you can use any editor and append the line at the end of the file. Try,

gksudo gedit /etc/modprobe.d/options


Girish

---

