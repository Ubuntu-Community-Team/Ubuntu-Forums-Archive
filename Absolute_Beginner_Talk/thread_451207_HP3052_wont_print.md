---
title: "HP3052 wont print"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Xiequn on 2007-05-22
Hello, I've just installed feisty on my dell inspiron 630m laptop. Mostly seems ok, still need to check it out.
Having DIFFICULTIES with my HP 3052 all in one. It works fine on XP. Feisty sees it. Device manager sees it. CUPS sees it.
I checked the drivers mentioned throughout the numerous posts here. I've got foomatic and hplip and postscript and whatever the heck else.
When I send a print job it says it does it!!
Ha, I say, and Ha again!
		
LaserJet-3052
	
  Home      Administration      Classes      Documentation/Help      Jobs      Printers  
  	
LaserJet-3052 (Default Printer)
	Description:
Location:
Make and Model: HP LaserJet 3052 Postscript (recommended)
Printer State: idle, accepting jobs, published.
Device URI: hpfax:/usb/HP_LaserJet_3052?serial=00CNCJ102560

Print Test Page Stop Printer Reject Jobs Move All Jobs Cancel All Jobs Unpublish Printer Modify Printer Set Printer Options Delete Printer Set As Default Set Allowed Users
Jobs

Search in LaserJet-3052: Clear

Show Completed Jobs Show Active Jobs

Showing 6 of 6 jobs.
  	Sort Ascending 	 
ID  	Name  	User  	Size  	Pages  	State  	Control 
LaserJet-3052-9  	Test Page  	xiequn  	19k  	1  	completed at
Tue 22 May 2007 04:35:02 PM CST  	 
LaserJet-3052-8  	Test Page  	guest  	19k  	1  	completed at
Tue 22 May 2007 04:29:18 PM CST  	 
LaserJet-3052-7  	Test Page  	xiequn  	150k  	1  	completed at
Tue 22 May 2007 04:26:46 PM CST  	 
LaserJet-3052-6  	Test Page  	xiequn  	150k  	1  	completed at
Tue 22 May 2007 04:26:34 PM CST  	 
LaserJet-3052-5  	Te		
LaserJet-3052
	
  Home      Administration      Classes      Documentation/Help      Jobs      Printers  
  	
LaserJet-3052 (Default Printer)
	Description:
Location:
Make and Model: HP LaserJet 3052 Postscript (recommended)
Printer State: idle, accepting jobs, published.
Device URI: hpfax:/usb/HP_LaserJet_3052?serial=00CNCJ102560

Print Test Page Stop Printer Reject Jobs Move All Jobs Cancel All Jobs Unpublish Printer Modify Printer Set Printer Options Delete Printer Set As Default Set Allowed Users
Jobs

Search in LaserJet-3052: Clear

Show Completed Jobs Show Active Jobs

Showing 6 of 6 jobs.
  	Sort Ascending 	 
ID  	Name  	User  	Size  	Pages  	State  	Control 
LaserJet-3052-9  	Test Page  	xiequn  	19k  	1  	completed at
Tue 22 May 2007 04:35:02 PM CST  	 
LaserJet-3052-8  	Test Page  	guest  	19k  	1  	completed at
Tue 22 May 2007 04:29:18 PM CST  	 
LaserJet-3052-7  	Test Page  	xiequn  	150k  	1  	completed at
Tue 22 May 2007 04:26:46 PM CST  	 
LaserJet-3052-6  	Test Page  	xiequn  	150k  	1  	completed at
Tue 22 May 2007 04:26:34 PM CST  	 
LaserJet-3052-5  	Test Page  	xiequn  	150k  	1  	completed at
Tue 22 May 2007 04:10:29 PM CST  	 
LaserJet-3052-3  	Test Page  	xiequn  	150k  	1  	completed at
Tue 22 May 2007 03:01:57 PM CST  	 
  	Sort Ascending 	 
	
	 
	Nothing is printed, printer is on, has paper, toner etc. 
So, What do I do here?
Also, will the scanner and fax part be this difficult too??

Thank you for taking the time to read this rant.
Jen:confused:

---

### Post by dstew on 2007-05-22
What version of hplip do you have? I am not sure, but if you are using hplip, which I think you are since your device is hpfax, you might have to use the non-postscript driver hpjis. I think **hp-check** on the command line will show the status of the hplip system. **hp-setup** will let you pick the correct driver (a foomatic driver with hpjis in the name).

---

### Post by Xiequn on 2007-05-22
DSTEW, you are so good!
That was it. Works perfectly:D:D
Thank you very much,

Happy little chicken

---

