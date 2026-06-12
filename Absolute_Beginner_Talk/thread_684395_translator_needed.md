---
title: "translator needed"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by bibas on 2008-02-01
hi 
here is an instruction some guys in nepalinux gave me to make my modem work in the OS.

I tried same with ubuntu but cudnt make it work coz i didnt have root password and other input returned errors..can anybody help me translate these instructions into ubuntu lanuage?



> 1.Open the gnome terminal.
> 2.Do: su and provide the Root password.
> 3.Enter the command:chmod +x /etc/ppp/peers/
> 4.Click Applications-->Internet-->Gnome PPP
> 5.Click Setup
> 6.Under Modem Tab, Click Detect by choosing /dev/ttyS0 or /dev/ttyS1
> in Device menu whatever will be appropriate for your CDMA.
> 7.After few seconds your CDMA will be detected.
> 8.Now click on Init Strings button
> 9.Double click on Init2 and provide the extra initialisation commands
> (note:you can find the extra initialisation commands in the CDMA phone
> manual)
> 10.After that click the Close Bold text button.
> 11.Finally in the Gnome PPP application type username , password and phone no
> 12.Click 'Remember Password'
> 13.Click 'Connect' to use the internet.

---

### Post by jan quark on 2008-02-01
try this first

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

and post the result of the terminal command

```
lspci
```

pls

---

### Post by hyper_ch on 2008-02-01
well, ubuntu does not use the root account (su) by default. Normally you use "sudo" as prefix to any command that you want to run as "su".

---

