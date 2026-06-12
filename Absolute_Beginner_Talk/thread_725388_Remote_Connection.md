---
title: "Remote Connection"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Windy George on 2008-03-15
Hi All:

Brand new to Ubuntu, been trying Linux for years this is the first one that installed and worked as expected.  System A is Windows Vista OS,  system B is Ubuntu.  Ubuntu goes on line perfectly and I am able to browse the shared folders on the Vista system from the Ubuntu system, and copy files from Vista to Ubuntu.    The Vista system does not see the Ubuntu system.  I have tried every combination of connecting to the Ubuntu system from the Vista system to no avail.  My Laptop is a Windows XP OS and I am unable to see the Ubuntu system from it either.  Otherwise, the Vista and XP  systems see and speak to each other very nicely.

Now I know that I am messing something up, but I do not know just what it is I am messing up.  Is there a tutorial some where that might help out an old IBM'er.    Any suggestions would be appreciated

PS: I have tried the Vista forum as well.

George

---

### Post by Forrest Gumpp on 2008-03-15
Try aysiu's Ubuntu Linux Resources for some good background, and perhaps very specific information.  See:  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

There are other pages on partition planning you will be able to reach from the links on this page if it does not help you directly.

---

### Post by prshah on 2008-03-15
> **Windy George said:**
> Hi All:

My Laptop is a Windows XP OS and I am unable to see the Ubuntu system from it either.  

George

Install Firestarter (a reasonable front-end to iptables) and Allow connections on "samba (smb)" ports (137-139 and 445) for your vista machine's/laptop's IP.

---

### Post by Windy George on 2008-03-16
HI ALL:

I tried Firestarter, Ubuntu system still not seen by vista system.  Remote connect on the Vista system will not connect with Ubuntu system, gives error message that the credentials used were not valid.  I only have two users set up on the Ubuntu system and neither will work to connect from the Vista system.

Also, the printer on the Vista system is a Samsung ML-2510 and it is shared, I have downloaded the Linux driver for the printer from Samsung but I have been unable to install it.  I also have the printer CD and getting the driver from there hasn't happened yet.  The driver has an install but gives a error about not establishing the hardware platform yet.  

Still trying!

George

---

### Post by Faud on 2008-03-16
Can your XP system see your Ubuntu ? using Samba. I know that at my house the only difference being that a user name and password must be added for my wifes XP computer to see and write to my shared folders.

---

### Post by Windy George on 2008-03-17
Hi All:

Thank you all that have responded, you've have been very helpful but I have not managed to get this done yet.  Neither the laptop with XP or the desktop with Vista see the desktop with Ubuntu.  Ubuntu does see both of those and will let me copy files from either.  The remote connection on the Vista OS argues that my credentials are incorrect.  Hyperterminal on the XP OS just does not see the Ubuntu system, it is 'Unable to connect'.  

I have been trying to install the driver for a shared printer on the Vista system.  The printer is a Samsung ML-2510 and I have the driver on the CD that came with the printer as well as a newly downloaded driver.gz.  I am sooooo close.  After extracting the driver file and moving to that directory *_sudo aptitude install install_*  goes through the motions but states that nothing will be installed because root privilege is required.  Running the GUI Printers in administration does see the printer and verifies the connection.  There is no Samsung ML-2510 driver in the list, that is why I downloaded one from Samsung.

I down loaded and printed "How to install ANYTHING in Ubuntu" by Simon Grey. it is an excellent set of instructions.  It almost got me going with the printer, I am still missing something.  I appreciate all of the suggestions that have been put forth, I will keep trying.  

George

---

### Post by Faud on 2008-03-17
[https://help.ubuntu.com/7.10/internet/C/networking-shares.html](https://help.ubuntu.com/7.10/internet/C/networking-shares.html)

---

### Post by Windy George on 2008-03-17
Hello Faud:

BINGO, using the Start, Run, \\ipaddress worked to allow the Vista system to see the Ubuntu system.  Thank you very much.   

I am still trying to get a terminal connection on the Vista system to connect with and work to the Ubuntu system.  Any more magic there???? 

Thanks again for the help with the first part of this problem.  

George

---

### Post by Windy George on 2008-03-19
Hi All :

Well, I now have a terminal running from Vista to Ubuntu.  I found two terminal emulator programs both shareware, the Nexus Terminal and Eric's TelNet 98.  They both connect up easily to the Ubuntu system using SSH(2) and emulate a VT220 terminal.  I am not sure which one I'll keep, still have time to decide.  

I have not been able to find any freeware terminal emulators that are Vista enabled.

Still trying to resolve the use of the shared Vista printer by Ubuntu.

George

---

