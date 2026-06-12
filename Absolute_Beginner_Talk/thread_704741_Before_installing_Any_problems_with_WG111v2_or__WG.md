---
title: "Before installing: Any problems with WG111v2 or  WG311v2?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by FireFreek on 2008-02-22
Before I waste a CD by burning Ubuntu on it, does Ubuntu have out of the box support for a WG111v2/WG311v2 wireless adapter? If not, how hard is it to get it to work, and will it work perfectly? I probably won't have any access to the internet once I install, so I want to make sure.

---

### Post by Crooksey on 2008-02-22
Is it a PCI card or USB, do you still have windows drivers?

---

### Post by zerhacke on 2008-02-22
[http://ubuntuforums.org/showthread.php?t=212365](http://ubuntuforums.org/showthread.php?t=212365)

---

### Post by FireFreek on 2008-02-22
WG111v2 is a USB, WG311v2 is a PCI card.

---

### Post by Crooksey on 2008-02-22
Well 99% of the time if you have windows drivers, ndiswrapper will work.

---

### Post by sennep on 2008-02-22
The WG111v2 might work out of the box, I've seen some people getting it to work with WEP 128 out of the box. Notice that there are two different versions of the WG111v2. I've gotten mine to work flawlessly with ndiswrapper and Wicd. See the link in my signature if you can't make it work out of the box.

---

### Post by dcstar on 2008-02-22
> **sennep said:**
> The WG111v2 might work out of the box, I've seen some people getting it to work with WEP 128 out of the box. Notice that there are two different versions of the WG111v2. I've gotten mine to work flawlessly with ndiswrapper and Wicd. See the link in my signature if you can't make it work out of the box.

My WG111v2 works with 7.10 "out of the box" - it is a "0846:6a00" and does not need any Windows drivers (and since I use the x64 version, none of the Windows drivers work anyway!).

I can get it to work with WEP or WPA with the native Ubuntu components - the only "issue" I have is that I have to have SSID enabled on my router for it to connect.

---

