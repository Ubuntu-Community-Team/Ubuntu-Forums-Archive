---
title: "Printer works but wont print text?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-03-12
Hi all 
I have only had obuntu for 3 days now and am getting used to it quite well:confused: 

My problem at the moment is my HP deskjet 980cxi USB printer.
Using a wordprocessor i can print a graphic in colour or greyscale but it wont print out any text unless i use a coloured font?

I thought maybe i was out of black ink but i used my laptop to print text from windows and it worked ok?

Has anyone got any ideas i could try
I've spent ages googling around and reading loads of info but nothing that helps me.


Mike

---

### Post by Scunizi on 2007-03-12
It's possible you might need to use a different driver.  I was just looking at [http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_980C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_980C).  I'm not sure of the difference between the cxi and the c but this writeup mentions possibly using the driver for the 990.

---

### Post by mpooley on 2007-03-13
Thanks scunizi
I just tried that but no luck!
I do hope i'm not going to have to return to windows jus cos my printer wont work:frown: 
this is a weird problem!

thanks 
Mike

---

### Post by Scunizi on 2007-03-13
Here's another shot.  Open your browser and go to [http://localhost:631](http://localhost:631).  That's the web frontend for cups.  Despite what "features" you may have chosen under System/Admin/Printers they may not have changed in cups.  I've found with every printer I've hooked up that the default paper size is A4 and it's only changable directly in cups.  Last ditch for me.  Hope it's fruitfull!

---

### Post by mpooley on 2007-03-13
Thanks:KS 
went through the cups dialogue and it worked!!:) 

Cheers Mate!

---

### Post by mpooley on 2007-03-16
OK I've got over the trauma of getting my printer to work on a usb port  LOL
now i would like to get it working on the network!

It is plugged into my US Robotics router's USB- I have installed in cups using the address specified in my router "http://192.168.2.1:1631/printers/My_Printer"

But i dont get any output at all?

can you help?

thanks 
Mike

---

### Post by Scunizi on 2007-03-16
Sorry.  I'm gonna be watching this one.  Typically you'd have the printer hooked to a machine and share it, but I still haven't been able to get my windows machines to see my Samsung ML-2010.  I gave up until I find more energy to tackle it.

---

### Post by nrwilk on 2008-02-18
Thank you!

I had the exact same problem, and using the CUPS frontend to setup the printer worked for me too.

Just for reference to anyone else who wants to try this, if you've already set the printer up, delete its entry and use the CUPS frontend to redo it from scratch.

Thanks again :)

---

