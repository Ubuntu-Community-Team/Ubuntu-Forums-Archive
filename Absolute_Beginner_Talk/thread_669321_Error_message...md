---
title: "Error message.."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by PedroCT on 2008-01-16
Hi there, i'm not completly newbie, but sometimes i get stuck on some problems. I was trying to compile Mercury language on ubuntu 7.10 with the most recent build-essential package. After doing configure and make i tried to do the last step which is make install. It started to compile but after a while i received the error message: No rule to make target 'de'

Can somebody please give me a idea? This happened before when trying to compile some other programs and allways ocurried while make or make install

---

### Post by jryprt on 2008-01-16
> **PedroCT said:**
> Hi there, i'm not completly newbie, but sometimes i get stuck on some problems. I was trying to compile Mercury language on ubuntu 7.10 with the most recent build-essential package. After doing configure and make i tried to do the last step which is make install. It started to compile but after a while i received the error message: No rule to make target 'de'

Can somebody please give me a idea? This happened before when trying to compile some other programs and allways ocurried while make or make install

Try  ```
sudo make install
```  Its just a guess .

---

### Post by dstew on 2008-01-16
Sometimes you have to have the **linux-headers** package for your particular kernel installed, if the program you are trying to compile is looking for linux-specific code. The command **uname -r** will tell you what kernel you have.

---

### Post by PedroCT on 2008-01-16
I'm already in SU... lol i'm not that newbie...

---

### Post by PedroCT on 2008-01-16
I found out that a friend of mine has the same problem...both of us are running the same operative system and have dual core pc's... the header name reported has:

 linux-headers-6.22-14 generic

---

### Post by PedroCT on 2008-01-16
lol last noticed problem, make clean does not work... reports as:

no rule to make target 'clean'

---

### Post by dstew on 2008-01-16
Did you install the linux-headers package?

---

