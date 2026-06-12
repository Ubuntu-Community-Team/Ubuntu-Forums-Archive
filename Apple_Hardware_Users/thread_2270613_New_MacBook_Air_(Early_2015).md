---
title: "New MacBook Air (Early 2015)"
date: 2015-03-24
forum: Apple Hardware Users
---

### Post by Keith_Ng on 2015-03-24
Has anyone had any luck installing Ubuntu on a new MacBook Air (early 2015)? I've tried 14.04, 14.10 and 15.04. Wifi didn't work for any of them, and 14.* had a weird display problem - icons were showing up sporadically (sometimes on mouseover) and text inside windows weren't showing up at all (though tooltip and notification texts WERE showing up).

I'm not the only one, right?

---

### Post by mohamed15 on 2015-03-24
well, I'm not expert. Try to connect to the internet through cable (ethernet, if possible or use usb wifi adaptor if you have it). Do ubuntu update and restart. Check if ubdating solve all proplems or not. Now disconnect the cable ethrenet and close the lid and re-open again the lid after a second or so. Then, log in and see if the wifi now works or not.

---

### Post by Keith_Ng on 2015-03-24
You're right! The updated drivers did work. However, the MacBook Air doesn't have an ethernet port, so I had a to USB tether via my phone. But once the update was done everything is most working well. Screen/backlit keyboard controls aren't working yet though.

---

### Post by mohamed15 on 2015-03-25
Great. Just a suggestion, try to see if you can assign shortcut keys in the system settings for the Screen/backlit.

---

### Post by theWhirlyNerd on 2015-07-27
Which version did you end up installing?

---

### Post by davidchute26 on 2015-08-05
If your using a newer MacBook I'd recommend the latest version of Ubuntu. Also a note when installing make sure the check box for install updates is checked. The driver might be pulled down during the installation and if it doesn't work out of the box check the Additional Drivers application for wireless drivers. Good luck

---

### Post by theWhirlyNerd on 2015-12-07
> **mohamed15 said:**
> Great. Just a suggestion, try to see if you can assign shortcut keys in the system settings for the Screen/backlit.

To get the brightness keys working, I used this for Fedora 23: [https://jamielinux.com/blog/cannot-adjust-screen-brightness-on-fedora/](https://jamielinux.com/blog/cannot-adjust-screen-brightness-on-fedora/)

Tailored for Ubuntu 15.10, after you update the /etc/default/grub file, point grub2-mkconfig to the Ubuntu grub.cfg file:

```
grub2-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by Bucky Ball on 2015-12-07
@Joshua_Clements: As your link concerns Fedora the info about update grub seems incorrect for Ubuntu. After changing the /etc/default/grub you close the file and run

> sudo update-grub

That's it. Do not follow the instructions on that link to update grub after the changes. :)

---

### Post by theWhirlyNerd on 2015-12-07
Good catch, Bucky Ball. I do believe you're correct. I remember troubleshooting this on Fedora and wondering why "update-grub" wasn't working... Thanks!

---

### Post by Bucky Ball on 2015-12-07
;)

---

