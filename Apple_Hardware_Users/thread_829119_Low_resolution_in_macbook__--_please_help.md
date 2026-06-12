---
title: "Low resolution in macbook  -- please help"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by brauer.erik on 2008-06-14
I am using macbook with leopard.  I have been dual booting with ubuntu but all of a sudden it will only come up with low resolution.  I even went to change it under the resolution menu, but there was no option.  The OSx side is fine.  My card is an intel video graphics card of GMA x3100.  I even checked the usplash file and the resolution is saying correctly like it should as 1280 x 800 but ubuntu will only give me 800 x 400 if I remember correctly.  Is there anyway to correct this.  It was working fine and only two days ago this happened.  I am using hardy and I hope that isn't the problem.  

Thanks
Erik

---

### Post by avtolle on 2008-06-14
Try at the terminal```
sudo displayconfig-gtk
``` to configure both the card and the screen. HTH.

---

### Post by brauer.erik on 2008-06-15
Thanks for the information.  Unfortunately, it is a temporary fix.  After I changed it, and rebooted, it went back to the old, but it did not fix my graphics driver for ubuntu on the intel driver.  I had the advanced pleasing features on before this happened but it won't come back.  

I am not sure if this is a bug in hardy, or not

Thanks
Erik

---

