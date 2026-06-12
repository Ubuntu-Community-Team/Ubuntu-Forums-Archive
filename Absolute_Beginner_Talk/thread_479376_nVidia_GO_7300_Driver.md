---
title: "nVidia GO 7300 Driver"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by BertDelRio on 2007-06-20
Hi. I'm new to Linux and decided to try out Ubuntu 7.04. Since my company is currently evaluating the 64-bit version of Vista, I decided to dual boot my Asus A8JN laptop with the 64-bit version of Ubuntu.

The problem I have with Vista and Ubuntu is that they both do not have drivers for the monitor and built-in camera. Everything else is fine, though.

Overall, Ubuntu runs a lot faster, but Vista looks better. Please note that I'm just comparing Vista's Explorer and Ubuntu's Firefox. For some strange reason, Explorer renders pages much better. This didn't happen when I was running Firefox on Windows XP.

Notwithstanding the comparative looks, I am happy with Ubuntu. It installed drivers for my wireless and cabled LAN with no fuss. If I can get the 2007 versions of Office Project, and Vision to run on it, I probably won't use the company's Vista and switch to Ubuntu.

Anyway, my question is where can I get a driver for my monitor?

Asus doesn't seem to make Go 7300 drivers for the A8JN laptop. I tried checking DELL as I heard they'll be bundling Ubuntu with some of their GO 7300-installed laptops.

The lack of a driver is really frustrating.

Any help would be greatly appreciated.

---

### Post by cogadh on 2007-06-20
> **BertDelRio said:**
> Hi. I'm new to Linux and decided to try out Ubuntu 7.04. Since my company is currently evaluating the 64-bit version of Vista, I decided to dual boot my Asus A8JN laptop with the 64-bit version of Ubuntu.

The problem I have with Vista and Ubuntu is that they both do not have drivers for the monitor and built-in camera. Everything else is fine, though.

Overall, Ubuntu runs a lot faster, but Vista looks better. Please note that I'm just comparing Vista's Explorer and Ubuntu's Firefox. For some strange reason, Explorer renders pages much better. This didn't happen when I was running Firefox on Windows XP.
Run this in a terminal:
```
sudo apt-get install msttcorefonts
```
Usually the reason web pages don't display properly is because Firefox is trying to use different fonts than what the page was coded for. This will install the Microsoft True Type core fonts, which usually corrects the web page font issue

> Notwithstanding the comparative looks, I am happy with Ubuntu. It installed drivers for my wireless and cabled LAN with no fuss. If I can get the 2007 versions of Office Project, and Vision to run on it, I probably won't use the company's Vista and switch to Ubuntu.

Anyway, my question is where can I get a driver for my monitor?

Asus doesn't seem to make Go 7300 drivers for the A8JN laptop. I tried checking DELL as I heard they'll be bundling Ubuntu with some of their GO 7300-installed laptops.

The lack of a driver is really frustrating.

Any help would be greatly appreciated.
It's not the monitor that needs a driver, its your video card. Follow the instruction [here]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") to properly install your drivers.

---

### Post by BertDelRio on 2007-06-22
Thank you very much for the help!

---

