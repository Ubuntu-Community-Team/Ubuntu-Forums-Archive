---
title: "Change Keyboard Map on 7.04 Server"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Catterly on 2007-06-13
I am running 7.04 server under VMWare workstation.  Unfortunately I have switched vmware host pcs and now have a mismatch between my keyboard layout and the server configuration. 

Please will somebody advise how to reconfigure keyboard in text mode.  I am just looking for basic functionality not fully mapped multimedia keys.

Thanks
Simon

---

### Post by avik on 2007-06-14
```
xmodmap /usr/share/xmodmap/xmodmap.*code*
```

where *code* is the code of the keyboard layout you want.  Look at the contents of /usr/share/xmodmap for all the available keyboard layouts.

---

### Post by Catterly on 2007-06-14
Thank you for the suggestion.  

Unfortunately xmodmap is not present after a base server install and when I try to install it cannot find it within the packages on the installation CD.  

As connecting this this device to the network is slightly problematic, is there any other way of correcting the mapping or is this the only direction to go?

Simon

---

### Post by avik on 2007-06-15
I don't exactly know of any other way.  The only thing that comes to mind is to download xmodmap from [http://packages.ubuntu.com]("http://packages.ubuntu.com") using some other device and transfer it via a USB drive or something.  Unfortunately, dependancies might pose a problem.

Other than that, I have no idea.  Anyone else?

---

### Post by gfowler on 2008-01-03
> **Catterly said:**
> I am running 7.04 server under VMWare workstation.  Unfortunately I have switched vmware host pcs and now have a mismatch between my keyboard layout and the server configuration. 

Please will somebody advise how to reconfigure keyboard in text mode.  I am just looking for basic functionality not fully mapped multimedia keys.

Thanks
Simon

On the offending machine do:

 dpkg-reconfigure console-setup

---

