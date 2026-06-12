---
title: "Printing very faintly"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by enpey on 2007-02-27
Hello all,

I have spent a few hours today trying to enable printing from Ubuntu 6.10 to a HP DeskJet 948c printer connected via USB to Windows XP system. It sits on a static IP address.

I am able to print to the printer, but it prints very very faintly, closer to non-existant. A print test page works, except the colours tone range goes blank in the box to the right of the 90% colour (assumingly, the 100% box), but I am not sure if this is just the norm, or if it has something to do with my problem - as printing text docs would use 100% black (again, assuming).

I have downloaded hpijs-2.1.4 and extracted just the DeskJet 948c ppd file and "Install[ed] Driver" through the printer properties (**System -> Administration -> Printing**). If I try to install that again it says driver already installed (as I'm using the same file again..just seeing if it did anything different).

Any help would be much appreciated,

Thanks, Nathan

---

### Post by carlosfocker on 2007-02-27
Did you have this working with windows (Assuming you had windows installed).  Its really sounds like a ink cartridge problem.  If you still have windows install some where I would test it. If it does the same then replace the ink cartridge.

---

### Post by enpey on 2007-02-28
Sorry, I had mentioned that when I first tried to post but I had an unexpected error and it all disappeared.

I printed from the XP machine that the printer is connected to and it worked fine. I have printed from another XP machine on the network and it printed fine...thus I don't believe it is the cartridge..

---

### Post by steven8 on 2007-02-28
> **enpey said:**
> Sorry, I had mentioned that when I first tried to post but I had an unexpected error and it all disappeared.

I printed from the XP machine that the printer is connected to and it worked fine. I have printed from another XP machine on the network and it printed fine...thus I don't believe it is the cartridge..

This may sound silly, but make sure it isn't set up for draft printing.

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_948C]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_948C")

This page of info at the linux foundation says you've done everything right.  :confused:

---

### Post by enpey on 2007-02-28
In the printers advanced tab, the resolution was set by printout mode and quality was normal.. Tried changing these options but had no effect. Still non-existent printing...
Have tried printing through OpenOffice and gedit...

---

### Post by steven8 on 2007-02-28
Go to system>administration>printing.  I am not at home on my Linux box, so I'm not sure, but on this dialog you will find the output choices such as draft, etc.  That is where the printout mode is set.

---

### Post by enpey on 2007-02-28
Yes that is what I have changed, and what has always been set on normal. But to no avail...

Ok, I have just sent a test page via **System -> Administration -> Printing**, selecting the 948c and clicking **Print a Test Page** at the bottom of the General tab. It prints out fine, except the top and bottom lines (the greyscaled ones) stop at 90%, ie they do not have a full black square. I am not sure if this is meant to be there or not, but all the colour ranges work perfectly. The lines running around the border of the page are cut off at the bottom (ie they dont run horizontally along the bottom of the page).

---

### Post by steven8 on 2007-02-28
Oh wow.  So the page, although not complete, printed in the right colors and blacks, etc?  yet it prints badly from programs?  Hmm.

I have had test pages not complete, then sent another and it printed okay.  I have never had a page from a program not print completely, so I'd not worry about that.

I'll have to do some hunting to see why the test page is okay, but not from programs. :-/

---

### Post by enpey on 2007-02-28
Ok, thanks Steven. Fingers crossed..

Edit: Yes, there are six colours that have come out from 0% (no colour) to 100%.

---

### Post by steven8 on 2007-02-28
Dagnabbit!  Everything I find just tells me your printer should be working just fine.  I'll keep hunting and let you know.

[edit]I did just find a thread that refered your printer as finicky and temperamental under Dapper :([/edit]

---

### Post by enpey on 2007-02-28
Well..I don't think its too temperamental in  my case, just consistently doing the same wrong thing :(
At least with temperamental I might get a page or two out every now and then haha

---

### Post by steven8 on 2007-02-28
I am going to suggest that you try changing the driver to hplip.  According to the hplip site it says your printer is support by their driver version .95 and up.  Give that a try and see what happens.

---

### Post by enpey on 2007-03-01
Alright, installing HPLIP 1.7.2 using the self extracting archive with installer, on automatic as it says Ubuntu 6.10 is supported. 

I get to the HP Device Manager - Printer Setup Wizard, Choose Connection type where I choose Network/Ethernet/Wireless (direct  connection or JetDirect), then hit Next.
No Devices Found.
I have tried searching manually with an option there using the Windows computer name, although I am not sure what to use -

The computer's IP add is 10.1.1.3, the printer is connected on USB001, printer shared name is 948Printer, and computer (windows name) is PODLICH. Computer here referring to the one connected to the printer.

I only really have the option to hit cancel now, and I'm not sure if HPLIP has finished installing...

---

### Post by steven8 on 2007-03-01
I've never worked with a network printer at home.  What happened after this?

---

### Post by enpey on 2007-03-02
Ok, well I have HPLIP installed, it just doesn't have any printers added to it. I haven't had the time to play around with it today (work starts at 6:30am and just got home at 9:45pm). But will have a go at it maybe tomorrow night (work again tomorrow) and I'll post any problems or hopefully that I have figured it out.

Thanks, Nathan

---

### Post by steven8 on 2007-03-02
Best of luck, my friend.  It's 6 o'clock here and I go off shift at 7.  As I say, keep us posted!

---

### Post by enpey on 2007-03-05
Ok, well I go into the HP Device Manager through **Applications -> Accessories** and it comes up with 'No Installed HP Devices Found.' Gives me a list of ways to install a device, so I choose CUPS web interface, where I already have the HP printer installed on the printer list, and I am able to print a test page perfectly from there (a different test page to the one I was printing previously), with black and white tones and colour.

  	

Search in Printers: Clear

Showing 1 of 1 printer.
  	Sort Descending 	 
DeskJet-948C
	Description: HP DeskJet948C
Location: 10.1.1.3
Make and Model: HP DeskJet 948C Foomatic/hpijs (recommended)
Printer State: idle, accepting jobs, published.
Device URI: smb://10.1.1.3/Boss:@10.1.1.3/948Printer

Boss is the username of the computer it is usually connected to, but tonight someone tried turning that comp on and the keyboard has packed it in and so they just moved the printer to a diff comp. [I haven't tried installing it on that comp from here (it is in my little brothers room and he's now asleep)]. It still tells me that the printer is ready to go... so I'm assuming some error there.

Still not sure what's going on..

---

### Post by steven8 on 2007-03-06
I had 'No HP Devices Found' until I installed the newest hplip, but my printer is a different model.  I read a thing that said you shouldn't have both hplip and hpijs installed at the same time, because they will conflict with each other, so be careful.

---

### Post by enpey on 2007-03-07
How would I go about uninstalling hpijs? sudo aptiude remove hpijs ? I did that, and opened HP Device Manager but still showed nothing, couldn't find anything on the network nor would the CUPS device show up..

---

### Post by steven8 on 2007-03-07
When you go to System>Adminstration>Printing and choose Add Printer, does it see your printer?  If it does, set it up as a network printer, then choose hplip as the driver, even if it says hpij as recommended.  See if that works.

---

### Post by enpey on 2007-03-09
Well that's basically how I did it initially. And so the printer is there, and it is in my CUPS localhost list of printers when i access that site.. 
And I can print test pages from there both the CUPS site and from the System->Admin->Printing HP DeskJet 948c menu..

---

### Post by steven8 on 2007-03-09
So, were you able to do it now and assign the new driver?

---

### Post by enpey on 2007-03-09
In my CUPS Model/Driver for DeskJet 948c menu, there is a choice for: 
- CUPS Gutenprint v5.00 (en)
- Foomatic/hpijs (recommended) (en)
- Foomatic/hpijs (recommended) (en)

There are two entries for the Foomatic/hpijs driver. No option for HPLIP. I don't see HPLIP as an option for anything actually. HPLIP is not a .ppd file, so I'm guessing that is why I cannot install that as the driver...

---

