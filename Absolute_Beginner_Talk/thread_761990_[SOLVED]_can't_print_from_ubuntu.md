---
title: "[SOLVED] can't print from ubuntu"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by beckym@cincoed on 2008-04-21
I am unable to print anything on my printer (Brother  DCP 115-c) - when i ask it to print it selects the right printer and then seems to think it has printed without anything actually happening - not even an error message on the printer. I can only find printer drivers for this model that are for windows or mac's - any ideas out there?

---

### Post by linuxwizard on 2008-04-21
You can get your driver here > [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

---

### Post by beckym@cincoed on 2008-04-21
Thanku - i have the driver installed - now when i go to add printer it is asking me for a ppd file and the one i installed is a .deb file.  if i try to follow the instructions on the brother website i can't login as root using the terminal it denies me access but i only have one password so i don't understand why -  

perhaps i'm not tekkie enough for ubuntu :(

---

### Post by boomdiddly on 2008-04-21
> **beckym@cincoed said:**
> Thanku - i have the driver installed - now when i go to add printer it is asking me for a ppd file and the one i installed is a .deb file.  if i try to follow the instructions on the brother website i can't login as root using the terminal it denies me access but i only have one password so i don't understand why -  

perhaps i'm not tekkie enough for ubuntu :(

Can't help with install the printer but use SUDO in terminal to get the access you need it will ask you for your password so it's

```
sudo whatever_command_it_asks_for
```

hope this helps

---

### Post by stchman on 2008-04-21
> **beckym@cincoed said:**
> I am unable to print anything on my printer (Brother  DCP 115-c) - when i ask it to print it selects the right printer and then seems to think it has printed without anything actually happening - not even an error message on the printer. I can only find printer drivers for this model that are for windows or mac's - any ideas out there?

That printer is reported to work "mostly" according to openprinting.org.

[http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-115C](http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-115C)

There are instructions.

---

### Post by beckym@cincoed on 2008-04-21
thanku - the sudo thing works :) but i still can't get them installed :(

---

### Post by beckym@cincoed on 2008-04-21
thanku stchman - i'll check that out

---

### Post by beckym@cincoed on 2008-04-21
thanku guys - i followed the last link to [http://ubuntuforums.org/showthread.php?t=302960](http://ubuntuforums.org/showthread.php?t=302960) and got it sorted :)

---

### Post by avtolle on 2008-04-21
If you haven't had success yet, look at the link. I used it to install my Brother MFC240C, and the printer install instructions given seem to work for a number of printers. Good luck.

[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

---

