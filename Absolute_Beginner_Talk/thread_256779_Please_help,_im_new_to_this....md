---
title: "Please help, im new to this..."
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by blunt1 on 2006-09-13
:confused: I have installed ubuntu for the first time yesterday and i am having problems connecting to the internet.

im now getting a message when i log on saying:
Could not look up internet address for blunt1
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
blunt1 to the file /etc/hosts.

i can still log in though...

i have looked on the internet for answers but i dont understand what to do!?

Also, i cant open "networking" in system/administration but i could before... i think i may have cause the problem by trying different things  to get my internet connection working...](*,) 

hope someone can help!

cheers, j

---

### Post by PPAAUULL on 2006-09-13
I would just do what it says and add it to the file

---

### Post by blunt1 on 2006-09-13
> **PPAAUULL said:**
> I would just do what it says and add it to the file
How do i do it?

---

### Post by jolan_jj on 2006-09-13
Whats your /etc/hosts ? In terminal do ```
sudo gedit /etc/hosts
```. The first two lines should look like ```
127.0.0.1 localhost blunt1
127.0.1.1 blunt1
```
Save the file and reboot.
Hope that will help :)

J

---

### Post by steve.horsley on 2006-09-13
It sounds to me like you have changed your computer name somehow. Changing the computer name has to be done in two files:
**/etc/hostname** should contain the computer name **only**.
**/etc/hosts** should contain the hostname to the right of **127.0.0.1** along with the alias **localhost.**

If you ever change the hostname so the two files disagree, then sudo stops working. You can use the GUI network configuration tool to change the hostname (assuming you can use sudo), and this changes both files.

If you have broken sudo by changing one file only, you will need to boot into recovery mode (which makes you root), and use these two commands to fix them:
nano /etc/hostname
nano /etc/hosts

HTH
Steve

---

### Post by blunt1 on 2006-09-13
I have re-installed ubuntu now, no probs after logging in... 

Thanks everyopne for your help!!!:D 

I still cant connect to the internet?! any ideas?!:-k 

Thanks

---

### Post by jimrz on 2006-09-13
> **blunt1 said:**
> I have re-installed ubuntu now, no probs after logging in... 

Thanks everyopne for your help!!!:D 

I still cant connect to the internet?! any ideas?!:-k 

Thanks

need a bit more info...

what type internet connection? dial-up/dsl/cable
what make/model modem?
wireed/wifi/usb?

whatever setup you have there are almost certainly people here who have similar and can provide iseas on how to get it going

---

### Post by steve.horsley on 2006-09-14
And start a new thread with that info (with an appropriate title) - people are unlikely to read this one far enough to find a new question raised 9 posts down.

---

