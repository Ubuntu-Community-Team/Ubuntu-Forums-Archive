---
title: "/etc/hosts with ubuntu?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-11
My domain has an arecord set that maps my domain to the static ip address of my router behind which I have several computers, including my new ubuntu desktop installation, which has been configured to have an internal static ip as well.

So - the domain is webdroid.net the arecord points to my static ip 216.66.109.110.  My internal ip on this ubuntu box is set statically to 10.254.0.110.

If I try to access webdroid.net from this box, I get a routing error.  If this was a windows machine, I would edit the /etc/hosts file and add an entry that mapped webdroid.net to 10.254.0.110.  

How do I do the equivalent in ubuntu/linux?

Thanks!

---

### Post by Wicca on 2007-03-11
Exactly the same way: add an entry in the file /etc/hosts.

---

### Post by bernied on 2007-03-11
> **atraeyu said:**
> If this was a windows machine, I would edit the /etc/hosts file and add an entry that mapped webdroid.net to 10.254.0.110.
I don't understand this, windows doesn't have an /etc/hosts file, does it? Isn't it buried somewhere in Windows\system32\drivers or some other nonsense?

Anyway you certainly can edit the /etc/hosts file in linux.
```
sudo nano /etc/hosts
```
I suspect that this is not what you are asking for though ... ?

---

### Post by bernied on 2007-03-11
You can also access this file through the GUI control panel - under the Domain Name System tab in the Network Settings section.

---

### Post by atraeyu on 2007-03-11
Awesome, thanks!

---

### Post by atraeyu on 2007-03-11
Yup, windows has an /etc/hosts file buried in the system deep down.  I didn't realize linux had the same (only not buried way down).  That was exactly what I needed.  Thanks all.

---

### Post by Josh1187 on 2007-04-26
Ok. New to Ubuntu.

I dont really know if there is a difference but my laptop is running Xubuntu. I did something and now when the computer starts up. I get the following error message.

Could not lookup internet address for xubuntu-laptop. This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding xubuntu-laptop to the file /etc/hosts on your system.

I click Continue anyways cause the try again button doesn't work.  

I cannot access anything in the Xfce menu under the systems category. What do I do?

---

