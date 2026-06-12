---
title: "No X on live cd??"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-03-13
I'm trying to convince my mom to let me switch her computer from XP to Edgy, she was close to letting me after I explained all of the great things ubuntu has that windows does not, but when i went to boot from the live cd there was no x. I know the cd is ok because it's the same edgy disk I used to install ubuntu on my laptop. I tried changing xorg.conf drivers to vesa but still no luck. Graphics are an ATi X300. Anyone have any idea??

---

### Post by Najand on 2007-03-13
You probably need to install ati fglrx driver. Look at Ubuuntu Community Page:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
for guidence to install it.

---

### Post by lamalex on 2007-03-13
installing fglrx requires a restart, I cannot restart and save changes in a live environment and I do not want to necessarily install ubuntu on this pc, i need to check other hardware compatibility. I know how to install fglrx my laptop is also ATi but live cd works with it. anyone else have any ideas?

---

### Post by Najand on 2007-03-13
I think just restart xorg is enough, if you are using Edgy of Dapper. I think you know that but for the record, you can restart xorg by pressing Ctrl Alt and Backspace simultaneously.

---

### Post by cyberdork33 on 2007-03-13
this is probably a stupid question, but you did download the live cd, not one of the others...

and now that we got that out of the way, what DOES it do? are there any errors on startup? does it just leave you at the terminal?

---

### Post by lamalex on 2007-03-13
ha yes it is a live cd, as I said in my post I know it works because I have used it to install ubuntu before. Multiple times. I boot to it, i get that fancy blue screen that tells me my xserver is not properly configured and then I'm dumped to a terminal. I tried changing the drivers in xorg.conf to vesa, which SHOULD work, but they do not for some reason. I have also tried ati, and radeon. Havn't been able to get it to load gdm.

---

### Post by lamalex on 2007-03-13
bump

---

### Post by cyberdork33 on 2007-03-13
That "blue screen" should ask if you would like to view the log... Look for lines that start with (EE)

---

### Post by lamalex on 2007-03-13
i will take a look next time I'm home. thanks.

---

### Post by lamalex on 2007-03-17
WITH ATI DRIVER:
(EE) No Devices Detected

If i try to start gdm from terminal it just fails regardless of driver (vesa, radeon, ati)

---

### Post by cyberdork33 on 2007-03-17
Found a HOW TO:
[http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X300](http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X300)


It says you don't have this issue with 6.10. Is this the version you are using?

---

