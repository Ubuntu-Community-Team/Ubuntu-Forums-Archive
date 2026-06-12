---
title: "Fesity Hangs for Minutes and then GDM appears...."
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by marianoi on 2007-05-06
Hello everyone...

I have this problem with my wife's Laptop. She's been using Ubuntu since Dapper and all the installations went great (well, sort of). But we have problems with Feisty.

I  tried with both the LiveCD and the Dist-Upgrade and I found the same problem. The thing is that the kernel boots fine until HALD, then the systems hangs for about 2 minutes and after that GNOME loads and everything else works fine.

The PC is a relatively old Averatec 3280 (AMD Sempron, S3 video, AC97 sound, 1GB RAM...). What I ended up doing was updating the system to Feisty and keep an old Edgy Kernel...So now she can boot using the Edgy Kernel into a Feisty Desktop...

Does anyone know what could be happening? What could have changed from Edgy to Feisty that makes this new Kernel hangs? (I mean, in our other PCs Feisty rocks!)

Thanks for helping!

Mariano

---

### Post by vadim.iablokov on 2007-05-06
I have the exact same problem with my Averatec 3270, but sadly I cannot figure out the cause of the hang up. Can you tell me how you updated to feisty but kept the edgy kernel?

---

### Post by marianoi on 2007-05-06
I Installed Edgy First. Then you should update it until you see no more updates coming on the Update Manager (this way you will have the latest Edgy Kernel).

Then do the Distribution Upgrade. If you do it this way the old Kernels will not be deleted (at least they were not deleted in my case).

Then you can change the GRUB menu list to always boot the old Kernel. For that do this:

```
sudo gedit /boot/grub/menu.lst
```

Then comment out (put  # in front of the line) the line corresponding to the new kernel, something like this (the new Kernel ends with 20.15):

```

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd1,5)
#kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=a43bdae4-997c-44af-b847-0960a33d8e85 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault
```

You could do the same thing with the "recovery mode" option. After that change the default Boot option to make it point to the old kernel. For that, in the same file, close to the top change the kernel number to whatever you like (if you like the old kernel and kept the recovery mode of the Feisty one, it should be "1", as it starts counting from "0").

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		1
```

Hope that helps. I believe (please somebody correct me if I am wrong) that you can keep in your "/etc/apt/sources.list" the Edgy critical update repo so your kernel keeps updating with edgy...

I would like to see this solved sooner than later. I wish I could file a Bug Report but I am not sure what the problem is as the system ends up booting!

Someone else having something similar?

Cheers

Mariano

---

### Post by vadim.iablokov on 2007-05-06
I found a possible solution that someone posted [here]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/319006274831") although it didn't work for me, maybe it will for you.

---

### Post by marianoi on 2007-05-06
Thanks a lot for the link...but unfortunately it did not work for me. What is even more annoying is the fact that there are absolutely no errors during booting...:confused:

---

