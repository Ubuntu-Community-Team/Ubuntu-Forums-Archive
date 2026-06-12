---
title: "Wine usage"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Loki1989 on 2006-07-14
what file does wine pull form on your hard drive i know its in c://windows but i got lost from there im using it to install a driver hopefully it works

---

### Post by echo $USER on 2006-07-14
I think you mean...
> 
/home/yourusername/.wine/drive_c

---

### Post by Kilz on 2006-07-14
> **Loki1989 said:**
> what file does wine pull form on your hard drive i know its in c://windows but i got lost from there im using it to install a driver hopefully it works

Wine is a kind of windows emulator. The wine program file is in /usr/bin . It stores windows program files in the .wine folder in you home folder. You may not be able to see it because folders with a . for the first character in thier name are normaly hidden.

---

### Post by Loki1989 on 2006-07-14
ok well when i tried to get my driver it went to soemwhere on my hard drive in my windows.

---

### Post by skale on 2006-07-14
I don't think wine willbe able to run drivers for hardware not supported by Linux. If it's a wireless network card, try searching "ndiswrapper" in the wiki.

---

