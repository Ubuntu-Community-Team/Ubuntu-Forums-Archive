---
title: "Unmount USB Flashdrive"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-19
Do I have to unmount my USB Drive before shutting down?

 In windows there is a 'safely remove hardware' button. Is unmounting similar to this, and is it done automatically at shutdown? (I don't want to ruin my USB Drive.)

---

### Post by Klaidas on 2006-05-19
You should unmount your usb drive. Yes, it is similar to "Safelly remove hardware".
```
umount /mount_point
```

---

### Post by aysiu on 2006-05-19
[QUOTE=Clay85]
 In windows there is a 'safely remove hardware' button. Is unmounting similar to this, and is it done automatically at shutdown? (I don't want to ruin my USB Drive.)[/QUOTE] Unmounting isn't just *similar* to "safely remove hardware"--it's the exact same thing. And, yes, shutting down will unmount the USB drive as well. But you don't have to shut down to unmount it. You can usually just right-click it and select *unmount volume*.

---

### Post by Clay85 on 2006-05-19
Yay! Thanks for clarifying. :)

---

### Post by meng on 2006-05-19
On a related note, my OCZ Rally 2 GB USB drive does _not_ have its light switched off after I unmount it (unlike when I use it with Windows). However, everything seems to be fine. I don't _think_ this is a problem - anyone else care to comment?

---

### Post by Clay85 on 2006-05-19
I have two USB Drives. On one the light only comes on while it's writing/reading. On the other the light comes on when I mount it, and stays on (even after it's unmounted). I think the latter USB Drive is a real peice, though. I sawed off the plastic case and cut a hole through it with my dremel so it would go on my keychain. It still works with a hole in it. xD (It never worked well anyway.)

---

### Post by aysiu on 2006-05-19
[QUOTE=meng]On a related note, my OCZ Rally 2 GB USB drive does _not_ have its light switched off after I unmount it (unlike when I use it with Windows). However, everything seems to be fine. I don't _think_ this is a problem - anyone else care to comment?[/QUOTE] Yes, this is a weird thing. I think most USB keys are designed for Windows. If I use my USB key with Windows, the light will turn off if I "safely remove" it.

If I eject it in Mac OS X or unmount it in Ubuntu, though, the light will stay on. I have not seen any adverse effects from removing it with the light on, though.

---

### Post by Klaidas on 2006-05-19
I'm having the same problem with light staying on when unmounted. Thank's for clearing it aysiu :)

---

### Post by meng on 2006-05-19
I should point out that after I unmount, I mentally count to 10 before physically removing the drive. The reason is that one day I pulled it out straight away, and when I got to work I found that none of the file changes had "taken". I probably don't need to wait so long but I'm never in much of a hurry.

---

### Post by Klaidas on 2006-05-19
Hmm, maybe your're right, meng. That's a pretty uselful advice :)

---

### Post by mcduck on 2006-05-19
The difference with the light is probably because linux unmounts the drive, but doesn't cut power from it.

For example, with linux I can plug in my iPod and unmount it, and it will still charge it's battery, but in windows after 'safely removing' the iPod it also stops charging..

---

### Post by Klaidas on 2006-05-19
When unpluging my "safely removed drive" in windows, it blinks for a sec. Should I worry about that? I mean, can I be sure that it doesn't get somehow mounted for 0.5 seconds and then removed not-safely?

---

### Post by meng on 2006-05-19
[QUOTE=mcduck]The difference with the light is probably because linux unmounts the drive, but doesn't cut power from it.

For example, with linux I can plug in my iPod and unmount it, and it will still charge it's battery, but in windows after 'safely removing' the iPod it also stops charging..[/QUOTE]
Cool! A difference between Linux and other OS that can honestly be labeled a "feature".

---

### Post by Miroku on 2007-05-24
why is it that when i delete stuff on my usb drive, i have to unmount it for the usb drive to allow me to use the free space i just made? it is not very convenient. or am i just doing it wrong?

---

### Post by Miroku on 2007-05-24
no clue anyone?

---

