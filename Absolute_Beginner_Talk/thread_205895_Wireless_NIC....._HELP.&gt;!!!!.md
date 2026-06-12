---
title: "Wireless NIC..... HELP.&gt;!!!!"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-29
i have a laptop that i have just installed ubuntu on, and my main problem is the wireless network card, everytime i enable it in networking settings, when i exit it, it is disabled...

how do i check that the drivers have worked....

also, the WNIC is in-built into my laptop, and when i press the button on the side of laptop to enable the WNIC, the WNIC light does not come on....

please help

---

### Post by shoot2kill on 2006-06-29
**Bump**

---

### Post by Raistlin355 on 2006-06-29
First do this in terminal:

lspci | grep Broadcom\ Corporation

and post your the output here, this will tell us what card you have.
then if you have ndiswrapper installed type this in terminal:

sudo ndiswapper -l

that will tell you if the driver is installed and if the hardware is present

---

### Post by shoot2kill on 2006-06-29
[QUOTE=Raistlin355]First do this in terminal:

lspci | grep Broadcom\ Corporation

and post your the output here, this will tell us what card you have.
then if you have ndiswrapper installed type this in terminal:

sudo ndiswapper -l

that will tell you if the driver is installed and if the hardware is present[/QUOTE]


ok.. here is first command

```
gav@gav-laptop:~$ lspci | grep Broadcom\ Corporation
0000:02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
gav@gav-laptop:~$

```

and second
```
gav@gav-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
sp30379.exe     invalid driver!
gav@gav-laptop:~$


```

---

### Post by Raistlin355 on 2006-06-29
Ok I personally don't have much experience with that particular card as I have the Broadcom Airforce 4813 but this thread might help
[http://ubuntuforums.org/showthread.php?t=185174&highlight=Broadcom+Corporation+BCM4303](http://ubuntuforums.org/showthread.php?t=185174&highlight=Broadcom+Corporation+BCM4303)
You may want to uninstall ndiswrapper before doing this.  I have been told by a few friends of mine that it worked for them.
Sorry I couldn't be any further assistance.:)

---

### Post by x64Jimbo on 2006-06-29
It's unfortunate that broadcom is uncooperative with the linux community but the best solution for now is still ndiswrapper. i had trouble with my built in card and then just got sick of it and installed a card with the atheros chipset

---

