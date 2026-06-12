---
title: "Wireless broadcom card driver error"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by jerden on 2008-04-08
I have tried to install the wireless card on my laptop but it doesn't work! I followed the online instructions but it says the driver is wrong! and i dont know why.

jerden@ubuntu:~$ sudo ndiswrapper -i /tmp/DRIVER_US/bcmwl5.inf
driver bcmwl5 is already installed

jerden@ubuntu:~$ ndiswrapper -l
bcmwl5 : invalid driver!

is there any way to uninstall the driver to try and reinstall it?
I need help fed up with having to sit near the router!!

Thanks

---

### Post by Het Irv on 2008-04-08
try using ```
sudo ndiswrapper -r bcmwl5
``` that should remove the driver, allowing you to try again.  I have had to use NDISWrapper in the past and I hate it.  I am glad all my wireless cards work OOtB or with the restricted drivers.

---

