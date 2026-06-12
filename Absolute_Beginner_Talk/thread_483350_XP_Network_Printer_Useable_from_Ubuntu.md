---
title: "XP Network Printer Useable from Ubuntu?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-06-24
The title says it all: I've got an HP PSC 1410 printer sitting on the network, shared through an XP machine.  I can't seem to get Ubuntu to recognize and use it properly.

Here's what I've done.

At the suggestion of UltraMathMan on another thread, I installed Print Services for Unix in Windows by going to Control Panel -> Add/Remove Programs -> Add/Remove Windows Components -> and checking "Other Network File and Print Services".  However, I ended up with the same results as before, which were...

System -> Administration -> Printing, then selecting "Detect LAN Printers" from the Global Settings menu doesn't help.  No printers are detected.  (Not sure if it's even possible for Ubuntu to see a printer through an XP box, but I gave it a try.)

Then I add a New Printer from the icon in the window by the same name.  I select Network Printer, then Windows Printer (SMB).  Then a series of "Authentication Required" windows pop up.  I've tried several different combinations of Username and Password: the Ubuntu machine's name/password, the Ubuntu machine's name and no password, no name and no password, and simply hitting Cancel.  No combination seems to have any effect on the outcome.  (There is no password on the workgroup, printer, or anything of the sort.  Each of the Windows machines does have a user password, but they don't require anything of that sort to talk to each other on the network.)

I select the computer that has the printer connected to it from the Host menu, then enter the Printer's shared name into the Printer box.  I leave Username and Password blank.  Then I hit Forward.

I pick HP from the Manufacturer list, and PSC 1400 from the Model list.  (The 1400 is the closest option to 1410, and also what the XP box's drivers consider the printer to be - it actually says "1400 series".)

The driver box says "hpijs (recommended)".  I'm not sure if I'm supposed to install that driver by clicking the "Install Driver" button, but if I try that it asks for a PPD file and I have no idea what it wants.  So I just hit Cancel and then Forward again.

I leave Description and Location blank and hit Apply.

The printer then appears in the Printers window, labeled PSC-1400 and is designated as "Ready".  If I right-click, select properties, and then hit "Print a Test Page" the printer will wake up and begin making the familiar "I'm getting ready to print something" noises.  However, it will not actually start printing, and instead just flash the power light signifying some kind of error.  To make matters worse, the job sent from the Ubuntu machine "clogs" the queue and will not delete without a restart of the XP machine.


Is there some way to make Ubuntu recognize and accept the printer connected to an XP machine?

---

### Post by JayTee on 2007-06-24
I wouldn't have bothered with setting up Unix printing services on Windows. I print to an HP845C which is setup as a shared printer in Windows. I select Printers in Ubuntu and click on Add New Printer icon and from there I select network printer and in the dropdown box to the right of the Network Printer radio button I select Windows Printer (SMB). Then you enter the hostname of the computer, the name of the printer share and a user name and password of someone who has an account and rights to print on the Windows XP computer. Note: you may not need the user/password if you're using Simple File Sharing on Windows XP Home.

---

### Post by Spektyr on 2007-06-24
Okay, tried putting in the user/password for the XP machine, since I'd already done everything else.

Now it's much, much worse.  When I tried to print a test page it did the same thing before, but now I'm unable to cancel the print job.  When I reboot the printer freezes up again and the job remains stuck in the queue.

---

### Post by Spektyr on 2007-06-24
Any help?

---

### Post by p_quarles on 2007-06-24
Is/was the printer working okay when you sent it jobs from Windows? 

I can't really offer that much help, since the last time a printer did that to me, I gave up and bought a new one (I really think that all printers should come standard with an "erase cache" button). If no one else is able to help you, though, you should try installing the printer directly to your Ubuntu box. The CUPS web interface ([http://localhost:631](http://localhost:631)) is far better than any control panel I've ever used with Windows. Worth a try, at least.

---

### Post by caro on 2007-06-24
I haven't tried using a printer on XP, but I have an Epson printer on a Win2K box.  All I did (from the Win2K machine) is set the printer up as a shared printer.  Then I was able to add the printer on my Ubuntu laptop without anything else.  System > Administration > Printing > New Printer

I do have to enter the username/password for the Win2K machine to access the printer but that's it.  Do you have the drivers for the printer you are using?

---

### Post by Spektyr on 2007-06-24
I finally got the job deleted from the queue, and yes, the printer works perfectly from every Windows machine in the house.

I've got the drivers, but unless I'm mistaken Windows/Mac OS drivers aren't much help for Linux machines.

---

### Post by Seisen on 2007-06-24
Check this out and see if it helps 

[https://help.ubuntu.com/community/WindowsXPPrinter]("https://help.ubuntu.com/community/WindowsXPPrinter")

---

### Post by homergreg on 2007-06-24
I have exactly the same problem with my PSC1110.  I found somewhere mentioned that this is a driver issue that can't be fixed without doing something to the windows print server called "ghostscripting".  It looked a bit complicated for me and I decided print from windows in vmware until I get a wireless print server.  I'll see if I can find a link.

---

### Post by ecs_pf5 on 2007-06-24
I had this problem with my HP PSC 1317

I can't remember what I did to fix it, but it works flawlessly now.

How is that for raising your hopes then leaving you hanging :p

I will try and find the thread.

Here it is [http://ubuntuforums.org/showthread.php?t=472987](http://ubuntuforums.org/showthread.php?t=472987)

I'll scratch my head and think if there was anything else relevant

I was getting that print job showing up on the XP machine as being from 'Guest' & clogging it up too, until I sorted out the workgroup name in samba properly.

---

### Post by Ambidextrous on 2007-06-24
In a word, "Yes".  In fact, it was less trouble to print from 7.04 to a Canon Pixma hosted by a pc running XP SP2 than it was to print to the same printer from Vista Ultimate on my other partition.  It didn't work immediately, though.  'Course, it helps if you give Ubuntu the correct name of the shared printer!

---

### Post by homergreg on 2007-06-24
Here's the thread from broadbandreports with the fix I was talking about.  Maybe ecs's link above is a simpler solution!

[http://www.dslreports.com/forum/remark,17623046?hilite=psc1110]("http://www.dslreports.com/forum/remark,17623046?hilite=psc1110")

---

### Post by Spektyr on 2007-06-24
Yep, as Seisen and ecs_pf5's suggestions advise, it was the disabling of bi-directional support from the XP machine that made things finally work.

So... what the heck is bi-directional support, and what does disabling it do?

---

### Post by homergreg on 2007-06-25
Awesome!  It worked for me too!  Much better than the workaround that I had found but not used.  Thanks!

---

### Post by Spektyr on 2007-06-25
Great, I'm glad it helped more than just me.

So does anyone know the answer to my earlier question?  The bi-directional support thing I turned off... what does it do?

---

### Post by ecs_pf5 on 2007-06-25
The best info I can find on a brief search is that bidirectional communications are only made use of, when a printer is directly connected to a computer. What it appears to do, is let the printer talk back to the computer to actively indicate it's current status.

On a network setup, the bidirectional feature is not relevant since the printer is not directly connected to the computer. The sending computer only needs to send info one way i.e., send the document off to the printer. Once done, the sending computer is not supposed to care anymore - it leaves the job of actually controlling the print job, to whatever is at the other end, be it a dedicated network printer, a print server PC, whatever.

Only the PC that is actually directly connected via some kind of off-network serial link (usb, parrallel cable, etc) to the printer, can properly utilise the 2-way bidirectional comms.

Well at least that's as I understand it, sorry not to be able to give more depth. But hey, it works ;) good one

On second thoughts, that doesn't make sense, does it? Because you DISabled bidirectional on the printer SERVER... oh, I just don't get it sometimes.. ho hum

---

### Post by maulteez on 2007-06-27
Want to clear the queue on your XP machine without rebooting? Here's how:
On the XP machine, do ctrl-alt-del to access the task mgr. Find spoolsv.exe and end the process.
Close the task mgr and open Windows file explorer. Go to c:>Windows>system32>spool>
PRINTERS and delete the file that is there. Close the file explorer and open a command prompt.
(Programs>accessories>command prompt) and enter spoolsv and hit enter and that restarts
the print spooler. You have to stop and restart the spooler because the queued file can't be
deleted with the spooler running. This sounds a little drawn out but it is a lot quicker than having
to reboot the machine.   :)

---

### Post by ecs_pf5 on 2007-06-28
Good one maulteez, because even rebooting didn't clear the remote downlevel document when I had the problem. It was a real pig to get rid of.

---

