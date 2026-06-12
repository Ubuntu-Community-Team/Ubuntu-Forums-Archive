---
title: "RDP and Printing"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-06-28
The one thing, whichs keeps me bound to windows is print from my RPD client. 

Can anyone tell me how to print using my RDP client?

Thanks

---

### Post by d_weil_e on 2007-07-17
Are you asking how to print from Remote Desktop?  Or how to print from your Windows machine via Remote Desktop?  Need a little more info.

If you want to print from your Windows machine using Ubuntu as a print server, you'll want to investigate using Samba and CUPS.  It's been a bit of a bear for me to get them configured as a print server that's compatible with Windows.  I finally figured out that there aren't any CUPS drivers for my printer. :-(

---

### Post by uclalinux on 2007-07-18
i want to connect to a windows server from a Ubuntu client. When using the Ubuntu client i would like to print to my local location.

---

### Post by MockY on 2007-07-22
The client must have the same drivers as you have on the Terminal Server. Since you are not using the same drivers on the Ubuntu-box as you would on a Windows box, the server can't communicate with your local printer (unless you are using a third party software). See [[COLOR="Red"]THIS[/COLOR]]("http://www.brianmadden.com/content/article/The-Ultimate-Guide-to-Terminal-Server-Printing---Design-and-Configuration") for more information about printing with Terminal Services.

---

