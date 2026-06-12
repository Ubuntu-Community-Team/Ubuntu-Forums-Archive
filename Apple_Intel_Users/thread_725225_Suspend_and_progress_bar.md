---
title: "Suspend and progress bar"
date: 2008-03-15
forum: Apple Intel Users
---

### Post by liberalist on 2008-03-15
Hi everyone,

I have just installed Ubuntu 7.10 on my white core 2 duo iMac (17"). I opted for the 32-bit version, should I install the 64-bit version? When I start up the machine, I don't get a progress bar like in 7.04. The screen just stays black and after a while the login screen appears.


**Update:** The following seems to be an issue related to the use of a restricted driver called fglrx. When this driver is not in use, suspend and hibernate do work. 
When the fglrx driver is enabled, suspend and hibernate do not work. 

How can I solve these two problems? Thank you very much in advance.

---

### Post by ronocdh on 2008-03-15
I've actually been troubleshooting suspend and hibernate lately. I don't think I've ever had it working smoothly in Gutsy (which I'm still using).

It's interesting to hear that it's related to fglrx. Are you sure it's not xgl-server, though? On 64-bit xgl-server gives me all sorts of weird bugs, but the kludgy nature of fglrx might indeed be the bigger problem.

Also, I've read that madwifi drivers prevent hibernation. But on an iMac, that probably doesn't mean anything to you!

---

### Post by cyberdork33 on 2008-03-16
older fglrx (as is in the Gutsy repo) + newer Linux Kernel (as is used in Gutsy) = No suspend

You need to use the newer ATI drivers (Use envy).

---

### Post by aongenae on 2008-03-16
Hi,

I have 7.10 on a macbook pro (first gen) and the latest Envy, everything is working except the suspend/hibernate...

I have read that it's an issue in the kernel and update to the one used in hardy would solve the isssue, you can give it a try and tell us or do like me wait another month for the release of hardy version... 

> **liberalist said:**
> 
The screen just stays black and after a while the login screen appears.


for the black splash-screen, you have to edit the file

/etc/usplash.conf

and replace the resolution there with your display's actual resolution (for the 15" this is 1440 by 900) After editing, enter 

```
sudo update-initramfs -u -k `uname -r`
```

---

