---
title: "Can not boot from my USB (Macbook Pro)"
date: 2021-12-26
forum: Apple Hardware Users
---

### Post by leon6j on 2021-12-26
I have a Macbook Pro (16inch 2019 version), and my goal is to have a dual boot system by installing Ubuntu 20.10.

Unfortunately, I have been unable to boot the computer from my ubuntu enabled USB drive. I would hold the "option" button while starting, and then see two options, my Mac OS hard disk and a EPI disk. I would choose the 2nd choice and let it boot from there. No matter how long I waited, I can only saw a black screen. I did hear some noise in the background though. 

I tested the USB stick with my other computer (Dell XPS laptop), and it worked fine. I also logged into the Recovery mode (Command + R) and change the setting to allow bootable from external devices. 

I wonder if anyone has success in booting from a USB stick on their Macbook Pro laptops?

Many thanks!

---

### Post by guiverc on 2021-12-26
Ubuntu 20.10 (*along with all flavors*) is ***End-of-Life***

- [https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/](https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/)
- [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you're planning to use the device off-line it won't matter, but I'd still recommend a supported release of Ubuntu  (*don't forget EOL media cannot access repositories of software as they're hardcoded for the address where supported releases store archives, so unless you manually overcome this experience may differ to what it was when release was supported*).

---

### Post by MAFoElffen on 2021-12-26
I can boot Ubuntu 20.04 LTS fine on mine, Macbook 13" (2007),  made from Rufus with the EFI and GPT partition table options. 

My lessons learned with MAC:

The important thing for MAC is that any USB Boot media has to be made with a GPT partition table or it will refuse to boot. It will not recognize MBR.

---

### Post by leon6j on 2021-12-27
Many thanks for the information.

Funny that Rufus can only run on Windows and Mac prefers that way of creating a bootable USB.


> **MAFoElffen said:**
> I can boot Ubuntu 20.04 LTS fine on mine, Macbook 13" (2007),  made from Rufus with the EFI and GPT partition table options. 

My lessons learned with MAC:

The important thing for MAC is that any USB Boot media has to be made with a GPT partition table or it will refuse to boot. It will not recognize MBR.

---

### Post by slickymaster on 2021-12-27
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by MAFoElffen on 2021-12-28
Here is the instructions to do it form Mac Hardware:
[https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview)

See the 'note' they said about what they said on Mac's only booting media with a specific type of partition table, which they mention at the bottom of page #1, which I mentioned above was 'GPT' type partition tales.

---

