---
title: "Is Linux for me?  I hope so!  Advice on filesharing and printing"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by th3dude on 2007-04-02
I currently run a small business printing booklets and manuals.  We have around a dozen PCs, all relatively recent (Athlon 64, Pentium D and Core Duo etc).  We have one machine as a dedicated file server, simply sharing several folders on the network (works great) and use the individual machines for DTP and printing.  We use Windows XP Pro on all machines.

Question 1
Can I use Ubuntu to replace the file server on our network?  Is it hard to do and what benefits would I find, if any?

Question 2
We use PDF files exclusively and need to be able to print 2 up, sometimes in booklet format etc.  We currently use fineprint in Windows to do this.  How can thus be done in Ubunutu?  I need to use a gui based system for this as I'm not the only one printing.

Ultimately we want to move from Windows 100%, for now though Linux taking over file and printer work would be a step closer.


Thanks in advance and I hope we can start the move soon.

---

### Post by nixclusive on 2007-04-02
Yeah sure you can use linux as a file/print server. Actually its a lot more robust solution for your needs!! You might wanna check out the live cd and try out the system before you make any significant decisions. Good luck.

---

### Post by th3dude on 2007-04-02
I've installed it on a seperate partition to experiment with.  So far I have file shares set up which I am now testing.  Not sure how to go about the print side though.  Does Ubuntu do this with CUPS or something?  Is there another tool/program I might need to print two up, booklets etc?

---

### Post by arbulus on 2007-04-02
Ubuntu does use CUPS to serve printers.  
Here's a link to a good CUPS how to:  

[https://help.ubuntu.com/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/ubuntu/serverguide/C/cups.html)

Once you get everything set to go, then you'll go to your favorite web browser and go to:

[http://localhost:631](http://localhost:631)

and that will get you the CUPS administration tool.  From here you can set up your printers.  I'm not familiar with the process of sharing with Windows computers, but hopefully this is a good start for you.

---

### Post by Liam1964 on 2007-04-02
I also work in the Printing industry. I work in a Tech support role. I have very little experience of Ubuntu, but having seen a customer I recently visited to set up a new plate making system for them, using it on all but one of their computers ... well this got me hooked. I have been playing with it ever since. It certainly works better with Postscript and PDF formats than windows ever will. I am about to start reviewing all the RIPs that can run on Linux ... is it a RIP that you are looking for, or just a positioning software?

---

### Post by th3dude on 2007-04-03
I literally need to send print jobs to a selection of laserjet printers.  All my source files are PDF format and I need to be able to print some of them two up (two per A4 sheet), the rest need to be made into booklets.

Right now I use this:

Fineprint
[http://www.fineprint.com/products/fineprint/benefits.html](http://www.fineprint.com/products/fineprint/benefits.html)

I need to match this functionality as much as possible and it must be with a friendly GUI based interface as it's not just me using it.

Will cups do this?

thanks

---

### Post by thefoolisme on 2007-04-03
The one thing you do need to check is for drivers for your printers.  I have a Canon Laser, and there's no driver for it, so I can't use it in Ubuntu.  Since you're in the printing industry, that would probably be one of the first things I'd check.

---

### Post by th3dude on 2007-04-04
I use laserjet 4050 printers, they are about as standard as you can get.  I've already got printing working, what I need is the booklet and 2 up fixed.

---

### Post by compmodder26 on 2007-04-04
It would appear that your printer has driver that works perfectly: [http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4050](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4050)

---

