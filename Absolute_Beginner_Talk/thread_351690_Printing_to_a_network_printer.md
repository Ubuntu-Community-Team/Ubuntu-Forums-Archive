---
title: "Printing to a network printer"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by ray.rogers on 2007-02-02
Greetings, I am a user in a large-network school, and I have a project to print to a networked printer.  We are on 192.168.1.X, and the printer is staticly set for 192.168.1.4.  It is a HP Lazerjet 2200.  Thank you for any help.

---

### Post by Patrick K on 2007-02-02
Have you been to the CUPS site? [http://www.cups.org/](http://www.cups.org/) A lot of info there. 
Here is the site I used when setting up my printer on a D-Link print server, might help:
[http://gentoo-wiki.com/HOWTO_D-Link_DP-100_HW_Printerserver](http://gentoo-wiki.com/HOWTO_D-Link_DP-100_HW_Printerserver)

---

### Post by dstew on 2007-02-02
CUPS is needed. With Xubuntu, there is a web-page configuration manager for CUPS printers that is installed along with CUPS. It worked for me to share a Windows shared printer. If your printer is directly on the network it should be easy.

---

### Post by bcom on 2007-02-02
Here is how I set up a printing on a Windows network via a print server.  Your situation is probably different but this might help point you in the right  direction.

System - Printing - Add Printer

Select Network Printer in the Add Printer Dialog box and then select Unix  Printer (LPD) from the drop down box.

This should bring you to a place where you can enter two pieces of information - Host and Queue.  For Host I entered the IP address of my Print Server.  For Queue I entered L1 or L2 depending on which port the printers are connected to on the print server.

In your situation, the Host information would be 192.168.1.4 and the Queue might be L1.  BTW, its important to enter a capital L, not a small l.  If you enter l1 or l2 instead of L1 or L2, it won't work.

Oh yes, after you enter this information I believe you will be asked to install the driver for the printer.  This part is fairly straight forward as you only need to find your printer on the list and click your way through.

---

### Post by Robotuner on 2007-02-02
Interesting, I am trying to get Edgy to see my windows printers.  I have one directly connected to a machine and another on a print server (192.168.111.8).  I haven't gotten it to work, but then I have been trying to go through Windows (SMB) instead of CUPS or Unix.  I figured cups was for printers on a linux network and unix was unix.  

It never would have occured to me to go the unix route.  Don't understand why, but thanks!  Any hints on accessing the laserjet directly connected to one of my other windows machines?

---

### Post by Robotuner on 2007-02-04
Turns out that for a printer not directly connected to the lan via a print server, but connected to a winxp machine through the lpt port, all I had to do was use Windows Printer (SMB) and specify the computer name as the host and the name of the printer as defined in the windows printer configuration.  Works great that way.

---

### Post by thomas.mckay on 2007-02-06
> **bcom said:**
> Here is how I set up a printing on a Windows network via a print server.  Your situation is probably different but this might help point you in the right  direction.

System - Printing - Add Printer

Select Network Printer in the Add Printer Dialog box and then select Unix  Printer (LPD) from the drop down box.

This should bring you to a place where you can enter two pieces of information - Host and Queue.  For Host I entered the IP address of my Print Server.  For Queue I entered L1 or L2 depending on which port the printers are connected to on the print server.

In your situation, the Host information would be 192.168.1.4 and the Queue might be L1.  BTW, its important to enter a capital L, not a small l.  If you enter l1 or l2 instead of L1 or L2, it won't work.

Oh yes, after you enter this information I believe you will be asked to install the driver for the printer.  This part is fairly straight forward as you only need to find your printer on the list and click your way through.

Thank you very much. I was previously using someone else's account (I ahve now registered), and it has worked. Thank you so much for your help.

---

### Post by tesseract420 on 2007-02-08
After completing the steps above (in installing the Unix printer) you get a Step 3 (of 3): Printer Information, requiring you to fill out "Description" and "Location". I thought these were important, but the "Ubuntu Linux for Non-Geeks" (at p. 172) lists, "my cat's favorite place to sleep" for the descriptio and "the messy office" for "Location" so obviously these aren't critical. 

Unfortunately it still didn't work.

The test page read: "%!%PS-Adobe-3.0
                                                          %%Title:  PPR Test Page
                                                                                              %%DocumentNeededResources:  font: Helvetica %

followed by ten or so blank pages. 

I'm using a Xerox WorkCentre M123 printer. Xerox says the printer isn't supported under Linux, but there is a Mac OSX ppd file. I used the Max OS X ppd file for the printer, so maybe this is the problem. On the other hand, 6.06 LTS seemed to recognize the ppd file without any problem, and after installation listed the printer in the database.

I have previously tried "http://localhost:631" in order to access the CUPS menu, but no luck.

I just sat with my system administrator, and during "add printer" we found the network, but not the printer. However (and referring to the install unix printer steps above) the IP address of the printer and the queue L1 seem to be correct because, even though the test page printed improperly, it still did print.

I'm now at a loss. Anyone have any ideas?

---

### Post by floundered on 2007-02-09
> **Robotuner said:**
> Turns out that for a printer not directly connected to the lan via a print server, but connected to a winxp machine through the lpt port, all I had to do was use Windows Printer (SMB) and specify the computer name as the host and the name of the printer as defined in the windows printer configuration.  Works great that way.

Or more specifically, for those still searching for instructions:
[LIST=1]
[*]From the main Xfce panel click on **Applications->Settings->Printing**
[*]Select **New Printer**
[*]Enter a friendly name, description, and location for the printer.  What you enter here will be seen when you print from an application and select a printer, so it's your choice.  Click **Forward** when done.
[*]Select "**Windows Printer via SAMBA**" from the list on the left.
[*]I think the large field in the middle is meant to **browse the network** for a printer, but it did not show anything on my system other than the workgroup name.  If it helps you, great, but it's not necessary.
[*]In the top field that starts with "smb://" enter the Windows network name of the printer in the form "***ComputerName/PrinterName***" (no quotes).  For example, if your computer was named Redmond and the printer HP1220C then you would enter "Redmond/HP1220C"  (no quotes) in the box.  On my Xubuntu-to-WinXP system, I noticed that these fields were not case-sensitive.
[*]Enter a **user name** and **password** for an account that's already set up on the Windows machine.  It is not necessarily the same as the Xubuntu username and password, but must match an existing account on the windows machine.  Being a smart Windows user you have of course disabled the Guest account on the windows machine, so you'll need something here.
[*]Click **Verify**.  A small dialog box will pop up to let you know whether the printer was accessible or not.  (I noticed that the printer was always declared accessible regardless of what I did or didn't enter for the name and password, but printing only worked with the correct name and password, so be sure to enter those correctly.)  If printer is "inaccessible", go to the Windows system and double check the name of the computer and printer, and ensure that the printer is shared.  Click **Forward**.
[*]Select the **printer brand** from the list, or provide a PPD file if you know what that is.  **Forward** you go.
[*]Pick the desired **printer model** and then the **driver** from given lists.  If "Gutenprint" doesn't mean anything to you then just pick the normal printer model if possible.  To help select the correct printer and driver click on the **Printer, Driver, and PPD** buttons, which will reveal very helpful text for many of these items.  When in doubt, select the most normal looking printer model (no "Gutenprint" unless you have it) that matches your setup, and also select the driver marked as "recommended".  **Forward** ho.
[*]Try clicking on **Print Test Page** and see if the printer spits anything out for you.
[*]Select your default printer **settings** and other bits to your satisfaction.
[/LIST] 

Also note that you can open up your web browser and enter the address **[http://localhost:631]("http://localhost:631")** to see the internal CUPS server page, where you can manage the current print jobs and mess about with other settings.  It may help to add a panel or menu launcher or just a browser toolbar bookmark to quickly get to **[http://localhost:631/jobs]("http://localhost:631/jobs")**. (This is nice for all the times when, if you're like me, you've accidentally started to print all 567 pages of some PDF instead of just the current page.)

---

### Post by tesseract420 on 2007-02-10
I'd love to use the 'localhost' option, but I get this message:

I typed "http://localhost:631" and got:

"ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: [http://localhost:631/](http://localhost:631/)

The following error was encountered:

* Connection Failed

The system returned:

(61) Connection refused

The remote host or network may be down. Please try the request again. "


Putting that aside, on 6.06 LTS at least, there's no xfce choice and the only way to get to printers is via System--printers. Doing it that way, you don't come across with a smb:// option at all. 

Still not printing, any other suggestions?

---

### Post by Coburn on 2007-02-28
Your localhost problem is not permanent.

Most likely it is a problem with your firewall or network settings.  I played around with mine until I was able to use the CUPS webmin utility.  Though the Gnome print manager does almost the same thing.

---

### Post by tesseract420 on 2007-03-10
I upgraded to Edgy and was able to access [http://localhost:631](http://localhost:631).
After following all the steps, my test page consists of one page with one line, followed by ten or so blank pages.

There's a windows network in the office, and the printer is a standalone printer not connected to any pc.

anyone have any ideas?

---

### Post by Detonate on 2007-03-10
Try [http://127.0.0.1:631](http://127.0.0.1:631) and see if that works.

---

### Post by dstew on 2007-03-10
Are you sure CUPS is installed? If so, how did you install it? The fact that you cannot connect to the CUPS web print manager suggests that either CUPS is not installed, or is not installed correctly. In order for it to work, it has to be installed from the Synaptic package manager, and you have to install it from the correct disk (the one that matches your Ubuntu installation).

Finally, in Xubuntu at least, you need to add the user cupsys to the group shadow. I don't know why, I think it is a bug. The cupsys user is created when installing cups, and the group shadow was already there on my system, but you need to put the user cupsys into shadow.

---

