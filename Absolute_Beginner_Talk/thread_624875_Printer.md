---
title: "Printer"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-27
ok... so I also have a_** Dell A920 All-in-One printe**_r which fails to work.
Please see attached screen dump which shows that it is recognised ok but ...

Is there any way I can get this one to work in Ubuntu 7.10?

Thanks

Bern

---

### Post by linuxwizard on 2007-11-27
Which driver have you tried using ? According to this link that printer is the same as Lexmark x1270 and uses the z600 driver.
[http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920](http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920)

[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X1270](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X1270)

Try using this to install the z600 driver
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

Lexmark makes Dell printers.

---

### Post by stchman on 2007-11-27
> **bern1939 said:**
> ok... so I also have a_** Dell A920 All-in-One printe**_r which fails to work.
Please see attached screen dump which shows that it is recognised ok but ...

Is there any way I can get this one to work in Ubuntu 7.10?

Thanks

Bern

According to [http://openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920](http://openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920)

your printer works perfectly under Linux.

Make sure you are using the Lexmark z600 driver.

---

### Post by bern1939 on 2007-11-27
Thanks a lot but when I follow the install instruction at the following point:

tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.

I get bells ringing and a lot of gobbledgook !! I am only using the command prior to the #

??

Thanks

Bernard

---

