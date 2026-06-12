---
title: "HELP a chromeOS user in dev-mode"
date: 2013-02-24
forum: Any Other OS
---

### Post by crummychrome on 2013-02-24
:icon_frown::icon_frown::icon_frown:Please help:

I've been dual-booting my ACER C710 Chromebook with ubuntu formally known as "ChrUbuntu". the first install of Ubuntu while running my chromebook in dev-mode, I set the partition option to 200. I think that is too low for not using the ChromeOS and I want to resize the partition and remove all the previous ones. please tell me what commands or scripts I have to run in order to  resize the partition and possibly remove previous installations of Ubuntu to free up disk space. this chromebook has 320gb And I believe 200ram. I am very new to all of this and have done numerous researching to solve this issue but I have gotten no answers yet. I am looking for fast responses, Thx.

---

### Post by oldos2er on 2013-02-24
Moved to Other OS/Distro Talk.

---

### Post by crummychrome on 2013-03-02
time for me to start studying...:P

---

### Post by darkcrimson on 2013-03-04
If you want to resize or add/remove partitions; boot into an Ubuntu livecd and take a look at Gparted. It's a graphical tool that will allow you to make all of the above changes very easily with minimal hassle.

---

### Post by oldrocker99 on 2013-05-28
It should be noted that using GPartEd within Chrubuntu is very likely to render the system unbootable. The best way to increase the size of your Ubuntu partition is to back up everything you do have saved in /home using your Google cloud space your machine still has available, even under Ubuntu, using Chrome. Then boot into Chrome, and make a USB ChromeOS recovery disc by typing

chrome://imageburner

into the Chrome address bar and follow the instructions. Then turn the box off, and hold down the power button, ESC and F3. You'll get a "Chrome OS is missing or damaged" message, at which point you insert the USB drive you just made. Let the ChromeOS install itself, and reboot.

Turn the machine off again, and reboot the same way. When you get the message about ChromeOS again, hit ctrl-d until you get asked if you want to enter developer mode. Hit space to enter developer mode, then wait for it to reboot into ChromeOS.

Then, follow the instructions you already did to install Chrubuntu, giving yourself a larger partition. Restore your stored files, and you're good to go, aside from reinstallation of the software you had before.

---

