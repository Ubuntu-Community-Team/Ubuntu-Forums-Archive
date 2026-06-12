---
title: "XP on Hda5"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-02-17
g'day,
          Is there any way I can install Windows Xp on Hda5 without it
a) booting straight to windows when I want to start my computer and
b) having to install Windows before reinstalling Ubuntu and all my Hda1 goodies?
I feel I have had plenty of practise manually editing my partitions, etc. and am loking for a quicker way (can you install something like GAG in the Windows partition to get Linux to show up when the computer boots?)

any help would be grand    :)

---

### Post by Ocxic on 2006-02-17
i dunno if windwos will install to a logical partition, and i have a feelin it wont like it. theres no way to stop windwos from writing to the MBR so you'll have to re-install grub, if your installing windows after you've installed ubuntu.

---

### Post by carverj on 2006-02-17
will I need GAG to re-install GRUB? Do you mean in the windows filesystem? 
And how do I install them? Have never done it before. AAARGHH. whew, that's better
:confused:

---

### Post by carverj on 2006-02-17
A HOWTo on installing Windows partitions on Linux is what I need if such a thing exists.
:neutral:

---

### Post by pompeyjohn on 2006-02-17
Another option would be too use a third party extended mbr tool. Bootit NG by Terabyte will do what you want. I dont know of any free tools that can though, sorry.

---

### Post by carverj on 2006-02-17
HAHA, will just have to cancel all appointments and do it the old fashioned way huh (install Windows, install Ubuntu again, add repositories or run Automatix script, link home partition to fstab)?
Does anyone recommend using GAG? I believe I tried it once before without success. may give another try. 
:-k

---

