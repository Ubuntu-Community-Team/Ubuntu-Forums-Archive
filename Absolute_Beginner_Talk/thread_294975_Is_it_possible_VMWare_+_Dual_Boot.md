---
title: "Is it possible? VMWare + Dual Boot"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2006-11-07
Is it possible to partition my hard-drive to have Windows XP and Linux, but be able to access the Windows XP through a VMWare Server in linux also?

So, I have the ability to boot just into Windows XP if I want to, or if I want to run Windows XP from Linux, I can.

---

### Post by David Corrales on 2006-11-07
Yes you can, but the windows copy won't be the same. They'll be separate copies, and probably, you'll need 2 licenses lol.

---

### Post by Bachstelze on 2006-11-07
In theory, it is possible to use a physical partition in VMWare but there will be a problem regarding your hardware. When you will run your windows "normall" (i.e. chosing it at boot time), it will install drivers for your real hardware and when you will boot it from your VM, it will have it's virtual hardware => problems. It's like installing windows on a computer then take he drive away and boot it in another. It may or may not work but not without problems.

---

### Post by Klaidas on 2006-11-07
Well, you could do that with separate installations... but if you mean, like, to be able to access one windows installation in two ways, then I think not.

---

### Post by ifross on 2006-11-07
It is possible, I tried it but I got an error and it wouldnt boot in VMWare, you have to create two hardware profiles in windows and choose the correct one when you boot (one for actual hardware, one for VM hardware)

Here is the article I used to try:
[Here](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

you might have better luck than I did :)

---

