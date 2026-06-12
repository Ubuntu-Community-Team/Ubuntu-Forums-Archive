---
title: "Editing Grub Boot Timeout"
date: 2009-11-06
forum: Apple Hardware Users
---

### Post by Cerin on 2009-11-06
How do you edit the timeout value in Grub? I've found howtos that describe editing /etc/grub.conf or /boot/grub/menu.lst, but neither of these files exist in Ubuntu 9.10. I've tried creating them, with the value "timeout=3", but Grub still uses a different timeout.

---

### Post by sisco311 on 2009-11-06
Try startupmanager: [https://help.ubuntu.com/community/StartUpManager]("https://help.ubuntu.com/community/StartUpManager")

Click [here]("apt://startupmanager") to install it. 
To open it go to: System > Administration > StartUp-Manager.

---

### Post by buntuLo on 2009-11-06
> **Cerin said:**
> How do you edit the timeout value in Grub? I've found howtos that describe editing /etc/grub.conf or /boot/grub/menu.lst, but neither of these files exist in Ubuntu 9.10.
i just changed it, the file appears to be:
/boot/grub/grub.cfg
in my karmic installation. hope this helps.

---

### Post by sisco311 on 2009-11-06
> **buntuLo said:**
> i just changed it, the file appears to be:
/boot/grub/grub.cfg
in my karmic installation. hope this helps.

The grub.cfg file is not meant to be edited.

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")


[thread=1302743]Grub 2 - 5 Common Tasks[/thread]

[thread=1195275]The Grub 2 Guide[/thread]

---

### Post by Cerin on 2009-11-06
> **sisco311 said:**
> Try startupmanager: [https://help.ubuntu.com/community/StartUpManager]("https://help.ubuntu.com/community/StartUpManager")

Click [here]("apt://startupmanager") to install it. 
To open it go to: System > Administration > StartUp-Manager.

Thanks! That works perfectly!

---

### Post by buntuLo on 2009-11-06
thanks for pointing this out to me. i just changed it there and it worked, but i see the point of having custom configurations saved on a different file, nto changed in case of updates.

---

### Post by aeosynth on 2009-11-13
The file at /boot/grub/grub.cfg says that it's automatically generated using settings from /etc/default/grub. The "correct" way to change the timeout would probably be to edit this second file, then run 'sudo update grub'. That's what I did, and it works for me.

See [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202) for details on the config options.

---

