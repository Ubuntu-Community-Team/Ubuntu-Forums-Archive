---
title: "Samsung network printer &quot;job stopped&quot;"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Touque on 2006-07-26
Ubuntu 6.06
CUPS 1.2.1
Samsung CLP-600N
Latest unified driver downloaded from Samsung

I'm hoping someone will be kind enough to help me with this problem. My Samsung CLP-600N is a network printer and works fine with a Mac computer via the network but when I try to print from Ubuntu using the printers ip (ipp://192.168.2.110) nothing prints. Checking the printer properties lists the print state as Stopped:job-stopped.
The problem appears to be with Ubuntu, but I've run out of ideas. I'm stuck, any ideas anyone please?

---

### Post by Chaos_Spawnn on 2006-10-20
I too am running in to this issue but with a samsung 2152W. The print job status is "Pending:Printer-stopped" when using a CUPS ipp setup.

---

### Post by Tulip on 2006-10-29
Exact same printer, CLP-600N, exact same problem - printer seems to install okay, clicking on print makes the printer warm up for a second and then the print job pauses. I have also downloaded the latest unified driver from Samsung, and followed the steps outlined in
[http://www.ubuntuforums.org/showthread.php?t=65111&highlight=samsung+printer](http://www.ubuntuforums.org/showthread.php?t=65111&highlight=samsung+printer)
including shadowing cups and restarting it.
I have installed the printer manually through system>admin>printers, using the cups printer option and the correct address. I really hate printing from Ubuntu - I've also struggled unsuccessfully with an ML-6060. Why the hell did I get another Samsung?
](*,)

---

### Post by Tulip on 2006-11-01
Any ideas on this please? The printer is definitely set up correctly - I can print to it with a Windows machine no problem, and I can access the printer's web configuration page with the Ubuntu machine no problem either. The Samsung Unified Driver configurator is installed as well, and it can see the printer too but it just wont print. It just seems so damn close to working... Argghhh!

---

### Post by Touque on 2006-11-13
I changed the printer address type from ipp to lpd and all worked as it should.
As simple as that. 

:) 




"The more complicated they make the plumbing, the easier to stop up the drain" 
"Scotty" Chief Engineer, USS Enterprise.

---

### Post by Tulip on 2006-11-20
Care to share with this Ubuntu incompetent exactly how you did that please? I've made a few attempts without any success. Editing using the Samsung Unified Driver COnfigurator had no effect - couldn't save any changes.

I tried System>Admin>Printing, and deleted what was there to start fresh. New Printer, selected Network printer, and picked Unix Printer (LPD) from the drop down box. 

Now I get shaky. Added my printers IP address and the port number 192.168.0.9:515 to the host line. Does the port need to be specified, and is that how you do it? I've checked the printer config page and LPR/LPD Protocol is enabled and 515 is the specified port. Is anything added to the queue line?

Clicking next and I select the Samsung CLP-600 Series (SPL-C) Driver. It recommends Standard (Cups). Is this the correct one? Ive browsed through the Samsung directory that was created when I installed the unified driver and couldn't find anything obvious that might be a better match.

Applying this adds the printer successfully, but it's paused. Resume the printer, print a test page, and... nothing. The printer no longer does the 'job stopped' message and it says theres a job in the queue but it makes no more progress than that. The printer sits quietly in the corner, not a peep - I should go do something similar before I break something. ](*,)

---

### Post by Touque on 2006-11-24
Hi Tulip,

I make no bones, I am very much a novice as well. There may well be a simpler or  proper / better way of fixing the problem. If anyone knows better then I'd be pleased to hear from them and learn.

I have just noticed you are using 6.10. When I found that simply changing the protocol to LPD got it working I was using 6.06. I'm sorry for this error on my part.

I just installed 6.10 and sure enough the unified driver configurator failed to install the printer.
Trying to install the printer from the "Add Printer" in "Printers" also failed because I couldn't find the clr-600 in the list of known printers.
I decided to manually add the appropriate .ppd file to the list and then re-attempt the install.
I did and it worked. Also upon re-booting the printer now appeared in the Samsung Unified Driver Configurator on the desktop.

The printer now works and as far as I am concerned that's all that matters.

May I suggest you do the following,

Try to install the unified driver configurator file from Samsung from a terminal. It will fail but it seems to do a partial install.
I copied the CLP-600splc.ppd file from the Samsung driver file using the following path;

/cdroot/Linux/noarch/at_opt/share/ppd/CLP-600splc.ppd

and copied it to /usr/share/cups/model

then from the Desktop I selected System, Administration, Printing, New Printer

I selected Network Printer (cups printer) and allowed it to search the network. In my case the printer was detected at 192.168.2.110  (Note, I did not enter a port number.)
From the list I selected, SAMSUNG for the printer make then from the list, CLP-600splc for the model.
I finished the install and re-started the computer.
All that I needed to do was correct the paper size to letter size and that was it.

---

