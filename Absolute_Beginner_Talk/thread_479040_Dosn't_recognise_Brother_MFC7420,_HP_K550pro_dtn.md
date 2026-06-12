---
title: "Dosn't recognise Brother MFC7420, HP K550pro dtn"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by red2chron714 on 2007-06-19
I have installed feisty on my dell laptop and am attemting to access my office windows network. I can see the other computers all running XP Pro sp2. My problem is trying to print to the shared printers on the network. The printers are connected to my desktop machine and all the windows computers on the network happily print to these shared printers. How do I get my ubuntu notebook to recognise these printers and print documents.

---

### Post by rajaiskandarshah on 2007-12-16
ok the simple steps. this is me using ubuntu 7.10 on acer aspire 5570 on wifi connecting to printer mfc7420 shared on windows xp sp2.

[LIST=1]
[*]install the brother mfc7420 lpr driver : [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
[*]install the brother mfc7420 cups wrapper driver : [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
[*]on ubuntu desktop, click on menu system > administration > printing
[*]in the printer configuration window, select server settings and check show printers shared on the network
[*]in the printer configuration window, click on the new printer button
[*]in the new printer window, select windows printer on samba and click the browse button
[*]in the smb browser window, browse to select your desired printer then click the OK button
[*]in the new printer window, click the forward button
[*]in the following new printer window, select brother printer from database, then click the forward button
[*]in the following new printer window, select mfc7420 for cups in the models list, then click the forward button
[*]in the following new printer window, enter a name, description and location for the printer, then click the apply button
[*]DONE
[/LIST]

---

