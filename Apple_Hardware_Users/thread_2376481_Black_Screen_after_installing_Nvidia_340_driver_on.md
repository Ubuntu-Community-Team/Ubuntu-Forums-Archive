---
title: "Black Screen after installing Nvidia 340 driver on Mac"
date: 2017-11-02
forum: Apple Hardware Users
---

### Post by alexinux on 2017-11-02
hi there!

I have Ubuntu 16.04 installed on a MacBook 13 2010 with an Nvidia 320m GPU. It's working fine with the nouveau drivers but if I want to do some gaming it requires the update from Nvidia. I've done it by downloading the recommended drivers from the website, and by the Additional Drivers app also and I get the same result......black screen after reboot and no login screen. I've seen some post about secure boot and other stuff but I haven't seen anything regarding the setup I have. Can somebody help? Anyone with a Mac that know how to get it working.

---

### Post by wildmanne39 on 2017-11-02
*Thread moved to **Apple Hardware Users for a better fit **.*

---

### Post by marvel.marv on 2018-02-10
Hi, I'm having exactly the same issue almost half year later. Did you manage to fix the problem?

---

### Post by newhacker1746 on 2018-02-19
> **marvel.marv said:**
> Hi, I'm having exactly the same issue almost half year later. Did you manage to fix the problem?

I have a MacBookPro6,2 with 330m + Ironlake Intel Graphics. I run 16.04.3 fully updated, and I ran some tests with dolphin-emu. I will try to get screenshots, but amazingly nouveau outperformed nvidia-340 by 4-5 frames consistently in many screens of Super Mario Galaxy 2, perhaps one of the most gpu-intensive games to emulate. I too have this issue, and have no idea how to fix it, but I feel that the nouveau driver today is really good, especially for Nvidia NV50, or tesla, for which it has great support and reclocking. Also, just in the name of supporting open source software. Ultimately, I just stood with nouveau. You may also want to look into power mode 0f and forcing it, which nouveau fails to switch to but can be switched into manually, netting you about 10fps more.

---

### Post by dragonier on 2018-02-24
> **alexinux said:**
> hi there!

I have Ubuntu 16.04 installed on a MacBook 13 2010 with an Nvidia 320m GPU. It's working fine with the nouveau drivers but if I want to do some gaming it requires the update from Nvidia. I've done it by downloading the recommended drivers from the website, and by the Additional Drivers app also and I get the same result......black screen after reboot and no login screen. I've seen some post about secure boot and other stuff but I haven't seen anything regarding the setup I have. Can somebody help? Anyone with a Mac that know how to get it working.

I am stuck with the same thing. Have a mac mini of 2010 with a Nvidia Geforce 320M. I installed different linux distros; manjaro, kde neon, debian, but end up having issues with the graphics card. Either screen tearing, browser
or video freezes-- with the nouveau card. Installing the suggested proprietary driver Nvidia-340 makes it boot into a black screen. I haven't been able to find an answer as to how to solve this issue. Hopefully someone has and will share it here.

---

### Post by dragonier on 2018-02-24
> **newhacker1746 said:**
> I have a MacBookPro6,2 with 330m + Ironlake Intel Graphics. I run 16.04.3 fully updated, and I ran some tests with dolphin-emu. I will try to get screenshots, but amazingly nouveau outperformed nvidia-340 by 4-5 frames consistently in many screens of Super Mario Galaxy 2, perhaps one of the most gpu-intensive games to emulate. I too have this issue, and have no idea how to fix it, but I feel that the nouveau driver today is really good, especially for Nvidia NV50, or tesla, for which it has great support and reclocking. Also, just in the name of supporting open source software. Ultimately, I just stood with nouveau. You may also want to look into power mode 0f and forcing it, which nouveau fails to switch to but can be switched into manually, netting you about 10fps more.

With the nouveau driver, your system doesn't freeze up on you?

---

### Post by dragonier on 2018-02-24
> **marvel.marv said:**
> Hi, I'm having exactly the same issue almost half year later. Did you manage to fix the problem?

Same here. Let me know if you have found a solution?

---

### Post by dragonier on 2018-03-01
OK guys. I hope you will check back in here because it looks like I have found the solution. I have been on the search for this for quite some time and have reinstalled my system for more than a dozen times. If you [follow this link]("https://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating/613573#613573") you'll see how it is solved. I have reinstalled kubuntu and everything seems to run fine now with proprietary drivers!!

---

