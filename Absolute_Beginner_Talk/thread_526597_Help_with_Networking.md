---
title: "Help with Networking"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by CadmannUK on 2007-08-15
Hi All,

First off I do not know too much about linux.

I have a Dell PowerEdge that I have installed 7.04 server and the desktop gui onto. I want to use this as both a file server (Samba?) and to host a club's website (when its finished)

I can not see the other windows PC's on the network and can get to their files, but I can't get onto the Ubuntu box from the windows XP boxes. I can see the ubuntu server in the networking page, but even when it asks me for my login and password it still doesn't connect?

Is there any howto's on basic networking and files and printer sharing faq's?

Thanks

CAD

---

### Post by jamvegan on 2007-08-16
Here's an Ubuntu doc about [Windows Networking]("https://help.ubuntu.com/7.04/server/C/windows-networking.html") (including installing and configuring SAMBA).

---

### Post by ugm6hr on 2007-08-16
> **CadmannUK said:**
> Is there any howto's on basic networking and files and printer sharing faq's?


For the password issue when accessing the Ubuntu shares - you need to add a line to your samba config file:
security=share

For details on how to do this (just 1 step) - look at the signature link "Easy Windows...." below.  You don't need to do any of the rest of it.  This will remove the password.  If you want to keep the password - you set it with smbpassword (I think - I haven't done this).

For printer sharing - this might be useful: [http://ubuntuforums.org/showthread.php?t=519779](http://ubuntuforums.org/showthread.php?t=519779)

---

### Post by CadmannUK on 2007-08-20
Hi,

This might be real stupid, but how do I login as Root, as I can't use the GUI login screen as it tells me I can't use this screen to login, and If I bring up a terminal window, I can't use login either?

Thanks

CAD

---

### Post by hyper_ch on 2007-08-20
By default you can't login as root... root is disabled - you'll first have to enable it but there's only very little reason to do so....

Normally you just acquire temporary root rights by issuing "sudo" in front of a command... it will then ask you for your user password.

---

