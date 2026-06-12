---
title: "The system is running in low-graphic mode"
date: 2012-06-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by siavashm31 on 2012-06-27
I wanted to install ubuntu 12.04 on an Asus Eee PC 1201K. After I installed the ubuntu 12.04 for the first time start up, it gave me the error message "The system is running in low-graphic mode"

I searched around and found the same problem with other people, but I tried their solutions and nothing worked so far.

Can any one help me to fix this problem??

---

### Post by papibe on 2012-06-27
Hi siavashm31.

Could you post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by siavashm31 on 2012-06-27
Hi,
The computer which has this problem wont start GUI even in low graphic mode, so I just pressed Ctr+Alt+F1 and then I logged in to Terminal. 
When I looked for **xorg.conf** I couldn't find it, but there were **xorg.conf.failsafe** instead and here is the content [http://paste.ubuntu.com/1062759/](http://paste.ubuntu.com/1062759/)

But about the log file it's too long and I can't write the content :( do you know how can I copy the file into a USB memory via terminal? so I can open it in another computer to copy and paste the content

Thanks for your help

---

### Post by siavashm31 on 2012-06-27
Here is some failures in the Log file, I tried to write unusual lines or lines with errors, I hope this can help to find out the issue.
[http://paste.ubuntu.com/1062799/](http://paste.ubuntu.com/1062799/)

the main problem is that it can not find any screen or usable configuration for the screen.

my graphic device is: SiS Mirage Graphics 741CX

---

### Post by siavashm31 on 2012-06-27
OMG,

I fixed it, I just save as the file xorg.conf.failsafe with name of xorg.conf and then I reboot and it worked :D

thanks for your hel cuz I didn't know about this file ;)

---

### Post by mwclark4453 on 2012-06-27
Very cool.  I'm going to have to try this.

---

