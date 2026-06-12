---
title: "Not able to record from Line In"
date: 2010-09-29
forum: Apple Hardware Users
---

### Post by rmcellig on 2010-09-29
I now have Ubuntu set up on my iMac dual boot. When I tried to record some audio from the radio that is attached to my Mac, all I get is white noise.

What do I need to do to get this working in Ubuntu?

---

### Post by linuxopjemac on 2010-09-29
Did you check in alsamixer if there is some channel muted?

---

### Post by rmcellig on 2010-09-29
Here is my alsamixer settings.

---

### Post by linuxopjemac on 2010-09-29
I don't know what it stands for, but S/PDIF is muted. Unmute it with "m".

---

### Post by rmcellig on 2010-09-29
I did that. Thanks. I don't know if this will be of any benefit but when I start up into my Mac partition, I launched a virtual a copy of Ubuntu 10.04 that I have that I use with VMWare Fusion. It works great! Attached are the settings for Ubuntu I use with VMware Fusion compared to the settings I have in Ubuntu 10.04 that I installed dual boot on my iMac.

---

### Post by rmcellig on 2010-09-29
Here is a more detailed Alsamixer screenshot. What are the rec options for? Do I need to check these? Anything else I need to change?

When I selected Microphone 2 from the Sound Preferences Input, that worked fine. It's the Input selection that does not seem to work and I need this to work because I record radio shows at the radio station I work at.

---

### Post by linuxopjemac on 2010-09-29
I have no idea, but I would just tick them and try to see if it makes a difference.

---

### Post by rmcellig on 2010-09-29
I typed in this command:

ubuntu-bug audio

I would like to post the results from this but don't know how to save the file unless there is a better way for me to gather info on the sound card etc...

---

### Post by linuxopjemac on 2010-09-29
ubuntu-bug alsa-base

---

### Post by rmcellig on 2010-09-29
Thanks!

I typed that in but all I get is a report that I have to send off. I have no way of copy/paste into this thread or is that not the intent of this command? Do I have to send this report to developers and greate an account to do so?

---

### Post by linuxopjemac on 2010-09-29
The bug report will be sent to the developers. There is little chance that people here can help you with that.

---

### Post by rmcellig on 2010-09-29
Thanks anyway. Do you know how I can transfer this thread to the Multimedia forum? Maybe I will have better luck there? :)

How would I go about transfering this post?

---

### Post by linuxopjemac on 2010-09-29
You can't. Only moderators can do that. I would just copy and paste it in that forum.

---

