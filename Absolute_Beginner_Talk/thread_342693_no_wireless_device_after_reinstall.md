---
title: "no wireless device after reinstall"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by naomi on 2007-01-20
Hi, I had kubuntu installed on my laptop and wasn't too happy with it (although everything worked properly), so I thought I switch back to Ubuntu/gnome. I wanted a fresh install, so I installed from a Ubuntu DVD I got from a magazine.
Now here's my problem: after installation (text mode, since I have a dual boot setup) Ubuntu starts, but unfortunately my wireless device isn't showing up. if I do an iwconfig there is no eth1 showing up, just lo, irda0 and eth0 (LAN).
I once installed Ubuntu on the same laptop with the same DVD and everything was working from the beginning, so I have no idea what's going wrong now. I also tried to install kubuntu now, but again, no wireless device
When I do a lspci the network controller shows up as 
"Intel Coorporation PRO/Wireless 3945ABG Network connection"

Thanks for your help,
Naomi

---

### Post by mikewhatever on 2007-01-22
Intel Coorporation PRO/Wireless 3945ABG, that wireless card seems to be a tricky one. I had the same problem, when I first installed Ubuntu from an alternateCD/text mode. That CD was downloaded and burnt in the first days of November. Last week, I downloaded a LiveCD, and wireless worked out of the box, when running Ubuntu from the CD. They may have updated something, or LiveCD and AlternateCD are not quite the same. Anyway, see this post to get the idea how I solved it: [http://ubuntuforums.org/showthread.php?t=321045](http://ubuntuforums.org/showthread.php?t=321045)
To sum up, after installing restricted kernel modules and gnome network manager the wireless worked.

---

