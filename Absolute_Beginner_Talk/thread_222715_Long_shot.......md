---
title: "Long shot......"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-25
Anyone know how to configure the admin access to "CUPS"?

---

### Post by wpshooter on 2006-07-25
> **dragon1964m said:**
> Anyone know how to configure the admin access to "CUPS"?

No, but it sure would be nice to know.  I think I saw a post on here yesterday that gave a listing of a file that you basically had to replace on your installation in order to get it to work (looked too difficult to me and likely to break something if you did not know what you were doing), so I think I will wait for the developers to see if they will come up with a way to make this work without having to possibly screw up your system in order to get it to work.  I will just keep using my little local printer setup.

Good luck.

---

### Post by MaximB on 2006-07-25
> **dragon1964m said:**
> Anyone know how to configure the admin access to "CUPS"?
what excactly do you mean ???

---

### Post by OU812 on 2006-07-25
I'm not sure if this is what you're looking for, but try entering

[http://localhost:631](http://localhost:631)

in a browser.

john

---

### Post by 5-HT on 2006-07-25
[quote=dragon1964m]Anyone know how to configure the admin access to "CUPS"?[/quote]To enable:

```
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart 
``` 

To disable again:

```
sudo deluser cupsys shadow
sudo /etc/init.d/cupsys restart 
``` 
For security reasons it may be a good idea to either disable access again once you're done with the config, or block external access to to the interface.

HTH

---

### Post by dragon1964m on 2006-07-25
Thank you 5-HT! That helped!! :-D

---

