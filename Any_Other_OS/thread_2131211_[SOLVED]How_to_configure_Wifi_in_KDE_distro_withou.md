---
title: "[SOLVED]How to configure Wifi in KDE distro without Internet connection?"
date: 2013-04-01
forum: Any Other OS
---

### Post by pooja on 2013-04-01
Hi everybody!
I've just installed Mageia 2 on my hp dv6000 series laptop in a dual booting system with Windows 7. This is my first experience with a KDE distro, so far I've used Ubuntu ( & Windows, of course).

Mageia though beautiful to look at, **can't connect to my home wifi **so I cannot update softwares or install the missing packages it needs to connect to the wifi!
I'm in the uneasy situation of experimenting with possible solutions in Mageia, then restart the pc, this time boot into Windows7, post updates on help forums, find out new tips & tricks to solve the wifi connection problem, then again switch back to Mageia in a totally time-consuming, never-ending cycle of actions!
So far, I've tried giving this command from Konsole: ```
ifconfig -a
```
Please see attached files for more insight.

---

### Post by carl4926 on 2013-04-01
That wireless should work OOTB

---

### Post by ppv on 2013-04-01
The error message says to install some files from intellinuxwireless.org. Seems to be a case of some files or component missing. Can you check if the files you require are present on that particular website.

---

### Post by iamkuriouspurpleoranj on 2013-04-01
You might be better off asking this question on the Mageia forum. They're very helpful and are likely more clued up on Mageia than the Ubuntu community. I would honestly just try looking for a firmware package in the MCC and maybe activating repositories that you don't currently have activated if you can't find a suitable package on your first look.

---

### Post by pooja on 2013-04-01
[QUOTE='ppv']The error message says to install some files from intellinuxwireless.org. Seems to be a case of some files or component missing. Can you check if the files you require are present on that particular website.  [/QUOTE]
I've looked for iwlwifi3945-2.ucode in *[www.intellinuxwireless.org](www.intellinuxwireless.org)*: not present.

EDIT:
From *[www.intellinuxwireless.org](www.intellinuxwireless.org)* I got to [http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/) and I found that particular file. I'll try copying it in the directory via usb key and will let you know the outcome.

---

### Post by carl4926 on 2013-04-01
That driver has been built in the kernel forever
It does not need installing

Lets see
```
lspci -nnk | grep -iA2 net
```

---

### Post by pooja on 2013-04-01
[QUOTE='iamkuriouspurpleoranj']You might be better off asking this question on the Mageia forum. They're very helpful and are likely more clued up on Mageia than the Ubuntu community. I would honestly just try looking for a firmware package in the MCC and maybe activating repositories that you don't currently have activated if you can't find a suitable package on your first look. [/QUOTE]
Just now I got a reply from them: they told me I must either connect Mageia through a wired connection and install that missing package or install it manually after downloading the package in another computer and transferring it to Mageia with a usb key.

---

### Post by pooja on 2013-04-02
Just a quick response to say that I managed to solve my problem by following the mageia forum instructions. Thanks to everybody for taking the time to look at my problem. ):P

---

