---
title: "Printing"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Stuart1941 on 2007-07-11
I need advice please, I have two desktop computers 1 has Ubuntu 7.04 installed and the Other one has Windows XP. Now on the Linux machine i see and read from various disk drives on the wiindows machine but when i try printing from the Linux M/C nothing happens. The printer is attached to a USB port on the Windows M/C. I have shared the printer in the Windows Control panel but I still can not get anything to print when I send a test page from the linux m/c although it says it has sent a page to the printer. I have installed the printer driver on the Linux m/c. The printer in Question is a HP Deskjet 5650 model. It works OK when connected directly to The Linux m/c. WHAT AM I MiISSING in the setup procedure. HELP
Stuart J Warner

---

### Post by Seisen on 2007-07-11
Maybe this will help.

[http://doc.gwos.org/index.php/Print_Windows_XP_machine]("http://doc.gwos.org/index.php/Print_Windows_XP_machine")

---

### Post by Stuart1941 on 2007-07-11
thanks for the reply i have followed all details but still cannot print anything the only thing i have noticed is a message which cpomes up sometimes but i donot hpow i get the message so cannot repeat it exactly but it goes somethng like this CANNOT CONNECT USE CFIS

---

### Post by krig on 2007-07-12
First: you need share printer on your windows comp you must remember: computer name, shared printer name, all in english without spaces.
second: in ubuntu click system/admin..s/print than click on new printer in window add printer choose network printer than windows printer SMB, as a host you need to enter the name of the windows computer without anything only the name in the printer name enter the shared name of the printer (as you remembered in first step)
third: click next and chose the correct driver (***.ppd file consult with producer of printer or take it from community site)

thats all

if doesnot work, pls see you windows comp first, than read about .pp file and its stability

---

