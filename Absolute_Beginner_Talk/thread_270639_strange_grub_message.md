---
title: "strange grub message"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by n0dl on 2006-10-03
Occasionally i get a strage grub message saying:
```
[17179587.264000] hda_intel: azx_get_response timeout, switching to single_cmd mode...

```
when i boot. Nothing on my computer is affected by this. Internet works fine, I am able to access my files on my hd sound is ok and stuff like that. What does this message mean? Is it anything I have to worry about?

---

### Post by ciscosurfer on 2006-10-04
You might be booting into Single mode (the recovery mode)...don't know for sure...got to do some research and I'll get back to you...but at first glance, that's my best hunch.

---

### Post by n0dl on 2006-10-04
I found out that hda stood for High definition Audio controller. Its a kernel message. It doesnt really effect anything and only appears on occasion. I dont think its much to worry about. However, that is all taht i have gathered. If anyone else finds anything uot please keep me informed

---

### Post by ciscosurfer on 2006-10-04
That's interesting.  Do you think your onboard audio is fried?

---

### Post by n0dl on 2006-10-04
No i dont think so. My audio works just fine. i play music on it and the sound is good.

---

### Post by n0dl on 2006-10-04
Well I figured out what that message was. I occassionally get a message from the kernel saying this
```
error recieving uevent message: no buffer space available
```
as well... However I do not experience anything unusual (everything runs normal, audio, accessing files, wireless, etc)

---

