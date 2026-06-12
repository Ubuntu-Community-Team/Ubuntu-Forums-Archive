---
title: "No Sound / Muted Sound"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Soft Earlobes on 2008-01-24
Hello. I'm new to Linux. I'm using Ubuntu Gutsy Gibbon on my laptop (HP Pavillion dv6648se).

The sound is somehow muted, even though it says on the screen that it's not. The light on the keyboard that would usually turn blue if the sound was unmuted glows orange. The sound is fine on Windows, though. Help, please.

Thanks in advance.

---

### Post by Soft Earlobes on 2008-01-24
Anyone?

---

### Post by Soft Earlobes on 2008-01-27
Help, anyone?

---

### Post by Majorix on 2008-01-27
Try alsamixer and see if all volumes are maxed. Run terminal (Applications > Accessories > Terminal if you are on Ubuntu) then type this:
```
alsamixer
```
Use left-right arrow keys to move around and up-down arrow keys to change the volume. Make sure all is maxed out and then press Esc to exit the program. Then try running a sound file again to test.

Hope it works.

---

### Post by Soft Earlobes on 2008-01-27
They were turned all the way up. I ran a file and there visualizations on the music player but no sound.

---

### Post by Majorix on 2008-01-27
Have you run previous Ubuntu's or other Linux distros on that computer before? Maybe the kernel has problems with your sound card.

---

### Post by Soft Earlobes on 2008-01-27
> **Majorix said:**
> Have you run previous Ubuntu's or other Linux distros on that computer before? Maybe the kernel has problems with your sound card.
No, should I reinstall?

---

### Post by Majorix on 2008-01-27
No I didn't say you should install them. I was asking if you successfully ran one. You could probably try a Linux LiveCD distro and see if it is a kernel issue or a problem with the configuration. Just download Damn Small or something as small as that one.

---

### Post by Soft Earlobes on 2008-01-27
Ok.

---

