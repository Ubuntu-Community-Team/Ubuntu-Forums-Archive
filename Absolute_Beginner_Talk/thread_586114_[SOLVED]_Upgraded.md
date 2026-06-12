---
title: "[SOLVED] Upgraded"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-10-22
Ok up graded from 7.04 to 7.10 on clean install. Open office error again and cannot install nvidia driver. How can I get it installed through the terminal again? I am drawing a total blank, maybe been at this too long today.:lolflag:

---

### Post by cfaulkner on 2007-10-22
sudo apt-get install nvidia-glx-new

---

### Post by ezak on 2007-10-22
sudo apt-get install nvidia-glx 
(for older gfx cards)

or: 

sudo apt-get install nvidia-glx-new 
(for newer gfx cards, your most likely option)

As for your OpenOffice problem, I would recommend:

sudo apt-get remove openoffice.org 
(remove)

sudo apt-get autoremove 
(remove dependencies)

sudo apt-get install openoffice.org 
(clean install)

---

### Post by J11Gyro on 2007-10-22
thanks drew total blank  now any ideas about dependency problems with open office? same errors I have been getting during updates will try that and see what happens Thanks again

msi board
XP2400
1.5gig ram 
Nvidia 5200 128 meg
dual boot with XP on 80 gig and 
ubuntu on slave 40 gig

---

### Post by J11Gyro on 2007-10-22
Thanks all worked :):)  now 1 more question how do I get the nvidia control panel back?

---

### Post by ezak on 2007-10-22
Cheers. 

For the Nvidia Control Panel,  just simply type:

nvidia-settings

---

