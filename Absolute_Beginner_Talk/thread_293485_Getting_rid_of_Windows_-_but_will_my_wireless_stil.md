---
title: "Getting rid of Windows - but will my wireless still work?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by lwf on 2006-11-05
I am thinking about installing Ubuntu 6.10 on my computer. I have tried 6.06 on my laptop and on a server and I kinda liked it but I still don't have any real linux experience which I am now hoping to get.

Anyway, I got a Linksys WUSB54GS (connected to a WRT54GS with custom firmware and speedbooster deactiveted) that is working fine under Windows XP. Will it work with Ubuntu 6.10? I don't want to work for days with having it working since it already works with Windows. Could it even work with speedbooster? Because that doesn't even works on Windows. :)

Thanks for any advices!

---

### Post by think13 on 2006-11-05
Is the Linksys WRT54GS the name of your router?  Because determining whether Ubuntu would work with internet is more based on your wireless card in your computer.

I'm not logged into Windows right now, so I can't find how to find your wireless card in Windows... but I will get back to you if no one else helps you.

---

### Post by lwf on 2006-11-05
Sorry I was a little too fast there. WRT54GS is my router (which is not really important anyway) and WUSB54GS v1.0 is my card. USB-card to be more accurate.

---

### Post by think13 on 2006-11-05
[http://ubuntuforums.org/showthread.php?p=1642727](http://ubuntuforums.org/showthread.php?p=1642727)
Has a little about your wireless card.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Has information about all wireless cards supported, yours is not on the list, but that doesn't mean it wont work.

---

### Post by lwf on 2006-11-05
Thanks but I still got a WUSB54GS v1.0. Forget about the router, thats not important. ;)

---

### Post by think13 on 2006-11-05
One option would be to boot off the live CD or set up a dual-boot, and if the wireless card works for you then, I would say that it would work in the final installation.

---

### Post by jpeddicord on 2006-11-05
A word of warning:
6.06 has better wireless support than 6.10.

:-k

---

### Post by think13 on 2006-11-05
That's strange... why would they go backwards in wireless support?

---

### Post by mips on 2006-11-05
Stick with Dapper. Edgy is well, edgy to say the least.

It's not so much the wireless card you have but what chipset it uses that is important.

lsusb -v  should tell you the chipset in use by the wireless device if i'm not mistaken.

[http://www.ubuntuforums.org/showthread.php?t=40299](http://www.ubuntuforums.org/showthread.php?t=40299)
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

---

### Post by tortus on 2006-11-05
Yeah I sort of regret upgrading to Edgy. My wireless card works, but it's a little buggy: doesn't seem to find non-secure hotspots that broadcast their SSID (but finds secure ones just fine). And after I connect to a non-secure hotspot (by manually typing in its SSID), if I then go back to my own secure hotspot, I have to reenter the key.

6.06 just worked. I am seriously considering downgrading.

---

### Post by esaym on 2006-11-05
According to [http://www.linuxquestions.org/hcl/showproduct.php?product=3391&cat=144](http://www.linuxquestions.org/hcl/showproduct.php?product=3391&cat=144) it will work.  But for another $30 I am sure you can find something that will work better:mrgreen:

---

### Post by mips on 2006-11-05
> **esaym said:**
> According to [http://www.linuxquestions.org/hcl/showproduct.php?product=3391&cat=144](http://www.linuxquestions.org/hcl/showproduct.php?product=3391&cat=144) it will work.  But for another $30 I am sure you can find something that will work better:mrgreen:

As far as I know there different Versions of that device and what goes for one version is not the same for all versions. It's dependent on the CHIPSET in use, but I must add that card does not look promising.

[http://www.ubuntuforums.org/showthread.php?t=216031](http://www.ubuntuforums.org/showthread.php?t=216031)
[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)

---

### Post by lwf on 2006-11-05
Are you saying that edgy is worser than dapper? :o I was hoping that it would be better...

Dapper worked on my laptop and I installed Edgy on another laptop and the wireless worked fine there too (but still no wpa...). I still haven't tried any linux dist at all on my workstation because of this USB-adapter. Maybe ill should just stick to Windows. :S

---

### Post by mips on 2006-11-05
> **lwf said:**
> Are you saying that edgy is worser than dapper? :o I was hoping that it would be better...


For **me** it has been worse and I've been using ubuntu since Warty. My experiences with Edgy has not been pleasant so far, other people have had great experiences. Keep in mind that Edgy is using newer technologies under the skin. If you want stability stick with Dapper imho.

---

### Post by javaJake on 2006-12-09
If you are still looking for support on this device, I have a HOWTO for it here:
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

---

