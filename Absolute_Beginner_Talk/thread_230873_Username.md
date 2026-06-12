---
title: "Username"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Gambylad on 2006-08-06
I have installed ubuntu using alternate cd, on reboot to finish setup it askes me for username & password I did not enter a username in setup but i did enter a password.I remember the password ok but i still cannot get beyond this point to finish setting up my ubuntu instalation.All help would be gratefully recieved.

---

### Post by darkenedday on 2006-08-06
what did you make for the host name? ubuntu by default should have set your username to "host name"-desktop

---

### Post by stormblue on 2006-08-06
Did you do an OEM install?

---

### Post by Jagot on 2006-08-06
I don't quite understand at what stage you are.  Is it installed and you're now trying to log in from the GDM?  If it's installed and you can boot from GRUB then boot into the recovery mode and at the prompt type:

```
cd /home
ls
```

You should see the username there.

You didn't happen to do an oem install did you?  If that is the case then the login would be 'oem' methinks.

---

### Post by Gambylad on 2006-08-06
Yes I installed oem. I have installed to remove cd and reboot I get as far as logon screen and no further.

---

### Post by Gambylad on 2006-08-06
THe omly info i entered was computer name for network and password

---

### Post by Jagot on 2006-08-06
If you installed it as an OEM then the password will be oem I think,  as I said in my previous post.

Read this:

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

---

### Post by Gambylad on 2006-08-06
I have lilo bootloader installed how do i boot to recovery mode

---

### Post by Jagot on 2006-08-06
You shouldn't need to - login with the password you set up and the username as oem.

---

### Post by Gambylad on 2006-08-06
many thanks
sorted
just a thick windows user

---

