---
title: "printer installation"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by pieniaszek on 2007-10-09
I have a HP Deskjet D4260 connected via USB to a Dell Dimension 4550. XP is installed on the master hd and Ubuntu on the slave. I searched for a driver and finally found Foomatic and a D4200 driver on the [http://linux-foundation.org](http://linux-foundation.org) web site.  I assumed that's the closest I will get to D4260 and downloaded the PPD file.

I can't even try to see if that will work because no printer is recognized. I checked to see if the USB ports were identified, and it appears they were.

What do I do to have Ubuntu recognize the printer?

By the way, I did not realize I had installed foomatic by the add/remove process and there is no way to find out by selecting Printers in the System pull-down.  I guess one is expected to jot down the details of all the software installed because once it is the pulldowns don't identify the vintage.

---

### Post by bumanie on 2007-10-10
There is no need to go to a third party source - go straight to HP. Hp support linux and have packages and/or install commands to use in terminal.
If you go here
[http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html](http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html)
you should be able to find what you need.
I recently bought a HP f4185 and installed it successfully under ubuntu by using the HP site.
PS: Just a side issue, but gutsy gibbon (due 18/10) apparently will recognise your printer when plugged in and install drivers without you have to do anything.

---

### Post by Orbital75 on 2007-10-10
Plug in your Printer to your USB
Now, type this into your Browser:  **[http://localhost:631/admin](http://localhost:631/admin)**
Under the Printer Tap, you should see your Printer.
Choose your Printer and then it will ask you again and it will be highlighted.
Choose OK and you will be asked for your User Name and Password.
Type that in and your all set...... 

Good luck....  :KS

---

### Post by pieniaszek on 2007-10-11
No success at [http://localhost:631/admin](http://localhost:631/admin)

/usr/lib/cups/backend/socket failed

What's a socket and what does have to do with having a printer connected on a USB port?

I'm really a newbie and probably should try to understand what that CUPS is and what it is telling me at that file location.

I had a 'ppd' driver from HP on my desktop and selected that file for installation.

---

### Post by pieniaszek on 2007-10-12
How can I tell that Ubuntu is even acknowledging that my D4260 Printer is connected to a USB Port?  A CUPS ppd file installation using a driver I downloaded, appears to have accepted the driver, but a test page goes into a queue.  

I had two computers hooked to a Belkin USB two switch and suspected that, but when I connected the cable direct, I still have no printer response.

---

### Post by Daveth on 2007-10-12
I think

```
lsusb  -v
```

should show whether it is seen - or not.

---

