---
title: "Problems with WiFi on Laptop"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-05-23
I've had my laptop for about a month now, and the wireless used to work just fine.  Recently, though, I took it to a friends house (where it worked), but when I came home it stopped working.  I am running Kubuntu 7.04.

The Network Manager gets to "Configuring Device" and stops, every time.  When I do an "lspci" I see the following info about my network card:

```
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02).
```

Thanks for your help.

EDIT:  I tried downloading WiFi Radar and WLan Manager, and neither one worked for me.  Since it worked before and suddenly stopped, I'm pretty stumped.  I will try to remove/re-install NetworkManager when I get home this evening.

---

### Post by rhysmc on 2007-05-24
Hi,
Is ipw3945 still in use in the restricted drivers manager? (or Kubuntu equivalent)

[img]http://glamdring.se/files/mcd.2007.05.24.17.59.15.png[/img]

---

### Post by Sparkster185 on 2007-05-24
Thanks for your reply.  Unfortunately, I'm at work so my laptop isn't with me right now.  I will check when I get home and update the thread.

---

### Post by Sparkster185 on 2007-05-24
> Is ipw3945 still in use in the restricted drivers manager? (or Kubuntu equivalent)

I can't seem to find any packages with "ipw3945", "iwp" or "3945" in the repositories.  Do you know which one it is exactly, so I could add it to my sources.list? 

I have my package manager set up to search restricted packages.

---

### Post by rhysmc on 2007-05-24
It is not in the repos.
In feisty it should come with the install. I am using the driver and it worked out-of-the-box.
Check if 'ipw3945d-2.6.20-15-generic' in in /sbin.
if it is, try...
```
sudo modprobe ipw3945 
```

Also, the drivers sourceforge site:
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

---

### Post by Sparkster185 on 2007-05-24
>  ls -l /sbin | grep ipw

Tells me that I do have the file in /sbin.

> sudo modprobe ipw3945

I executed this and it didn't give me any output at all.

Perhaps something happend and this module got un-loaded?  How should I re-load the module?

Thanks,

---

### Post by Sparkster185 on 2007-05-24
Weird, all of the sudden it connected.  It actually configured the device immediately and connected in about 10 seconds.

I really can't explain the sudden halt/resume, but oh well.

If anyone wants me to give more output, just for information, feel free to ask.

---

