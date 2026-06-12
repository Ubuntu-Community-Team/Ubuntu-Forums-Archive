---
title: "keyboard issue on boot up of dual boot system"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Bagga on 2007-07-14
Hi all, 
I've been using Ubuntu for about 4/5 months now and this is my first post .  At the moment I am trying to set up a dual boot system xp for games and a specific programs and Ubuntu 7.04 for everything else. I successfully installed xp then successfully installed Ubuntu however when i reboot and the option for selecting which operating system i want to use comes up i am unable to choose due to my keyboard not working and after 10 or so sec. i am automatically logged into Ubuntu ( the 1st option ). I should point out that prior to this the keyboard is working as i can still get into the bios and as soon as Ubuntu is loaded it works away fine , also this is a preexisting error as in i had this problem before installing xp but ignored it as it was not causing any issues. 

If anyone can help or point me in the right direction that would be great , or if i can provide any more info just tell me how to get it and ill do my best :)

---

### Post by oilchangeguy on 2007-07-14
do you have another keyboard you can try? and you don't say if your keyboard is usb, or ps2. and you can buy a new basic keyboard for around $15.00.

---

### Post by Moop on 2007-07-14
I assume that you have a usb keyboard. 

You can try going in the bios and looking for a legacy usb setting and set it to enable. It could also be called usb host.

---

### Post by Bagga on 2007-07-14
yep a usb keyboard will try and set legacy usb setting to enable and see how it goes will let you know

---

### Post by Bagga on 2007-07-14
that worked fine i now have access to both os's,  thanks Moop, :KS

---

### Post by smoker on 2007-07-14
hi, sometimes also in the bios setup, there is a switch (yes or no) for the bios to release control of pnp, or external devices, to the operating system, or to retain control with the bios. if you have this option, try it either way and see what happens, sounds to me like the bios may be releasing control of the usb keyboard before the operating system can take over, hence you lose control at the grub screen.

just a suggestion,
best of luck

EDIT: a bit late! still glad you are sorted now :-)

---

