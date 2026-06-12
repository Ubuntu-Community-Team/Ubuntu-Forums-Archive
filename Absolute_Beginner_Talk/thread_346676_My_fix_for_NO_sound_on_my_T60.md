---
title: "My fix for NO sound on my T60"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by no24 on 2007-01-26
Hi,

I've been seeing a lot of posts on having lack of sound on T60 thinkpads (or other laptops).

I understand this may only solve a small number of those individuals' problems, but here was my issue.

I had to install alsamixer and unmute PCM.

Hopefully this helps?

btw I'm running edgy

---

### Post by deadgobby on 2007-01-26
Have you seen this link?
[https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT60?highlight=%28T60%29](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT60?highlight=%28T60%29)

Gobby

---

### Post by M0ses on 2007-03-25
hi all,

i had the problem too, i could`t get sound working. My solution:

BIOS->Config->Alarm->Volume Beep->Enable

reboot

afterwards i could disable volume beep in bios again and sound is still working.

hopefully this will help anybody

greets M0ses

---

### Post by kandagatla on 2007-09-06
Sound was working Normally on my machine.
I remember disabling system beep from preferences->sound menu.
After that day i was not able to hear the sound.
I to get the sound back i just had to undo the earlier step and unmute PCM in alsamixer.
Best of luck guys.
and Thanks for Hints.

-- Rgrds
Srinivas.Kangatla

---

### Post by Paul_K on 2007-11-29
I have been beating my head against this for a week now.  I tried changing the grub boot to acpi=off
seen here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)
[http://ubuntuforums.org/showthread.php?t=323797](http://ubuntuforums.org/showthread.php?t=323797)


I could not boot like this at all.  It would lock up.

After I installed gnome-alsamixer and unmuted it worked.  THANKS!!!! GUYS!!!!

-PaulK

---

