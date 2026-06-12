---
title: "Adding a USB drive to grub??"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by yamfox on 2008-03-15
Hi, well I have a huge (physically) 120-GB USB portable harddrive connected to my computer which has Gentoo Linux installed on it. Any ideas on how to add it to grub? :confused:

---

### Post by herbster on 2008-03-16
Do you plan on having it permanently attached or will you be moving it back and forth between your box and another?

---

### Post by logos34 on 2008-03-16
> **yamfox said:**
> Hi, well I have a huge (physically) 120-GB USB portable harddrive connected to my computer which has Gentoo Linux installed on it. Any ideas on how to add it to grub? :confused:

If you're trying to boot ubuntu or another linux flavor on the usb, I'd suggest adding a [configfile grub entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") pointing to the root partition on the external.

---

