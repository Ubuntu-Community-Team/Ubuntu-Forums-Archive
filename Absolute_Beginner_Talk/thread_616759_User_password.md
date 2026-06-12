---
title: "User password"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by quadrantids on 2007-11-18
When I installed Ubuntu 7.10 (this evening) the installer asked me for a user name and password. Whenever I start up Ubuntu, the system asks me for these. I then tried to download and install compizconfig, at which point I was asked for my password (presumably the same to boot Ubuntu). The system told me the password was incorrect. I thought I must have made a typing error, but it keeps telling me it's incorrect.

I then shut down the computer and rebooted, just to make sure I hadn't forgotten my password. 

Can anyone please tell me why my password doesn't work to install new programmes (or simply to access the "administration" menus?

Thanks

---

### Post by gn2 on 2007-11-18
Did you create more than one user during the installation process?

If you did then use the first username/password you created to change the system.

If that doesn't work, try resetting the password: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by quadrantids on 2007-11-18
I don't think so, but I'll try using the link you suggest: thanks.

---

### Post by quadrantids on 2007-11-20
Thanks for your help: the problem seems to linked to my French keyboard. When I installed Ubuntu the cd installer considered my keyboard to be QWERTY. Although I use Ubuntu in English, to faciliate my work, I subsequently told Ubuntu to use a French keyboard AZERTY. In other words if I use Terminal, I have a QWERTY keyboard, but when I use the GUI I have an AZERTY one!

I don't remember being asked when I installed Ubuntu whether I had a QWERTY keyboard or not. Is there a way of telling it now?

Thanks once again.

---

### Post by gn2 on 2007-11-21
> **quadrantids said:**
> 
I don't remember being asked when I installed Ubuntu whether I had a QWERTY keyboard or not. Is there a way of telling it now?

Thanks once again.

There is, run "sudo dpkg-reconfigure -phigh xserver-xorg" (without the quotes) and it should give you the option to change the default keyboard. (along with everything else)

It's also possible to change the type of Keyboard in the Settings Manager>Keyboard>Layouts, untick "Use X Configuration" and click +Add and select the option you want.
(well it works in Xubuntu so should also be in Ubuntu somewhere)

---

