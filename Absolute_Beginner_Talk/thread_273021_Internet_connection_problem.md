---
title: "Internet connection problem"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by professor on 2006-10-07
Hello there.
 i need help with a little problem.i am new to linux dont know much about it. i installe ubuntu dapper and found that my modem is a winmodem. it is a conexant chipset so i downloaded the linuxant driver. now the OS detects my modem on /dev/modem but when i dial to my isp it dials disconnects dials disconnects and so on. i need any kind of help to solve this problem.

---

### Post by Linux Lover on 2006-10-07
professor

what type of dialer you are using to dial your isp, kppp or wvdial?

---

### Post by professor on 2006-10-07
i have a standard ubuntu installation, not kubuntu so i guess it must be wvdial.

---

### Post by Linux Lover on 2006-10-07
OK..... I think you yet have not started any dialler to dial out your ISP. Anyway, The first thing you have to note that the, "Extra Initialization Parameter"....... from your windows dialler. Please note it from your windows.

Now check whether you really have any previous dialler, if yes, create a backup of it.

$ sudo mv /etc/wvdial.conf /etc/wvdial.conf.old
$ sudo wvdialconf /etc/wvdial.conf

This (the last) command will do most of the thing for you. You can find some series of strings with "OK" at the end. A file will be created /etc/wvdial.conf. Now manually edit the file using your favourite text editor and change the parameters (user name, phone no, password). Put the init2 string value same as you have got the string value from your windows 'Extra initialization parameter'. Also do not forget to remove any leading # if it stays before your username, password or phone no. field. Save the file and dial,

$ sudo ./wvdial

---

### Post by professor on 2006-10-08
Thanks it really did the trick. I cant believe that i am so stupid but then again i have not used linux much. Thanks again.:-)

---

