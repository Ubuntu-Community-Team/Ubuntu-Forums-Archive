---
title: "Wireless on my Laptop"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-08-02
I'm trying to get wireless to work on my laptop, a Gateway MX6433. Wired works perfect, i don't know where to start, can anyone help me please?

---

### Post by yuvlevental on 2007-08-02
start with network manager Administration->Network. If it doesn't work, try [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by amrclutch1 on 2007-08-02
In Network Manager there is only Wired Connection, I have tried following the instructions for ndiswrapper and it doesn't work when i do it, it gives me errors.

---

### Post by nadalizadeh on 2007-08-02
download and install ndiswrapper
then give it your Windows Driver File (inf extension)
It works fine for me.

then type this command
/sbin/ip a

you should see a wlan0 after reboot.

---

### Post by amrclutch1 on 2007-08-02
Thanks for the help! I finally figured it out, i love ubuntu :D

---

### Post by GaryLittlemore on 2007-08-02
Armclutch1 what wireless card are you using?

---

