---
title: "yet another xp printer sharing help request"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by stormoog on 2005-11-20
I installed Ubuntu yesterday, and I have to say I like it. I've had some startup problems, but the answers to most things are in the forum :)

The only thing I can't seem to fix printing to/with my HP LaserJet 1020 attached to an XP machine.

I've so far tried this:

[COLOR="Red"]Step 1: Installing Samba on Ubuntu

    * Click System -> Administration -> Synaptic Package Manager
    * Enter your password
    * Now click Search and type Samba in the search box.
    * You should now see a list of items containing the word Samba.
    * Right click on the Samba with the little ubuntu icon on it and select mark for installation.
    * Click apply
    * The packages will now be downloaded and installed.[/COLOR]

(all ok, I rebooted here to be sure)


[COLOR="Red"]Step 2: Checking if your network is working

    * Find the ip address of your windows xp machine by going ... start -> run
    * Then type cmd
    * type ipconfig in this window and you should see your ipaddress there.
    * Now on your ubuntu machine goto the command line
      and type ping <your windows ip address>
    * see if you get a response.

if you get timeouts:
a.) Check if your network cables are all connected
b.) Check if your network cards are working
c.) Check the settings of your network interfaces
d.) Try disabling any firewall software[/COLOR]

From what I know, the ping is succesfull. I'm also sharing the XP machine's internet connection, so I guess the network should be allright.

[COLOR="Red"]Step 3: Sharing the Windows XP printer

    * start -> settings -> control panel
    * open printer and faxes
    * find the printer you wish to share with your ubuntu machine
    * Right Click -> properties on it and goto the sharing tab.
    * Click on share this printer and type a short name in the share name box.[/COLOR]

I called it "Laserjet 1020" (it had that name from before). I hope that the space in the name is not a problem.

I also did this:
[COLOR="Green"]On the Windows XP machine, go to Control Panel, Add/Remove, Windows Components, and pick Other Network File and Print Services. Choose install. The files are already on the machine, so the installation is a breeze.

Then go to Control Panel, Administration Tools, Services, and choose the TCP/IP Print Server. Change the startup type to Autorun. Click the restart button. Ok out of that.[/COLOR]

and I shut off the SP2 firewall between the computers.


[COLOR="Red"]Step 4: Adding the printer on the Ubuntu machine

    * System -> Administration -> Printing
    * Click Printer -> Add Printer
    * Click on network printer.
    * Select Windows Printer (SMB) from the dropdown.
    * In the host section type the IP address of your windows machine.
    * In the printer section type the share name you gave your printer
    * Now enter your username and password for your ubuntu machine.
    * Click forward.
    * Now select the manufacturer and model of your printer.
    * And finally click on Apply.
[/COLOR]

But nothing happens. If I print, I get a printer icon next to the clock for a short while, and then it seems to think that the print was succesfull. The printer does nothing though...

---

Edit: "[I]The LaserJet 1020 is a host-based printer (i.e. it does not have much built-in intelligence), and, as such, does not understand standard printer languages such as PCL5; it relies on the host providing the raster image.

So if your SCO Unix box is outputting preformatted PCL, this will not be properly understood by the device.[/I]"

What does that mean?

---

### Post by mechanic on 2005-11-20
I'm having similar problems, no solution as yet however (sorry). One thing I don't understand is why you need samba on the Ubuntu box - I would have thought that all you need is a ssh connection between the machines, and then the CUPS system should sort it out. Why you need a full blooded file and print server on the U. machine I don't follow.

m.

---

### Post by deNoobius on 2005-11-20
Similar problems here, have tried CUPS and SAMBA.  I'll definitely post if I solve the problem.  It is my one great disappointment with Ubuntu.

---

### Post by ed_d on 2005-11-20
I am running into the same problem. The XP box receives the job, and printer seems to go through the motions, but noting prints and cant seem to delete the job on the xp box. I trie "canceling" the job, but nothing, no delete and even a reboot dosent fix it.
If anyone knows how to delete the job on the xp machine (as no job on Ubuntu) let me know.

---

### Post by stormoog on 2005-11-20
I tried to install the foo2zjs printer driver, and now at least I have got a proper 

Ready: Connection failed with error NT_STATUS_UNSUCCESSFUL

error in the printer properties window...

Now what?!  :)

---

### Post by stormoog on 2005-11-20
"[COLOR="Magenta"]Open up the printer settings on the Windows box, click on the "Ports" tab and turn off (uncheck) 'Enable Bidirectional Support'.[/COLOR]"

This effectively stopped both XP #1 and XP#2 from printing. 


```

                internet
                   |
HP LJ 1020 -----  XP #1 -----------  XP #2 and Ubuntu
```

---

### Post by optikburn on 2005-12-01
I have found this link that discusses how to share Windows Printer to Ubuntu Machines.. it works...

[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html](http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html)

---

### Post by stormoog on 2005-12-02
Doesn't work for my printer, I'm afraid. But thanks for mentioning it.

---

### Post by Weman on 2005-12-21
The:

[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html](http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html)

helped me too. The trick that I missed before was in XP:
Open "Printer and Faxes" then right click on your printer then "Share", give your printer a share name that is short and with no special characters or spaces (ex. "HP940c" quotations not inclucded). 

And in Ubuntu:
Select "Network Printer" then use "Unix Printing LPD"

//weman

---

### Post by fishfillet on 2006-01-01
my share: [http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57)

---

### Post by stormoog on 2006-05-14
Tried again with Dapper Beta. Didn't work (although many of the steps were automated this time :-D )

---

### Post by Canguçu on 2006-07-28
It does not work here too. HP Deskjet 3745 on a Windows 2000 box.

---

### Post by Iso_K on 2006-08-29
Hi!

I have Ubuntu´s Dapper Drake and my printer is Canon MP150. My driver is from [www.turboprint.de](www.turboprint.de) because there´s not yet a driver in [www.linuxprinting.org](www.linuxprinting.org).

My problem was solved when I followed the instruction from the link: 
[http://raldztech.blogspot.com/2005/1...-to-linux.html](http://raldztech.blogspot.com/2005/1...-to-linux.html)

and:

The Windows XP Machine (The Print Server)

   1. Install your printer.
   2. Open your Control Panel, then open your "Add or Remove Programs"
   3. Click on "Add/Remove Windows Components" located on the left side of the dialog box
   4. Put a check on "Other Netwrok File and Print Services" then click "Details" make sure that the "Print Services for Unix" is selected. (you may need your XP CD and a reboot)
   5. Open "Printer and Faxes" then right click on your printer then "Share", give your printer a share name that is short and with no special characters or spaces (ex. "HP940c" quotations not inclucded). This Share Name would later be used as the Print Queue on your Linux machine.
   6. The Windows Firewall may block Linux machines from printing, turn off your firewall for the meantime.. we will turn it back on later.
   7. Make sure that your Windows' IP number is Static.

But I didn´t do it exactly as it says there. In the case of using  XP cd, i moved to the file i386 where i saw the needed files. Computer didn´t except them because their file names were LPDSVC and LPRMON. Files what the installation program asked were LPDSVC.DL_ and LPRMON.DL_. I just changed the names (renamed) and it went ok!

After that I installed my printer, but I installed it as an network printer: WINDOWS printer (SMB)! I gave the IP number of my XP computer and the name for the printer as well as my username and password. Now my network printing works! From Ubuntu to XP.

---

### Post by pm124493 on 2006-09-02
> **ed_d said:**
> I am running into the same problem. The XP box receives the job, and printer seems to go through the motions, but noting prints and cant seem to delete the job on the xp box. I trie "canceling" the job, but nothing, no delete and even a reboot dosent fix it.
If anyone knows how to delete the job on the xp machine (as no job on Ubuntu) let me know.

I have the same problem. You need to go to control panel and open Administrator Tools, then Services. Look for Print Spooler and STOP that service. Open an Explorer window and go to C:\Windows\system32\spool\printers\. If you have more than one printer there will be more folders so find the printer or there will be only files. Delete all the files. Go back and START Print Spooler. Your power off your printer to clear the buffers and you should be okay. There is a conversion problem with the Linux driver for some HP models. I have an PSC1315 and it hangs.

---

### Post by ffchaves on 2007-12-05
Is this thread dead?

Well... trying to revive the subject:

<quote>There is a conversion problem with the Linux driver for some HP models.</quote>

Although I face the same behavior described before in this thread (printer is found, job is sent, printer moves but doesn't print, spoolsv locks, etc...), when I plug the printer directly to my Ubuntu machine (and select the local settings for the printer instead of the remote, of course) it works perfectly.

I really hope to solve this soon, it's been really annoying...

---

### Post by ffchaves on 2007-12-06
Alright, following a post from the Apple PPC Users forum, this is what worked for me:

On the XP box:

control panel>printers & faxes>right click on printer>properties>ports tab>uncheck "enable bidirectional support"

Cheers!

---

### Post by ronmarley1 on 2007-12-06
Here's how I've always done it:
Share the printer on the XP box.
Add the printer on your Ubuntu box as a Samba shared printer using the following syntax:
```
smb://workgroupname/XPboxname/sharedprintername
```
Choose the correct driver.
Print.
The screen cap below is from the new printing tool in Gutsy, but this worked in older versions also.
Hope this helps.

---

