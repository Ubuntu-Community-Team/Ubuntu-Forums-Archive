---
title: "log in automatically - Ubuntu 6.06"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by LeftyMills on 2006-10-05
My computer
CPU 500 MHz;  256 Mbytes memory;  bios 1999;
Ubuntu 6.06 dual boot with Win98 SE

I went to system -> Administration -> login window -> security tab -> enable automatic login

Now, every time I boot I get 2 error messages-

1) "Power manager - this program cannot start until you start the dbus system service.  It is strongly recommended that you reboot your computer after starting messagebus."
(I note that 2 weeks ago someone else had a problem with the dbus system service, and was not answered.)

2) "Internal error! Failed to initiate HAL!"

Showng me how to enable automatic login without these error messages would be greatly appreciated.

L.

---

### Post by papafox on 2006-10-05
click System > Administration > Login Screen Setup, and select the Login a User automatically on first bootup checkbox. In the checkbox below it, select the user who should be logged in automatically.
In the Security tab of the window, you can allow root to login automatically, this is not recommended due to security implications.

---

### Post by LeftyMills on 2006-10-06
"click System > Administration > Login Screen Setup, and select the Login a User automatically on first bootup checkbox. In the checkbox below it, select the user who should be logged in automatically.
In the Security tab of the window, you can allow root to login automatically, this is not recommended due to security implications."



Thank you for your reply.  However, after system > administration there is no "login screen setup".  What there is is "login window".  Is this the same thing?
At login window, I have 5 choices - local, remote, accessibility, security and users.  I cannot see "Login a User automatically on first bootup" nor user who should be logged in automatically"

Could you please clarify.

L.

---

### Post by Jagot on 2006-10-06
> **LeftyMills said:**
> "click System > Administration > Login Screen Setup, and select the Login a User automatically on first bootup checkbox. In the checkbox below it, select the user who should be logged in automatically.
In the Security tab of the window, you can allow root to login automatically, this is not recommended due to security implications."



Thank you for your reply.  However, after system > administration there is no "login screen setup".  What there is is "login window".  Is this the same thing?
At login window, I have 5 choices - local, remote, accessibility, security and users.  I cannot see "Login a User automatically on first bootup" nor user who should be logged in automatically"

Could you please clarify.

L.

Login Window is the same thing.  Please see my attached screenshot.

---

### Post by LeftyMills on 2006-10-06
Thank you.

Lefty

---

