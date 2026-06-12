---
title: "installing TCP/IP printer"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by kdeanmitchell on 2008-03-14
I've looked at all the other forum topics on this an haven't found an answer yet so I'm posting this question for one of you smart guys/gals to help with.  

I have a printer - managed by the university that I need to connect to.  It's a brother 1470n I've already got the ppd driver as mentioned by several forum discussions.  But I can't connect to it.  

in windows I'll choose local printer - tcp/ip - and then give the ip address.  

How do I do this in ubuntu?  I've tried CUPS option, LPD option, and all the other options under network printer to no avail.  I've also tried local printer to see if it gave me the tcp/ip option like windows but the only option there is generic PDF.  I'll include some screenshots.  

I've even tried naming it 'lpt1' some forums said this might help.  

Thanks in advance for all your help.

---

### Post by taurus on 2008-03-14
If it has it own IP address, try System -> Administration -> Printing -> New Printer.  And in Devices, scroll down to the end and pick LPD/LPR Host or Printer and put in the IP address of your printer in Hostname.  You can call it whatever you want in the Printername field.  Then, continue and follow the instructions on the screen.

---

### Post by Kenny_F on 2008-03-14
I also have similar problem. I have a Canon IP5200 connected via ethernet to my router - so it will have an IP address. Tried most of the options in Add Printer but will try suggestions from Taurus.

PS. What happens if the router assigns a new IP address to the printer for any reason?

---

### Post by smurphy_it on 2008-03-14
I'll go through the steps of cups.

Open a web browser and goto [http://localhost:631]("http://localhost:631")

Then goto the Administration tab, and choose Add Printer.

Give it a name, location and optionally a comment, goto the next page.
Under device choose AppSocket/HP Jetdirect

In the field type in socket://172.24.34.164

Change the IP address to whatever your printer's Ip address is.

Kenny_F:  You should either give your Printer and IP reservation, or give it a static IP address so that the printer's IP address doesn't change.

If your printer has a network jack built in, then you can try the following couple of suggestions for setting the IP to be static.

#1 - Change it within the printer (if possible)
#2 - Open up a web browser and goto the IP of the printer (ex.  [http://172.24.34.164](http://172.24.34.164))

Lastly, use the router to give it an IP reservation (or Static IP depending on firmware).

---

### Post by kdeanmitchell on 2008-03-14
Taurus - Tried again - as you suggested with just typing the ip address - same results - it acts like it adds it but all test pages fail.

---

### Post by kdeanmitchell on 2008-03-14
smurphy_it - tried again using your directions for the CUPS.  Still not working :(  Any other thoughts?

Including another screen shot.  

Also - my printer does have a static IP assigned by the network administrator of our department at the university.  It never changes.

---

### Post by mebu99 on 2008-03-14
I have used KDE Control Module for the printer and have lots of luck.  You can get it through the Add/Remove tools.  The module is under Other called 'Default Printer'

---

### Post by kdeanmitchell on 2008-03-20
Thanks for the KDE tip.  

I ended up installing the whole KDE-desktop and was able to get the KDE printer utility to work.  It has a much nicer wizard that actually lets you choose TCP/IP as an option.  It was a breeze.  

Now I just have to figure out how to get rid of all the extra GNOME baggage I'm carrying around

---

