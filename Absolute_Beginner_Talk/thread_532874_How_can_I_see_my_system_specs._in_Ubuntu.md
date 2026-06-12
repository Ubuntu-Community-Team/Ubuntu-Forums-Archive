---
title: "How can I see my system specs. in Ubuntu ?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by HaemoLacria on 2007-08-23
^ Like which video card

---

### Post by Dr Small on 2007-08-23
I know there is some commands for all of this, but if you just install "sysinfo", it's all GUI and you should be able to see most of your system specs in it.

```
sudo apt-get install sysinfo
```
Applications > System Tools > Sysinfo

Dr Small

---

### Post by mikeyphi on 2007-08-23
> **HaemoLacria said:**
> ^ Like which video card

System/Preferences/Hardware information
scroll through it all till you recognize something about nvidia or ATI

OR you could open a terminal and enter:
 lspci -x

within the output will probably be something associated with a VGA compatible controller

---

### Post by Dark Star on 2007-08-23
Or for huge and detailed Cpu info type this in Terminal

```
sudo lshw
```

---

