---
title: "Will Linux dual boot with windows well"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by win98 on 2006-09-06
Hi guys Im installing linux on my main pc which currently runs windows. Is there an easy way to keep both os's seperate wiithout getting a second harddrive as im very low on cash.
Im a complete noob to linux but I can to technical things on computer. Thanx in advance

---

### Post by bigken on 2006-09-06
yep just use custom partioning when you install ubuntu from the live disc or you could also download qtparted boot disc and partion the drive 1st then install from the alternative ubuntu disc you must defrag the windows disc 1st ;)

---

### Post by win98 on 2006-09-06
I just wanted to add my windows is windows xp home edtion and I really need to know is it possible to make grub come up with a menu so I can chosse which os I use. Also thanks for telling me about the partitioning thing so sort out that bit.

---

### Post by bigken on 2006-09-06
yes ubuntu does this for you ;)

---

### Post by cotcot on 2006-09-06
When you are not sure you can install ubuntu with the alternate installCD and install the bootloader of a floppy. Floppy in will give you the grub boot menu; floppy out will boot you direct in XP. 
During install do not install the bootloader to the MBR ; install it to /dev/fd0 'this is only possible with the alternate install CD). After the installation you have to make your XP partition active again with fdisk.

---

### Post by win98 on 2006-09-06
Thanx for the replys I hope my version 6.06 lts cd that I ordered for free from the site. becuase I dont have a good internet connection will let me do that thnx again

---

### Post by steve.horsley on 2006-09-06
Assuming that windows occupies the whole disk at the moment, do the following:
0) Take a backup of all your important data, just in case.
1) defrag windows, maybe 2-3 times, then shut it down.
2) Boot the Linux installer CD
3) Start the installer and take the option to shrink the windows partiton in order to make room for Ubuntu.

P.S. The installer creates a boot menu and makes Ubuntu the default, but you can change that later if you want.

---

### Post by slibuntu on 2006-09-06
I just went thru the installer and it works great, grub was set up automatically so i can choose between xp and ubuntu, i've been running it for about a month now with no problems (touch wood), i'd recommend it!

---

