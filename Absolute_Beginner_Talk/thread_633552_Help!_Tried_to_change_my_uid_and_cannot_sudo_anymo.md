---
title: "Help! Tried to change my uid and cannot sudo anymore"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by max69 on 2007-12-06
Hello,
I have been really stupid,I tried to change my user id with this comand
 sudo usermod -u 21 max
 and I have now lost the ability to acces anything as permission is denied and I cannot even sudo anymore. I tried to do the reverse comand
 sudo usermod -u 1000 max
but it gives me this message
 sudo: uid 1000 does not exist in the passwd file!
Please help me I am stuck. Thanks in advance

---

### Post by taurus on 2007-12-06
Boot into recovery mode from GRUB menu and run that command, without the sudo, again.

---

### Post by max69 on 2007-12-06
Thank you so much it worked !!!!!

---

