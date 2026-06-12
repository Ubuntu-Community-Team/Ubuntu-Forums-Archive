---
title: "Help Installing NVIDIA Restricted Driver"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by whitedragon551 on 2008-04-07
Under the restricted drivers it says I need a NVIDIA GLX New driver. I downloaded the latest I think and tried to install it and it gives me an error and wont install.

---

### Post by keeler1 on 2008-04-07
what error does it give?

You might need to enable some repositories for this to work.  

If your using 7.10 and possible 7.04 as well (I am not sure however)  open up the file folder /etc/apt and double click on sources.list.

An application should launch called Software Sources.  On the first tab there is a menu option that says "Software restricted by copyright or legal issues (multiverse)".  Make sure this checkbox is checked.

---

### Post by whitedragon551 on 2008-04-07
It was Gutsy Gibbon 7.10. But after that driver I cant boot into recovery mode or anything. After the boot screen everything goes black. Apparently I wasnt supposed to have a linux distro.

---

### Post by overdrank on 2008-04-07
> **whitedragon551 said:**
> It was Gutsy Gibbon 7.10. But after that driver I cant boot into recovery mode or anything. After the boot screen everything goes black. Apparently I wasnt supposed to have a linux distro.

Can you reach the command line with the keys ctrl, alt, F1. To reconfigure your xorg.

---

### Post by Therion on 2008-04-07
You're booting off the hard drive, correct?  Sounds like the nVidia Black Screen of Death...  Can you boot to the desktop using Safe Graphics Mode?

Edit:  Ah... **overdrank** is here.  You're in good hands!

---

### Post by whitedragon551 on 2008-04-07
I can get to Vista fine. When I go into Ubuntu it doesnt work and gives me the black screen. yes I am booting off the HD. 

Overdrank I have no idea what your talking about. Im new to this.

---

### Post by overdrank on 2008-04-07
> **whitedragon551 said:**
> I can get to Vista fine. When I go into Ubuntu it doesnt work and gives me the black screen. yes I am booting off the HD. 

Overdrank I have no idea what your talking about. Im new to this.

Hi and if you see the grub and choose Ubuntu then when the screen goes black try the keys ctrl, alt, F1 and then see if you reach the command line. Login with user name and password and then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` when complete use the command sudo reboot. Hopefully this will get you back to the desktop (GUI)

---

