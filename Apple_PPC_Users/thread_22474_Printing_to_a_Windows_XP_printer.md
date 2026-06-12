---
title: "Printing to a Windows XP printer"
date: 2005-03-27
forum: Apple PPC Users
---

### Post by tater on 2005-03-27
Please someone, put me out of my misery and help me get my printer working.  I've tried a zillion different things today, but basically, here's what I'm doing.  I go to System, Administration, Printing, Add printer.

I choose SMB.  I've tried all different flavors of my hostname (the name of my windows machine) such as, if it were "machine", I've tried:

machine
/machine
//machine

and I've tried putting in it's ip number in these three flavors as well.

I put in the name of the printer, with slashes, without slashes, all different ways.

By the way, yes, the printer on the Windows XP machine is turned-on for sharing -- I have been using it as my printer here for two other Windows machines just fine for ages.

My printer is a Brother MFC-210C, but there are no drivers for it.  I choose MFC-9100c, because it is close in functionality and also uses the sort of generic epsonc for the driver.  But this isn't the problem, as I never actually get to the printer.

What I get when I try a test page, and then look at the test page's properties in the printer window is that it's unable to connect to the host.

And, oh gosh, can't find it now -- I tried that command that shows you if you can see everything on the other computer, it's something like smbclient //machine and yes, I can see all of my shared folders on "machine" and the printer.

Any ideas?  Help.

Thanks in advance,
tater

---

### Post by localzuk on 2005-03-28
This does indeed appear to be a problem. I have a network connected HP Lasejet 5N and I usually just connect to it via IPP, directly from one machine then use that as the spooling machine  - then connect to that CUPS server from any other machine.

I tried setting up a shared printer on my windows box and I have the same problem as you. It isn't the setup tool that is causing the problems either (as I have tried using the KDE printing manager also). It appears to be a broken CUPS that is doing it.

Have you tried connecting the printer directly to your linux machine and then having it share the printer via SMB?

---

### Post by tater on 2005-03-28
Well, it helps to know I'm not alone in this problem.  If you find anything that works, please let me know.  I'll keep experimenting as well.

No, I haven't tried connecting the printer directly to my mac.  It might be an interesting experiment, but I wouldn't want to use the mac for my printer server.  It's a Powerbook Pismo, so hanging the printer on it sort of defeats the fun of having a wireless notebook computer.  8) 

tater

---

### Post by tater on 2005-03-30
I still cannot print to my Brother MCF-210C printer, because I cannot find a printer driver written for ppc that will make it work. 

However, I am much farther along, and perhaps I can save someone else some major headaches in trying to print to a shared printer hanging off of a Windows XP machine.

First off, the windows machine is running Windows XP Home edition.  So, it doesn't have the capability of running "internet informations service" iis.  I did not know this.  The only option is running Unix LPD-LPR for it, but even this has to be installed and turned on.  

On the Windows XP machine, go to Control Panel, Add/Remove, Windows Components, and pick Other Network File and Print Services.  Choose install.  The files are already on the machine, so the installation is a breeze.

Then go to Control Panel, Administration Tools, Services, and choose the TCP/IP Print Server.  Change the startup type to Autorun.  Click the restart button.  Ok out of that.

Now, you'd think everything would be fine, to go back to the Ubuntu mac and get the printer running from there, however, if you have Windows XP Service Pack 2 on your windows machine, the windows firewall defaults to ON.  In other words, it's not going to allow the Ubuntu machine to print through it.

I had to find out which port the printing came in on.  Go to Control panel, My Network Connections, and on the left hand side of the screen, click on "Change Firewall Settings" and then the Advanced tab.  Click on Create a log file, and set up the log file.  OK out of that.

Back to the Ubuntu machine.  I went through the Add Printer thing again, only this time, I choose to set up Unix LPD-LPR printer.  In Host, put in the IP of the Windows XP computer.  In Queue, put in the printer name.  You know the rest of the drill, that is, on the next screen, pick out your printer, and complete this setup.

Now, choose to print a test page.

Go back to the Windows XP machine and open the firewall log file, wherever you saved it, whatever you called it.  I let it go to the default location and filename of C:\\Windows\pfirewall.log.  You'll see your Ubuntu machine in there as trying to send a print, and it will say rejected.  It will also show the port it was coming in on.  For me, this was port 515.

Now open that port.   Go to Control panel, My Network Connections, and on the left hand side of the screen, click on "Change Firewall Settings" and then the tab Exceptions.  Click Add Port.  On the screen that opens to add a port, put in any name you want to, and put in the port number you saw above, which, like I said, for me is 515.  Leave the TCP radio button selected.  Ok out of this.

If you want to watch the Ubuntu test printing page come through (that you are about to send in the next step) on the Windows XP machine, you can go to Control Panel, Printers&Faxes, and click on your printer, to open the printer's activity window.

Back to the Ubuntu machine.  Cancel the test page that's running, that hit the firewall in the previous steps, and choose to send another test page.  Do this while watching the screen on your windows machine, the printer activity window.  If everything's working, you'll see the test page go through the window's printer activity window.

I was so overjoyed when I got this far.  I know now that my Ubuntu mac is sending the test page, and that it's going through the windows machine and out to the printer.  Now, all I need is a driver that will work for the Brother MFC-210C.

I wrote to Brother and ask them about a ppc Linux driver.  Here is the next-day (prompt yet disappointing) reply they sent:

"The Linux LPR driver for MFC210C is available
just for i386 CPU(80386 compatibility).
We're afraid we are not providing you
with drivers for CPU of PowerPC."

Anybody know of any driver that will work, even if it's just for text-only????

Hope this helps someone get their networked printer going.

tater

---

### Post by Tomas_IV on 2005-03-31
I had similar problems: It was said the printer is printing, but it did nothing. Then I found that in the printer properties appears an error message about failed autentication (while everywhere else it still seems the printer is printing).
This helped:
Open Gnome Panel | Computer | System Settings | Network. In the "Common" tab fill the field "Domain" with the workgroup in which the XP machine with printer belongs. (Filling anything may work, but I did not tested. Every Windows machine has a generic workgroup set by default, so maybe the problem is that Ubuntu does not.)
Then add the network printer again as Windows (SMB) printer.

Not sure about exact menu/tab/field names above - I have it all in Czech, but still hope this can help.

---

### Post by tater on 2005-03-31
Thanks Tomas, but I have now totally confirmed that the problem is a lack of a driver for the Brother MFC-210C printer.  

As an experiment, I hung the printer directly off of my Ubuntu mac.  In "Add a printer," the printer was recognized correctly, as MFC-210C.

I tried every printer driver, for all brand names and generic, one at a time, trying to get the printer to print a test page.  Nothing worked.

For many drivers, the printer's LCD showed "receiving data," however, it stayed there forever.  I would leave the computer and printer sitting there, with the printer showing "Receiving Data" for up to 30 minutes.  Nothing ever came out of the printer.

I'm completely stuck at this point.

tater

---

### Post by Mickael on 2005-06-02
Hi,

I'm also struggling with setting up an MFC 210c but this is for a Mandriva distribution. I have the printer correctly set up on my XP machine but I just can't set the printer on my linux one.
I am 100% new to linux tech so I'm not quite sure what is or what's not possible. For instance I found this driver [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) but I'm not sure if this shows that there is a real possibility to have the printer working on linux.

Any idea?

Mickaël

---

### Post by billsimcox on 2005-06-18
_**Situation**_

MS XP box has a HP OfficeJet 4110 (multifunction device) connected to it. I want to print to ths device from my Ubuntu box.


_**Solution**_

On the Ubuntu box:

System>administration>printing>new printer

Connection = SMB Network
Host = xphome (replace with your XP box name, caps sensitive)
Printer = HP (again, replace with your printer's share name)
Username = leave blank
Password = leave blank


On the XP box:

control panel>printers & faxes>right click on printer>properties>ports tab>uncheck "enable bidirectional support"

That is it!!   :)

---

### Post by grnemo on 2006-09-12
Thx Mate :d:d:d:d

---

### Post by roadrawts on 2007-05-23
> **tater said:**
> Thanks Tomas, but I have now totally confirmed that the problem is a lack of a driver for the Brother MFC-210C printer.  

As an experiment, I hung the printer directly off of my Ubuntu mac.  In "Add a printer," the printer was recognized correctly, as MFC-210C.

I tried every printer driver, for all brand names and generic, one at a time, trying to get the printer to print a test page.  Nothing worked.

For many drivers, the printer's LCD showed "receiving data," however, it stayed there forever.  I would leave the computer and printer sitting there, with the printer showing "Receiving Data" for up to 30 minutes.  Nothing ever came out of the printer.

I'm completely stuck at this point.

tater
Tater,

Did you ever fix your problem of the printer not printing the test page.  I now have the same problem on a HP OfficeJet 5610.  Ubuntu sends the test page to the printer, it makes a few noises, and then just sits there forever saying 'printing....' on the printer display and in the print queue manager.  Need some help.  Am very frustrated.  Tried New Printer, Windows SMB, and everything is recoginzed properly.  And it does send something to that printer.  So maybe it's a driver problem????

---

