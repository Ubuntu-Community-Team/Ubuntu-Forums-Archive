---
title: "How to install ATI Radeon 9600 Mobility drivers?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Sharky123 on 2007-12-03
Hello guys!

I hope you'll forget me for posting dumb things, I'm totally new to Linux. I've installed Ubuntu 7.10 yesterday on my laptop, which has a Ati radeon 9600 mobility card in it. After install, i was wondering around as normal user to see what video drivers were installed for this card, and i found that Ubuntu used some Ati universal mach driver, so (with my 'nothing will make it worse than it allready is-' windows attitude) i went ahead and changed the driver manually by model to 'Ati radeon'. This resulted in a maximum 640x480 resolution (which i am using now) and something tells me that my ati should be able to perform better. So i went to the Ati support website and downloaded some Linux drivers for my card. I got some file named 'ati-driver0installer-7-11-x86.x86_64.run'. The manual says that i should go with the terminal to the directory containing this file and just type the name of this file to start the installer. But when i do this, i get:
'sudo: ati-driver0installer-7-11-x86.x86_64.run: command not found'

I tried it as a normal user and with sudo. I dont really know anything more about linux than this, so I'm kind of stuck here. Can anyone point me in the right direction??

By the way: Ubuntu looks LOVELY :)

Cheers

---

### Post by gn2 on 2007-12-03
You could try using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Sharky123 on 2007-12-03
Hey thanks! Looks good, looks nice and noob-proof. I've read the accompanying notes of envy, and installed the package. It detected the graphics card correctly, and it downloaded something of about 45 Mb. Then it started installing something after which it said that the installation was complete. It told me to reboot, so i did. But now when i boot up, i can log in (resolution seems to be something like 800x600, but with very small charactersize and spacing), and.. i get a white screen with a white mouse pointer. Nothing more. I do hear the logon sound and it goes to sleep if i push the sleep button, but even in recovery mode i end up with a blank white screen.

Ehm.. help? (I'm using windows to type this message..)

---

