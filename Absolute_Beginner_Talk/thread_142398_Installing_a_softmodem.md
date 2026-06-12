---
title: "Installing a softmodem"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by earl gray on 2006-03-10
Hello community,

I'm sorry if this question pops up often, I tried to get an answer elsewhere but couldn't.

I added Ubuntu as a second OS on a WinXP machine with a Conexant SoftK56 PCI modem which Ubuntu doesn't autodetect.

A Google search led me to linmodem.org and scanModem, which identified SmartLink chipset. I downloaded the suggested package, but, being a beginner, I have no idea how to use it. The readme file suggests I type 'make', but I don't have that command on my system.

Thank you for your help.

--
EDIT:

I connect to the Internet from WinXP, and transfer data between the two systems on a memory stick. I cannot connect from the Ubuntu to download repositories.

---

### Post by az on 2006-03-10
Does this work for you?  If you scroll down the page, you get links to the files you will need to download from another computer and transfer to your non-networked (because your modem does not work) box.

[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=BinaryDriverHowto%2FSmartLinkModem](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=BinaryDriverHowto%2FSmartLinkModem)

---

### Post by earl gray on 2006-03-16
I downloaded a Linuxant driver for my kernel, but it failed to detect the device altogether.

scanModem detected a SmartLink compatible chipset. I downloaded a suggested archive and installed the build-essential package from the Ubuntu CD, but when I tried to compile the driver, I got tons of syntax error messages, as if the drivers were buggy?

---

### Post by Mustard on 2006-03-16
[QUOTE=earl gray]I downloaded a Linuxant driver for my kernel, but it failed to detect the device altogether.

scanModem detected a SmartLink compatible chipset. I downloaded a suggested archive and installed the build-essential package from the Ubuntu CD, but when I tried to compile the driver, I got tons of syntax error messages, as if the drivers were buggy?[/QUOTE]

Can you save the errors you get into a text file, transfer it somehow to windows and then paste it in here?  Maybe use a floppy disk or external USB drive?

---

### Post by earl gray on 2006-03-17
Sorry, I was obviously trying to install the wrong thing - I downloaded the package with my kernel version attached to its name and now it's working fine. In fact, I'm sitting at Ubuntu right now, viewing this through Firefox.

Thank you very much for your help. I felt completely lost when I saw Ubuntu the first time, but I could tell by the community that it would be worth it in the end.

---

### Post by Mustard on 2006-03-17
[QUOTE=earl gray]Sorry, I was obviously trying to install the wrong thing - I downloaded the package with my kernel version attached to its name and now it's working fine. In fact, I'm sitting at Ubuntu right now, viewing this through Firefox.

Thank you very much for your help. I felt completely lost when I saw Ubuntu the first time, but I could tell by the community that it would be worth it in the end.[/QUOTE]

Job well done. :)  Congratulations.

---

