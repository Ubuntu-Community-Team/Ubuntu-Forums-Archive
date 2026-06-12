---
title: "Ubuntu 12.04 after installation and reboot in/output error"
date: 2012-09-27
forum: Apple Hardware Users
---

### Post by raleeha on 2012-09-27
Hello,    i am not sure if this is correct topic and right forum. But i don't know right now where to write down this topic. Sorry for that.    When i install Ubuntu 12.04 on a PowerPC the installation went well but after the system reboots it shows me an in/output error.   My suggestion is that yaboot seems correctly installed but the kernel will not found on the defined partition.    I tried to boot on yaboot command line following:  /boot/vmlinux /dev/hda3 root=/dev/hda3 video=ofonly  At the moment i dont know the correct error message what will be displayed.    If i remember correctly i had an ext4 partion for the ubuntu installation, an newworldboot partition for yabootloader in hfs format.    I will try to give more details but now i dont know how to do this. If you can guide me it would be appreciated.     Thank you in advance    Best regards    raleeha

---

### Post by raleeha on 2012-09-30
Hello,   i have solved that issue. When i install to a ext2 filesystem yaboot will find the kernel.   greetings   raleeha

---

