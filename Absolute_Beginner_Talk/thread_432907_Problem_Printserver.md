---
title: "Problem Printserver"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by bb-g on 2007-05-04
I just made the switch to Ubuntu today on one of my sytems. I use a Linksys psus4 to connect my printer (Epson Acculaser c1100) to the network. I can find drivers for the printer, but i can't find a way to get my printer to work, i don't know how to install him.
In windows i use the program that comes with the psus4 that makes a connection of the printer to a virtual port, but this program doesn't exist for linux.
can someone explain me how i can get it to work in Ubuntu?

I use the Ubuntu 6.06.1

---

### Post by Seisen on 2007-05-04
Where did you find the drivers at?

---

### Post by bb-g on 2007-05-04
i found the drivers at the epson-site. The main problem is the drivers/utility program of the psus4 OR me who doesn't know how to get the setup to work.

---

### Post by Seisen on 2007-05-04
Try these directions and see if they work to get the printer installed.

[http://ubuntuforums.org/showthread.php?t=105590&highlight=aculaser]("http://ubuntuforums.org/showthread.php?t=105590&highlight=aculaser")

---

### Post by lazyart on 2007-05-04
Linuxprinting.org is a great place to learn of printer compatibility and driver info.

Lookee here: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100)

That should get you started.

Since it connects to the network, go to System->Administration->Printing and click on new printer.  Select Network Printer and enter the IP address that the psus4 is configured for.  You'll first need the driver from the link above.  Hope this helps!

---

### Post by zorg_4 on 2007-06-06
bonjour : 

System->Administration->Printing and click on new printer. 

Unix printer (Lpd)
IP address of the psus4
queue on the 3° box

[www.arlydepannage.com](www.arlydepannage.com)

---

