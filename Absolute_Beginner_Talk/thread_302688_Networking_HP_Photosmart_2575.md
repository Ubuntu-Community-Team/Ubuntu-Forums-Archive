---
title: "Networking HP Photosmart 2575"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Larry Roll on 2006-11-19
[FONT="Arial"][SIZE="4"][/SIZE][/FONT]****

I am brand new to Ubuntu and Linux.  I DO NOT UNDERSTAND HOW TO EXECUTE COMMANDS ON THE TERMINAL.  Please understand that.  I want to get my HP Photosmart 2575 all-in-one printer/scanner/copier working.  What do I do?  I need the step-by-step instructions, totally stripped of geek-speek and with the training wheels locked ON.  Absolutely no presumption of any competence on my part should be assumed.  

I am running Ubunto 6.06 on a Dell Dimension E521 with the AMD64 processor.  My network is with another Dell, a Dimension 8400 running Windows XP Home and linked to the internet with a Linksys router connected to a DSL modem. Can anyone help?  

I'd prefer E-mail communications to [email]yodoc@aol.com[/email]

Thanks for your help!

---

### Post by cilynx on 2006-11-20
Here goes...

The 2575 is Officially Supported on Linux by HP.  

On the toolbar on the top of your desktop...
Click System->Administration->Printing
This will open the printer admin dialog
You should have only the "New Printer" icon
Double click on the "New Printer" icon
This will first "read the printer database", then open up the "Add a Printer" dialog
It should say really big across the top "Step 1 of 3: Printer Connection"
Printer Type should be set to Local
[from here on, I'm flying from memory...the 2575 is on a client's machine that I don't have easy access to]
You want to use the detected printer
The name of the printer in the box could be cryptic / geeky, but it should say HP 2575 somewhere in there.  If it's the only printer connected, there should only be one option anyway.  (As an aside, you could use the printer on the HP port as well as it's the same thing, but I like the other way better.)
Highlight the name of the printer in the "detected printer" box
If there are no options in the box, then something is wrong with either your physical connection or your base system as the drivers are included out-of-the-box.
Click "Forward"
You should now be on "Step 2 of 3: Printer Driver"
Select "HP" for the Manufacturer
Select "PhotoSmart 2570" as the Model (257x all use the same driver)
Select "hpijs (recommended) - HPLIP 1.6.9" as your driver (version number not really important, just put it there cause mine had it)
Click "Forward"
You should now be on "Step 3 of 3: Printer Information"
You can just hit "Apply" here to finish.  All information is optional.
"Name" is whatever you want to see when you click "print" in an app and it shows you the printer.
"Description" is where I usually put the extended model information so that I don't have to go look it up later
"Location" is generally a room number or some such if you admin a bunch of machines

Good Luck

---

