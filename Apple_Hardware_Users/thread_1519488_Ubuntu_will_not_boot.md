---
title: "Ubuntu will not boot"
date: 2010-06-28
forum: Apple Hardware Users
---

### Post by Tylerjd on 2010-06-28
Ok, so heres my problem. I boot into rEFIt and get a choice for Mac OSX and Linux. I choose linux, and then I just get a blinking cursor. Nothing more. It will not boot. I have also tried booting an Ubuntu install cd, and it has the same effect. I do not have access to an external display as I'm in an airport waiting for my plane. I'm running Ubuntu 10.04 on /dev/sda3, and Mac OSX on /dev/sda2. Help with this issue is greatly appreciated as Ubuntu is my main OS. Oh, and OSX boots fine.

EDIT: I should say that I'm advanced at using Ubuntu, and very comfortable with using the terminal. And I have data on the Ubuntu partition that i need. It is formatted EXT4

---

### Post by linuxopjemac on 2010-06-28
I think you should reinstall GRUB2 on /dev/sda

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Tylerjd on 2010-06-28
> **linuxopjemac said:**
> I think you should reinstall GRUB2 on /dev/sda

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I would, but Mac doesn't want to boot off any cd besides the Mac OSX install DVD. Windows, and many flavors of Linux will not boot.

---

### Post by linuxopjemac on 2010-06-28
Did you try booting with the Option key (Alt key next to Apple key) hold?

---

### Post by Tylerjd on 2010-06-28
I had to burn 3 different DVD-R's before it worked, but the weird thing is that now the first DVD is working. I'm now going to attempt to reinstall GRUB2. Ubuntu (on the HDD) is not working yet though.

---

### Post by (Julien) on 2010-06-28
Hi,

I have a similar problem, in my case I can only boot with the Option key pressed at startup. The first time the system hangs, then I reboot and it works. It seems reproducible...

Julien

---

### Post by Tylerjd on 2010-06-29
Sorry it took a while to reply. I fixed it by restoring an image made by clonezilla about a month ago. Now Ubuntu works fine. I tried reinstalling GRUB but that didn't work. I didn't loose any valuable data. Weird issue, hope it doesn't happen again. And yes I tried with the alt/option key.

---

