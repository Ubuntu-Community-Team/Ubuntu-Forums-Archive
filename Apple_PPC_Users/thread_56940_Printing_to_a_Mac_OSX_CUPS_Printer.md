---
title: "Printing to a Mac OSX CUPS Printer"
date: 2005-08-14
forum: Apple PPC Users
---

### Post by bozaman on 2005-08-14
Having just spent a substantial portion of my day attempting to get printing set up on my Ubuntu (Hoary) Intel-based laptop in order to print to a Mac OSX (10.4.2) hosted USB printer (Samsung ML-1450), I thought I would share the steps involved for others to have at their disposal...

1. Set-up your printer and verify that it works correctly in Mac OSX.
2. Enable printer sharing in the Mac OSX System Preferences panel.
3. Verify the Mac OSX printer queue name:
    - Open Terminal
    - Type: "view /etc/printcap" (without the quotes), press enter
    - Find your printer in the list (if you only have one printer this should be easy)
    - The value before the "|" is your Mac OSX printer queue name ("ML_1450", for example, is the Mac OSX printer queue name for my situation)
4. Within Ubuntu, go to System, Administration, Printing
5. Go to Printer, Add Printer
6. Printer Type: Network Printer, CUPS Printer (IPP)
7. URI:
    - http://<IP address of Mac OSX>:631/printers/<Mac OSX printer queue name> (If you have set up your /etc/hosts file with a valid IP and host name for your Mac OSX system, then you can substitue the host name for the IP address in the URI)
8. Printer Driver:
    - Manufacturer: Raw
    - Model: Queue
    - Driver: Standard
9. Apply

This should create a new printer for you to access.  Right click, select "Properties" and set the correct Paper and Advanced settings for your situation and then "Print a Test Page".  If all went well, you should have a test print appear in a few minutes.

I relied upon a lot of trial and error, the Ubuntu forums and the [Printer Sharing from OSX](http://members.cox.net/18james/osx_printer_sharing.html) web site supported by Ronald Florence to get this set up and working for my situation.  YMMV, but good luck!

---

### Post by nrwilk on 2005-11-16
Thanks a lot, bozaman!

It's even easier than this in KDE.

---

### Post by jdusablon on 2006-05-07
That was a VERY helpful post! THANK YOU!

It's quite difficult to get any info on how OSX shares printing at all, nevermind a beautiful howto like this!

Now I'm printing like a champion.

---

### Post by Monkus on 2006-09-22
God bless ya!

---

### Post by aysiu on 2006-10-29
Brilliant, easy-to-follow tutorial. It worked flawlessly, and now I can print from my wife's good printer (the printer I have connected to my Ubuntu computer is crappy).

---

### Post by trink on 2006-11-04
Perfect!  I thought I was going to be sunk on this problem, being both a new Mac and new Ubuntu user.  Thanks for taking the time to post this solution. -tr

---

### Post by aysiu on 2006-11-05
Mind if I ask how this works?

I don't need the driver for that printer apparently...? I just use "raw"? How does that work?

---

### Post by wormser on 2007-06-04
Great write up, but I am having issues.  I am trying to print over the internet.  Will this guide still work?  I opened up the port on my router and forwarded it to the Mac with the printer.

1.  working
2.  print sharing turned on and firewall is open
3.  queue name verified
4.  done
5.  done
6.  done
7.  used IP address and domain  :631/printers/DESKJET_930C
8.  done
9.  done

I check the printer status on the Mac and localhost:631 in Firefox and do not see any of the jobs.

Any ideas?  Thanks.

---

### Post by wormser on 2007-06-04
OK, I got it working when I plugged into the local network.  I am going to start a new thread on how to print over the internet since it is a bit different.

Thanks for the guide.

---

