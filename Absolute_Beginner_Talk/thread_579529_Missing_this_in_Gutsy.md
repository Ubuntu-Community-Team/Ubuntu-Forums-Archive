---
title: "Missing this in Gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-10-18
Edgy had this installed by default, for feisty you had to download packages, like vox, mpg123 etc, in gutsy even after installing the said programs I'am unable to sample audio by hovering cursor over the audio icon. Any solutions or suggestions? This is one nifty feature that impresses window believers the most, and I' am missing it.

---

### Post by markl187ld on 2007-10-18
It's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/mpg321/+bug/125739").

You need to Install:

mpg321
ubuntu-restricted-extras
PulseAudio
PulseAudo-esound-compat
libasounds2-plugins

---

### Post by Dyegov on 2007-10-18
I was also thinking why it didn't work in my feisty when it used to do on edgy . . . Anyway, I'm downloading that once Gutsy downloads and installs. Thanks ;)

---

### Post by FredB on 2007-10-18
> **markl187ld said:**
> It's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/mpg321/+bug/125739").

You need to Install:

mpg321
ubuntu-restricted-extras
PulseAudio
PulseAudo-esound-compat
libasounds2-plugins

Thanks for the bug info. I didn't know about it ;)

---

### Post by Beggar on 2007-10-18
Man those were the good old days, it took me weeks to figure out why my computer would randomly play music....

---

### Post by mahiyar on 2007-10-18
Did and tried all that, now the bubble is coming but still no sound.

---

### Post by steveneddy on 2007-10-18
Man - does it seem like synaptic is taking forever today to DL anything?

---

### Post by mahiyar on 2007-10-18
Of all the three consecutive releases I have tried from edgy to Gutsy, in Gutsy I found the most problems. Now even my sound recorder is not working. Of course I will make a separate thread for it.

---

### Post by kazamx on 2007-10-18
> **steveneddy said:**
> Man - does it seem like synaptic is taking forever today to DL anything?

Its because its release day. the Ubuntu servers are being hammered. not only do they have every man and his dog downloading the upgrade from 7.04 to 7.10, they also have every single one of them trying to download all those col little bits and bobs they need. Give it a day or two to settle down.

---

### Post by FredB on 2007-10-18
> **steveneddy said:**
> Man - does it seem like synaptic is taking forever today to DL anything?

Logic. It is a release day after all. It will be better in two or three days.

---

### Post by mahiyar on 2007-10-18
Hey Folks give a thought about my problem

---

### Post by chrisccoulson on 2007-10-18
> **markl187ld said:**
> It's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/mpg321/+bug/125739").

You need to Install:

mpg321
ubuntu-restricted-extras
PulseAudio
PulseAudo-esound-compat
libasounds2-plugins

I get audio previews after installing these packages. However, I now have another problem. When a user logs out of my machine, the pulseaudio process is never terminated and subsequently, the next user who logs in to my machine is told the sound device is busy until I manually kill the pulseaudio process. Do you see something similar?

---

### Post by mahiyar on 2007-10-19
After installing pulseaudio, I could not even open sound recording programme, it contunually gave the error "Settings incorrect, check multimedia etc" until I finally uninstalled pulse audio. Still waiting for a solution to this.

---

### Post by bouss on 2008-02-21
Though I found nothing for libasounds2-plugins installing all else made it work. Thanx a lot:)

---

