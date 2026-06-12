---
title: "Help"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by andrew_d_neal on 2007-06-01
My copy of Ubuntu came in the mail this afternoon. I put it in the CD drive and started to run it.(I have a portable drive) The Ubuntu browser opens up and I can choose to install five things.(Firefox, Thunderbird, Abiword, Blender, ClamWin) I want to install all of Ubuntu and the case my CD came in today says for me to simply put my Ubuntu CD in my drive, and restart or turn on my computer. When I do this though, Ubuntu doesn't install, or even start to, Windows just starts up like normal.(I'm using XP) What's the deal? Why wont my CD begin my Ubuntu installation? Why is it that when I reboot, Ubuntu doesn't install, Windows just starts right back up?

-Andrew

---

### Post by Lucifiel on 2007-06-01
Oh... you need to check your Bios and set it to boot from your cd drive.

Press F1 or Del to access Bios when the computer is starting up.

---

### Post by drowner on 2007-06-01
If you have an external CD rom, its probably a case that the BIOS on your computer is not set to boot from cds

Try restarting your computer, and when it turns on hit a few random keys: F1, F2, del, esc, one of the will bring you to a BIOS menus, where you should be able to tedit the order in which things boot.

It should be Cd then HDD, so that you can boot the Ubuntu CD.

Is your CDRom connected by USB? If it is, you may have a little issue, although maybe not.

---

### Post by raja on 2007-06-01
You have to set up your bios so that it boots up from the cd first and not the hard drive.

---

### Post by jonward0690 on 2007-06-01
Yea you need to hit F1 or delete or F12 and make your pc boot off the live cd.

---

### Post by Lucifiel on 2007-06-01
You will need to change your boot priority in your bios. 

Also, you will need to check which F# key will allow you to access Bios.

Edit: I suggest that you check the bios manual for your motherboard or your computer. Because every bios is different so we can only try to guess certain things.

---

### Post by starcraft.man on 2007-06-01
And just in case (since no one else posted)... here's a guide to installing via [Live CD,]("http://www.psychocats.net/ubuntu/installing") and this is about [partitions.]("http://www.psychocats.net/ubuntu/partitioning")

Have fun once ya get it to boot up :).

---

### Post by Lucifiel on 2007-06-01
Yeah , totally forgot about setting up and partitions.

To threadstarter: make sure you read these guides before installing Ubuntu. Otherwise, you could lose one of your partitions if you ain't too careful, man. :p

---

### Post by andrew_d_neal on 2007-06-01
My CD drive is connected by a USB. What's the problem?

---

### Post by Lucifiel on 2007-06-01
Oh this means that your motherboard must be able to support booting from a usb drive. 

Otherwise, you won't be able to boot using the Ubuntu Livecd.

What you can try:

Look in your motherboard manual or Bios for anything about "usb emulation" or something similar. 

Enable the option and if your motherboard can support booting from usb devices, you will be able to choose your usb cd-rom from the boot priority list.

---

