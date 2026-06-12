---
title: "ie in wine"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by TheOtherLinuxFreak on 2007-03-24
how do i install ie 6 in wine? thanks for your help. im installing a program that needs ie 6 and thats y i need it.

---

### Post by aktiwers on 2007-03-24
Check this out:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by eljalill on 2007-03-24
You need to download the installation files for IE (.exe or so).
Save them on lets say the Desktop.
Open a terminal, and go to the Desktop (cd Desktop)
run
wine setupIE.exe (or whatever else it might be called) .

And the run 
wine IE.exe (or whatever else the .exe to invoke it is called).

---

### Post by aysiu on 2007-03-24
> **aktiwers said:**
> Check this out:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
Ubuntu-specific instructions on IEs4Linux here:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by TheOtherLinuxFreak on 2007-03-24
i have ies for linux. i tryed to instal ie6 by dowloading it and runing it with wine but it said that i wasnt connected 2 the internet but i was. any suggestions?

---

### Post by aysiu on 2007-03-24
> **TheOtherLinuxFreak said:**
> i have ies for linux. i tryed to instal ie6 by dowloading it and runing it with wine but it said that i wasnt connected 2 the internet but i was. any suggestions?
Instead of summarizing the output, can you copy and paste here the exact terminal output of the command to install IEs4Linux?

---

### Post by eljalill on 2007-03-24
Did you already look at this?
[http://appdb.winehq.org/appview.php?iVersionId=469](http://appdb.winehq.org/appview.php?iVersionId=469)
It says, it needs some changes in the reg....

---

### Post by TheOtherLinuxFreak on 2007-03-24
> **aysiu said:**
> Instead of summarizing the output, can you copy and paste here the exact terminal output of the command to install IEs4Linux? do u mean the output of the ies for Linux installation? the installation worked perfectly and i even tried it out. but the install dialog on the program that i was instaling said that i didn't have ie6.

---

### Post by aysiu on 2007-03-24
> **TheOtherLinuxFreak said:**
> do u mean the output of the ies for Linux installation? the installation worked perfectly and i even tried it out. but the install dialog on the program that i was instaling said that i didn't have ie6.
You're trying to install a Windows program that requires you to have Internet Explorer? I don't know if that's going to work.

What's the program?

---

### Post by TheOtherLinuxFreak on 2007-03-24
printmaster silver 10. by broderbund

---

