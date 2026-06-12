---
title: "Cant boot ubuntu 6.04"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Gleeed on 2006-03-18
Hello.
I have windows on C: and just installed ubuntu 6.04 on a new empty harddrive ( E: ) and now when I'm booting the computer I cant choose OS, It only load windows, what has happend ?

---

### Post by Ramses de Norre on 2006-03-18
Did you install grub? Otherwise you'll have to install it using the live cd.

---

### Post by steve.horsley on 2006-03-18
Does it give you a choice menu? The GRUB bootloader should give you a list of availabl OSs. Or does it immediately boot windows just like it always did? 

If the latter, then it would seem that the GRUB didn't get installed properly. I'm not sure what to do about that except try and run the installer again. I thnk the bootlosder needs to go on the C: drive - probably /dev/hda.

---

### Post by Ramses de Norre on 2006-03-18
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")

---

### Post by steve.horsley on 2006-03-18
Of course! Doh!

---

