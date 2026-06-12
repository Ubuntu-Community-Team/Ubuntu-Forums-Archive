---
title: "Ubuntu 7.4 with Intel pro 1000"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by mcaycedo on 2007-08-27
I have installed Ubuntu v7.4 on a Dell Dimension E521 with AMD64 processor.  The built-in ethernet controller is only 100Mps and I went ahead and Installed Intel pro 82540EM (Gigabit) and disabled the built-in ethernet.  Do I need to install the linux intel driver for the Intel Pro?  Ubuntu seems to recognize the Intel board but I have to reboot the machine (cold start) a few times already and running with the built-in controller seems to be okay.
Any advise?

---

### Post by gobbles414 on 2007-08-28
I assume that you've looked in system --> administration --> restricted driver manager...?

---

### Post by mcaycedo on 2007-08-29
The only controller under restricted is the NVIDIA.  Where do I look to make sure it is using the right drivers and has recognized the Intel Pro board?

---

### Post by gobbles414 on 2007-08-29
mcaycedo,

To be honest, I am a little confused by your original post. If I understand correctly, your hardware is gigabit ethernet. But Ubuntu is only recognizing it as being capable of 100Mps. Therefore, you are trying to use a driver that will help Ubuntu to use the full gigabit capabilities of your hardware. Am I understanding correctly...?

---

### Post by mcaycedo on 2007-08-29
I did not mean to confuse you.  The Dell pc comes with a built-in 100mb on the motherboard that I disabled via Bios.  I installed an Intel Pro 82540EM card (Gigabit) to comunicate with my Gigabit switch.  I have a total of 9 computers (Dell e521) and I have two of them which keep freezing with the Intel controller; I removed it and used the built-in 100 and worked fine.  Should I install the latest Intel driver?

---

### Post by gobbles414 on 2007-08-29
Hi again mcaycedo,

I would say if 7 of 9 computers are working, something must be different with the other two -- or the way in which they are connected to your switch. Maybe some ports are defective. Re-enable the ethernet cards and then take your two malfunctioning computers and trade connections with two of your working computers. Also any differences in hardware or software could be important to consider. Something as seemingly insignificant as being hooked up to external speakers could make a difference. Keep me informed on your progress, please.

---

### Post by mcaycedo on 2007-08-29
Hi,

Thank you very much for trying to help me solve my problem.  I will be able to work on this next week since I am currently out of town.  By then, I will try your suggestions and will let you know of my results.

---

### Post by gobbles414 on 2007-09-12
mcaycedo,

How are you progressing with this issue?

---

