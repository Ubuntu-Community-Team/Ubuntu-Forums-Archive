---
title: "Windows box can't connect to HP PSC 2100 printer served by Ubuntu"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by oldtappan on 2007-04-11
I've served out my HP PSC 2100 from my Ubuntu 6.10 box.  My Windows machine can see it but when it tries to connect to the printer, it complains that it doesn't have the driver.  The [driver ]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=79488&lang=en&")for this specific model doesn't ship with Windows but is available from HP.  So I downloaded the HP driver file [it's a 160MB hairball and contains a bunch of drivers] yet Windows is still not available to install the driver!  

So is there another way I can print from my Windows box to this specific printer on Ubuntu?  Is there a way to "trick" Windows to do this?
Thanks.

---

### Post by crispy_420 on 2007-04-13
160MB for a driver! That is insane. What other garbage do they pack in there? Lots of extra software like image viewers and print tools?

I'll boot up windows and look into it.

Install that massive driver. If possible not installing some of the extra bloat. You only the driver after all.
Go to your control panel in Windows (assuming XP here or maybe Win2000 too). 
Top right there is Printers and other hardware.
If you can see your networked printer, right click and select properties.
In the new window under the "Advanced" tab select "New Driver".
Select "Have disk".
Most likely the driver ended up in your system32 directory. So let it search there (windows install drive -> windows -> system32). It may even say the driver name it wants to use, so if you see it just click it.

Now give it a test run.

Did that help you?

---

### Post by crispy_420 on 2007-04-14
Another option besides installing all that extra stuff (99% of that download) is to just unrar that file with [WinRAR]("http://www.rarlab.com/download.htm"). And just point that driver search to that folder.

---

### Post by oldtappan on 2007-04-14
Thanks Crispy for the advice.  Here's some more info:

Running the 161MB driver .exe, expands the file into several subdirectories.  These directories contain .inf, .sys and other files.  I tried to use the "New Printer Wizard" > "Have Disk" functionality to go through the directories and install the driver.  The wizard is set by default to search for .inf files.  I ran thru the wizard several times and selected various .inf files, yet it didn't like any of the drivers!   This is very strange because of a number of reasons.  What I'm trying to do is replace a Windows 2003 server that's currently acting as my print server with Ubuntu.  Currently my client machines (currently XP, Vista and Ubuntu) can connect to the 
Windows 2003 server and use the network printer.  That working fine.  So this means that all of the Windows clients have the HP PSC 2100 printer driver ALREADY installed.  So, I replaced the Windows 2003 server with an Ubuntu box and I'm trying to get the Windows clients to connect to the HP printer shared out by Ubuntu.  So installing new drivers on the Windows machines shouldn't be necessary since they already have the driver, yet when Windows tries to connect to the HP printer shared by Ubuntu, it asks for a printer driver.  And the correct printer drivers don't seem to work.  This is very strange.  

Is it possible that there's a mismatch in the way that Ubuntu is reporting the HP printer model and the way Windows is trying to find the driver based on reported printer model?  Is there anything specific I can do in the smb.conf file to rectify this?

---

### Post by Purplecatty on 2007-08-13
Anyone who are struggling with HP PSC 2175 All-in-One printer driver on XP client machine while Ubuntu Feisty Fawn 7.04 which is connected to printer. The XP Client machine don't have driver for it and it cannot find driver from HP PSC 2170 serie CDrom.

I found a way to get it working. Best thing is to install HP PSC 2175 driver from CDrom on Client XP machine first. Just check radio button "proceed installation without plugging in USB". After installation. then follow this instruction below..

On XP machine. Navigate to Printers and faxes in Control Panel or Start Menu (if listed), Click "Add Printer" and choose Network Printer and then choose radio button "Connect to a printer on an internet..." and type URL

"http://<printserver name>:631/printers/psc-2175"
(Printserver name is what on your Ubuntu box like example "John-Desktop" or "Kitty-Desktop".. You can find Ubuntu's server name on XP Client's network printer browse for quicker reference.. Be sure to add ":631" on the end before "/printers/psc-2175")

select driver on pop up driver list "HP-- PSC-950" (it is necessary to get em shut up!)and click OK

Once new default printer icon showed up on Printers and Faxes Window.

Right click new icon for drop down menu. Click Property.

Here's the MAGIC!!!

On tabs, Choose ADVANCED and click Driver

Scroll down and BINGO!! here is HP PSC 2170 serie driver. Click on it and click OK to change the driver

Then test your printer. It should print out with no problem! (It'll show Windows XP printer driver blah blah on printout from PSC 2175 through Ubuntu print server)

If you had different model printer and can't get driver for XP client, just Install it from CDrom and setup network printer then change the driver AFTER that!!  :):):)

Do the same with your HP PSC printer of any model that you Couldn't extract driver from CDrom.  Just Install it like you normally do on Windoz printer installation.  Then follow instruction above!!  This is the key of work around!!

---

### Post by wildkarde on 2007-08-22
Just my personal experience.  I have an HP PSC 2170.  I tried doing this and it did not work. 
I went through the installation of the 160MB 'driver' setup and when it asked to connect the printer, I did.
After install was finished, I plugged the printer back on the server.  I was then able to select the correct driver.

---

