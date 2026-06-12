---
title: "usb session"
date: 2019-02-10
forum: Apple Hardware Users
---

### Post by j3984 on 2019-02-10
If you try Ubuntu on a Mac to see if it works and you have to install a wifi driver.... will the driver disappear when you close out the temporary USB session??
I saw a video on 18.04 and the wifi driver was already there..he was doing a Mac too..

---

### Post by howefield on 2019-02-10
Moved to "*Apple Hardware Users*"

---

### Post by gsahli on 2019-02-10
Many Broadcom chips are supported in Ubuntu. It's important to understand that Broadcom's firmware must be re-installed at every startup.
Not sure this answers your question.

---

### Post by kurt18947 on 2019-02-11
If you so choose, you may be able to do a full install to a USB flash drive. I've never used Mac hardware so keep that in mind. Assuming the installer is the same as PC, you create a live USB, boot it with a second blank USB drive plugged in. Boot the live USB and click "install". Here's where it helps to be familiar with disk terminology so as to install the boot loader to the proper location. If you install GRUB to the wrong location you may not be able to boot your MacOS. Being the coward that I am, I unplug/remove any hard drives before starting. That way I *can't* overwrite existing installations. If you 'hard drive' is soldered to the motherboard or is otherwise inaccessible this isn't an option of course.

This step isn't strictly necessary but if you're uncertain about terminology it's a way protect your existing install. On my machines this is quite simple. Once created a full USB install will work like a 'real' install and any changes or additions will be saved just like a real install. On PCs there is a key that can be pressed to select the boot drive, does Mac have that the same thing? Running a full Ubuntu install from a USB drive may be somewhat less responsive and less durable than installing to a hard drive but will give you a taste of "the real thing" with no risk to existing installs. I've had better luck with this using generic USB flash drives. I had some Toshiba flash drives that didn't seem to work well for full installs perhaps due to additional features. Micro Center  branded flash drives seem to work well for me and they're cheap.

---

