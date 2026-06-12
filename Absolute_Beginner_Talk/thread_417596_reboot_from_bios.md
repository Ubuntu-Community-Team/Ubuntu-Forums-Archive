---
title: "reboot from bios"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-21
Hello, how do I get back into my bios and set it to start from cd so as to put my windows xp cd in, It wont boot from restart when I press F1 F2 or F12 it goes directly to Ubuntu

Thanks
Sherri

---

### Post by taurus on 2007-04-21
On some computers, you have to press the Del key.  Do you still have the manual for your computer and what model/manufacture is it anyway?

p.s.  I always leave my BIOS to boot from the CD first.

---

### Post by delilahjed44 on 2007-04-21
Thanks for your reply.  It is a 8100 dell demensions.  

Sherri

---

### Post by Patrick K on 2007-04-21
> I always leave my BIOS to boot from the CD first.I do too. The system throws up an error about a failure to boot from the CD but then moves on to Grub.

---

### Post by delilahjed44 on 2007-04-21
Well then how do you leave your bios on?? I tried the del key it was non responsive, so I need to eliminate grub as I see it, what steps do I take to do this??

Thanks
Sherri

---

### Post by taurus on 2007-04-21
Are you sure F2 doesn't work with Dell?  Remember, you need to press it fast so I would recommend you turn on your computer and start pressing/tabbing F2 like crazy.

---

### Post by st33med on 2007-04-21
When it boots, hit F2 (I think.. I have a Dell laptop, so it should be the same) RAPIDLY! Now find the menu that says boot options(or something) and make CD's the first priorty. Exit by Esc.

However, sometimes the BIOS skips by the CD too fast. To manually boot from the CD, hit (again, I think) F12 again VERY RAPIDLY at boot. Now select CD and it boots off it!

If you are just using the CD once, just use the second option.

---

### Post by delilahjed44 on 2007-04-21
As I sais earlier, I did F1 F2 and F12, you must hit these keys rapidly or you will not get into the bios, I see Grub is the culprit, how do I get rid of grub??

Thanks
Sherri, see it starts to kick in then grub pushes throug and starts up Ubuntu.

---

### Post by dreadlord_chris on 2007-04-21
> **delilahjed44 said:**
> As I sais earlier, I did F1 F2 and F12, you must hit these keys rapidly or you will not get into the bios, I see Grub is the culprit, how do I get rid of grub??

Thanks
Sherri, see it starts to kick in then grub pushes throug and starts up Ubuntu.

First off - on the Dell Dimension 8100 you press the F2 key **during the POST** to get the BIOS menu.

Second, this is not a GRUB issue - GRUB does not start untill **after** your computer's BIOS loads and it performs the POST (power on self test). When you first turn on the computer and it shows the CPU & RAM installed & detects the hard drives - that is the POST.
After POST the computer's BIOS hands control over to whatever boot-loader is present.

---

### Post by oilchangeguy on 2007-04-21
press and hold the esc key. start the computer. you should get a keyboard error, and you'll be prompted to enter setup (bios).

---

