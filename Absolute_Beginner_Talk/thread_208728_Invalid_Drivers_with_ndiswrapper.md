---
title: "Invalid Drivers with ndiswrapper?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by mikeymike1 on 2006-07-04
FYI: My wireless card is a TRENDnet TEW-421PC. 

 I installed my **Mrv8000c.inf** file with ndiswrapper.  I checked to see its status by typing ndiswrapper -l  and it said: 
*Mrv8000C invalid drivers* 
What am I doing wrong? Of course, any help is greatly appreciated.

Thanks and I hope I'm not being too vague, 
Mike

---

### Post by Apple 101 on 2006-07-04
You need the .inf file and the .sys file for ndiswrapper.  You appear to only have the .inf file.  Get the .sys file and try ndiswrapper again.  You can also use ndisgtk to perform the commands for you (available from Universe).

---

### Post by luger on 2007-09-14
This is the exact same problem I am having, with the same piece of hardware from TrendNet. I have moved the INF and SYS file into the same folder (mrv8000c) and tried installing using the ndiswrapper GUI and after "Installing Drivers" using that, nothing shows up in the installed driver window. Then when I go into the Terminal and check on the driver, it says "Invalid Driver". 

I cannot access the internet from that computer right now so I can't copy and paste any info at this time but can do my best to pick out any info and type it out as needed. Any help would be greatly appreciated.

---

