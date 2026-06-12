---
title: "installing driver problem"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2007-12-18
hey, i tryed to install a driver for my CWP-854 wireless card and all i found was drivers for windows, but when i try to install it i always get this error:
Error Number: 0x80040707
Description: DDL function call crashes: installrt2500qa.EnumerateDevice

Setup will now terminate.


Help me plz!!

---

### Post by diatribe on 2007-12-18
you will have to use windows drivers probably, how are ou trying to install them?

---

### Post by shayvasa on 2007-12-18
i am using a windows driver...im trying to install it with wine. i downloaded the driver from several diferent places and always i get the same problem.

---

### Post by Abu_Dayya on 2007-12-18
Did you try using NDISWrapper?

Check out this link : [https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)

---

### Post by diatribe on 2007-12-18
yes follow the above post, installing from wine will not work

---

### Post by shayvasa on 2007-12-18
theres still one problem...all the drivers i found are .exe and i cant install it

---

### Post by shayvasa on 2007-12-18
do u have a link from where i can download the driver?

---

### Post by shayvasa on 2007-12-19
plz naswer me

---

### Post by shayvasa on 2007-12-19
any1??? this is really important

---

### Post by shayvasa on 2007-12-20
come on answer me!!!!!

---

### Post by Abu_Dayya on 2007-12-22
Are you downloading the driver from the internet? Don't you have The CD that came with the wireless adapter? the .inf files should be in the CDs.

---

### Post by shayvasa on 2007-12-22
i dont have the CD...any other option?

---

### Post by Abu_Dayya on 2007-12-24
Try the following on a Windows PC:

- Go to the website of your adapter manufacturer
- search and download the driver (it should be .zip file with a folder in it)
- Find the .inf file and copy it to your Ubuntu PC
- Add it using NDISWrapper

---

### Post by shayvasa on 2007-12-25
but theres a problem, they only give me an option to download it as an .exe file.
Heres the web site:[www.cnetusa.com/newwebsite/techsupport/driverdownload.htm](www.cnetusa.com/newwebsite/techsupport/driverdownload.htm)
mine is CWP-854

---

### Post by Abu_Dayya on 2007-12-27
> **shayvasa said:**
> but theres a problem, they only give me an option to download it as an .exe file.
Heres the web site:[www.cnetusa.com/newwebsite/techsupport/driverdownload.htm](www.cnetusa.com/newwebsite/techsupport/driverdownload.htm)
mine is CWP-854

Download and run the .exe file in Windows. See if that .exe file will generate a folder or a .inf file.

---

