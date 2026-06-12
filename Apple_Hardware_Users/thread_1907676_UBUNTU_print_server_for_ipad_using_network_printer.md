---
title: "UBUNTU print server for ipad using network printer"
date: 2012-01-11
forum: Apple Hardware Users
---

### Post by rtrask on 2012-01-11
I have done some searching, but I have not been able to find an answer for this specific problem. I have a Dell 3100cn connected to my network. I would like to be able to provide a print server running on Ubuntu that would enable my daughter's ipad to print to it. I have seen the posts which describe how to do this with a printer that is attached to the linux box via CUPS / avahi, but not for a remote server. Does anyone have any ideas on how this might be achieved? I have found similar requests around a Samba print server, but I am not turning up any answers.

---

### Post by Wolfador on 2012-01-12
This looks like the correct procedure for archLinux 
[http://archlinuxarm.org/support/guides/applications/cups-apple-airprint](http://archlinuxarm.org/support/guides/applications/cups-apple-airprint)

probably just need to replace the pacman -Sy with apt-get install

---

