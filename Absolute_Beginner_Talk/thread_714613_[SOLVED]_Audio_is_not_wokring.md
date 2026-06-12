---
title: "[SOLVED] Audio is not wokring"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-03-04
Hi.
I have acer aspire3683 laptop.i install ubuntu 7.10 on it.
But it cant seem that audio is working.
How can i know that it is working and where can i find the driver either installed and which chippest it is.

i will be thankful.
Arif

---

### Post by kpkeerthi on 2008-03-04
What does ```
lspci | grep -i audio
``` print when run from a terminal?

---

### Post by mmarif4u on 2008-03-04
i get this:
> arif@ANL-Laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


---

### Post by kpkeerthi on 2008-03-04
Ubuntu has detected your sound card just fine. 

Open a terminal and type **alsamixer**

Use arrow keys to navigate and make sure the mixer channels (especially master and PCM) are not muted. Press 'm' key to mute/unmute. **MM** indicates muted. **OO** indicates unmuted. Also make sure the mixer volume levels are raised enough. Press 'Esc' to quit and check playback.

If it doesn't check [troubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") guide

---

### Post by mmarif4u on 2008-03-04
Thanks kpkeerthi.
I got it working by your method.
Thank you very much for fast help and reply.

---

### Post by kpkeerthi on 2008-03-04
Glad it worked for you. Enjoy your ubuntu. :)

---

