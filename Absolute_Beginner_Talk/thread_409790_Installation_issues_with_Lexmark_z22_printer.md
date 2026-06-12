---
title: "Installation issues with Lexmark z22 printer"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Mikasuliel on 2007-04-15
Ok, I have a friend who was told to switch to Ubuntu. All is fine and good except her printer won't work. I know that Lexmarks don't play nice. They don't have the option of buying another one. I'm sort of a beginner myself but know more linux than she does. 

Right now the system sees the printer says the printer is there and that it is printing but it isnt. I've had her restart the cups server. Is there some file she needs to edit that I dont know about?  It's a Lexmark z22 printer, she's running Edgy on a PC. 

I also had her install Alien but I havent a clue how to use it to install an RPM.  Any advice would be greatly appreciated.

Thank You.

---

### Post by Maestro23 on 2007-04-15
Yeah, Lexmark and linux = bad juju:D   Found these 2 docs that might help.  It's a little dated, but might guide you in the right direction.  You can also keyword search for some threads on the forums dealing with lexmark.  

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?highlight=%28lexmark%29](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?highlight=%28lexmark%29)

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters?highlight=%28lexmark%29](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters?highlight=%28lexmark%29)

Good luck.

---

### Post by Mikasuliel on 2007-04-15
Thanks! Tried the first one. No go. The second one looks promising though. Will let you know how it works out.

Thanks.

---

### Post by Maestro23 on 2007-04-15
Some links on Installing software: (.deb, .rpm, tar, etc...)

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by Sef on 2007-04-15
Read [Linuxprinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z22").  It says it will work partially with the Z32 driver.

---

### Post by nudnik on 2007-04-15
> **Sef said:**
> Read [Linuxprinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z22").  It says it will work partially with the Z32 driver.

I have the same printer and agree with their assessment. The print quality could be better, but the main problem is that it wont print more than one page, no matter the size of the document. The first page is printed and then it halts, lights blinking alternately on the printer as if it were out of paper. 

I don't believe there is a way to get this model to function properly with Ubuntu at present. Someday, someone may write a compatible driver, but I'm not holding my breath. I use an HP printer for Linux, the Lexmark is used solely with Windows.

---

