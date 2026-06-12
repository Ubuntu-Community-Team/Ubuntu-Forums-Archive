---
title: "Getting stuck while trying to usb boot Ubuntu 16.04.2 on a Macbook Pro"
date: 2017-05-09
forum: Apple Hardware Users
---

### Post by bradleybare on 2017-05-09
Thank you for the help.

I am currently trying to boot ubuntu on a mac so I can replace OSX completely. I have attached a photo of my mac specifications below.

[ATTACH=CONFIG]275021[/ATTACH]

My problem is in the boot phase. I can get into the bootloader and choose try ubuntu without installing. I also add "nomodeset" to the boot parameters. I have even tried by also removing "splash" and "quiet" from the boot params.

 My problem arises at the end of the boot phase. It is hard for me to explain but the computer freezes with a black screen and an underscore in the top left corner. The underscore is not flashing. It is frozen solid. The usb has a light in it and the light stops blinking at this point. I also attached a picture of the underscore. I will try to upload a boot video to see if someone can find a solution. 

[ATTACH=CONFIG]275020[/ATTACH]

I've waited up to an hour to wait for something to happen. Nothing yet.

This is killing me. I have a chromebook with ubuntu but I need more space. I decided to screw OSX and install ubuntu.


EDIT: I am using the AMD 64 iso. The 32 bit iso doesn't show up refind so I have to use 64 bit. My mac is also 64 bit.


Thanks again. Any questions are welcome!

---

### Post by bradleybare on 2017-05-09
I have been looking through the output code and right before the blank screen I am getting

ERROR: firmware file "b43/ucode29_mimo.fw" not found.

It then tells me to go to a website and follow instructions. go to wireless.kernel.org/en/users/Drivers/b43#device firmware. 

I think this is only for the wifi. I can deal with that later when it boots. If I am wrong please lead me in the correct direction. Thank you!

---

### Post by deadflowr on 2017-05-09
*Moved to **Apple Hardware Users** sub-forum*

---

### Post by bradleybare on 2017-05-09
I tried to boot without nomodeset, splash, and quiet and it froze at this point.

[ATTACH=CONFIG]275027[/ATTACH]

---

### Post by bradleybare on 2017-05-10
Well I figured it out. 

I had to add

outb commands

and

radeon.modeset=0 i915.modeset=1 and it booted.

Thread Solved!

---

