---
title: "xorg gone gutsy"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-10-31
this is just 1 of a few things thats gone wrong.cant boot up gutsy and sound is gone, slider for vol adj is missing. i may just reinstall but i have some pic folders to get off of it. im wondering if resubuntu will work with gutsy. also i if it will are instructions cear on what line commands to use?

---

### Post by overdrank on 2007-10-31
> **trucker33377 said:**
> this is just 1 of a few things thats gone wrong.cant boot up gutsy and sound is gone, slider for vol adj is missing. i may just reinstall but i have some pic folders to get off of it. im wondering if resubuntu will work with gutsy. also i if it will are instructions cear on what line commands to use?

Hi and could you explain what happened to the xorg and we maybe able you help you get it going. And have you tried to reconfigure your xorg from recovery mode?

---

### Post by trucker33377 on 2007-10-31
when i boot up i go to black screen to login not my desktop. i think ive got this really messed up grub is not working right. i have to use super grub disk to even boot

---

### Post by overdrank on 2007-10-31
> **trucker33377 said:**
> when i boot up i go to black screen to login not my desktop. i think ive got this really messed up grub is not working right. i have to use super grub disk to even boot

Ok then you can try  when you reach the blank screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line hopefully.  Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure  xserver-xorg
``` choose vesa as the driver answer a few questions. if you dont know the answers then leave as default answer given. when complete use the command to reboot ```
sudo reboot
``` If you can not get to the terminal this way then try and boot in recovery mode which is the second choice in the grub. Hope this helps and good luck!

---

### Post by Maestro23 on 2007-10-31
> **overdrank said:**
> Ok then you can try  when you reach the blank screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line hopefully.  Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure  xserver-xorg
``` choose vesa as the driver answer a few questions. if you dont know the answers then leave as default answer given. when complete use the command to reboot ```
sudo reboot
``` If you can not get to the terminal this way then try and boot in recovery mode which is the second choice in the grub. Hope this helps and good luck!

Make sure you pick your Display resolutions.

---

### Post by trucker33377 on 2007-10-31
thxs ill try got to head out to work now ill let you know if i get back to my desktop

---

