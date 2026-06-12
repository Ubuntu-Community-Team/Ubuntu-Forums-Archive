---
title: "Wvdial"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by terb on 2007-01-13
i have been stumbling around for about 2 weeks now trying to get on the internet. yesterday i read on some web page that Wvdial is the way to go. i looked it up and it was installed on my computer. but-- when i type wvdial i get reply that it is not configured. i have been all thru evey file i can find but i cannot find where to configure it. i have network card filled out but that doe not seem to do it. sure appreciate any help you all could give me

---

### Post by oyvindaa on 2007-01-13
Try [this](http://ubuntuforums.org/search.php?searchid=12722904) :)

---

### Post by ieee488 on 2007-01-13
Are you trying to use a dial-up modem?

As I understand it, wvdial is looking for file  /etc/wvdial.conf
Do you have that file?
If so, there are probably some lines that need to be un-commented. 
You can open it with gedit or any text editor.

---

### Post by terb on 2007-01-14
i have a external serial modem. when i dial -wvdial- it sees to find the modem but the wvdial file is not configured-- ie there is no phone # no address or password. i would like to know where to go to configure the file

---

### Post by zerhacke on 2007-01-14
> **terb said:**
> i would like to know where to go to configure the file

As stated previously, you need to edit /etc/wvdial.conf as root, so in a terminal type "sudo gedit /etc/wvdial.conf" and press enter.  Enter your password and press enter.  After a short time the text editor named gedit will open with /etc/wvdial.conf loaded into it.  Make changes as needed in that file.

If you can't figure it out, type "man wvdial" into a terminal and press enter.  It would be a good idea to run this command in a separate terminal than the one running Gedit so you may read the man file and edit at the same time.  When you're done with the man page, press the "Q" key to exit the manual program and return to a terminal.

---

### Post by terb on 2007-01-15
well-- i am getting an error message saying" temporary failure in name resolution system host name location." but i think that the modem that ubuntu "sees" is the diabbled winmodem and not my external one' i guess i will have to physically remove the winmodem to see.
i do want to thank you oyvinda, leee485 and Zeracke for your time and knowledge!!

---

