---
title: "Urgent problem concerning Grub"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by nilved on 2007-05-17
Hello, I'm having a very urgent problem on my dual-booted laptop. It is using Ubuntu 7.04 and Windows XP Professional. Previously, I had Ubuntu being the default inside /boot/grub/menu.lst, but changed default to 4, which should be windows. But this isn't the case! It now simply says 'GRUB' in the top left corner when booting?

What should I do? I need this computer to work for presentations. Thank you very much.

---

### Post by Bachstelze on 2007-05-17
You certainly made a mistake when editing your GRUB config. No worries though, you can use a Live CD to fix it :)

---

### Post by k33bz on 2007-05-17
can you show us what you have exactly in /boot/grub/menu.lst

---

### Post by nilved on 2007-05-17
> **k33bz said:**
> can you show us what you have exactly in /boot/grub/menu.lst
I can't really get onto the disc right now ... I kept it entirely at the defaults, except changed 'default 0' to 'default 4.'

---

### Post by k33bz on 2007-05-17
there had to be something else you accidently did, use a live cd to correct the problem

---

### Post by nilved on 2007-05-17
> **k33bz said:**
> there had to be something else you accidently did, use a live cd to correct the problem
I've got the laptop with me, luckily I backed up menu.lst first. I'll try to type out the non-commented parts, but it seems rather large. I'll edit this post with it in a minute if I can't sort it out myself. Thank you very much for your help, all of you.

---

### Post by starcraft.man on 2007-05-17
Just in case ya can't get GRUB fixed and working perfectly... my failsafe is always keeping a [GAG]("http://gag.sourceforge.net/") CD nearby, it'll make sure you can get in there if its urgent, it detects every flavor of OS out there I believe :)

You should be able to edit it from the Live CD though.

---

### Post by mikewhatever on 2007-05-17
When your PC boots, press Esc during the timer count down. You should then see the boot options, select Ubuntu manually, then, change the number to the right one.

---

### Post by nilved on 2007-05-17
> **k33bz said:**
> there had to be something else you accidently did, use a live cd to correct the problem
Hmm, I take back what I had said previously. I'm on the LiveCD right now, but can't get into /boot/grub, it's not there. What should I do?

---

### Post by k33bz on 2007-05-17
> **starcraft.man said:**
> Just in case ya can't get GRUB fixed and working perfectly... my failsafe is always keeping a [GAG]("http://gag.sourceforge.net/") CD nearby, it'll make sure you can get in there if its urgent, it detects every flavor of OS out there I believe :)

You should be able to edit it from the Live CD though.

i just scanned through that page, what all does that live cd do??

---

### Post by starcraft.man on 2007-05-17
[Link!]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

I believe thats what your looking for :)

---

### Post by starcraft.man on 2007-05-17
> **k33bz said:**
> i just scanned through that page, what all does that live cd do??

GAG is a great Bootloader, its my failsafe. It will scan any computers drive that are visible via BIOS and generate a new bootrecord of its own to access any and every OS installed. I have also never seen it fail, and it is fairly automatic :) It works with Windows Mac and I believe every Linux distro....

---

### Post by k33bz on 2007-05-17
> **nilved said:**
> Hmm, I take back what I had said previously. I'm on the LiveCD right now, but can't get into /boot/grub, it's not there. What should I do?

are you mounting your partitioned hd that has linux on it???

---

### Post by k33bz on 2007-05-17
> **starcraft.man said:**
> GAG is a great Bootloader, its my failsafe. It will scan any computers drive that are visible via BIOS and generate a new bootrecord of its own to access any and every OS installed. I have also never seen it fail, and it is fairly automatic :) It works with Windows Mac and I believe every Linux distro....

i think i am going to have to go get that. Thanks

---

