---
title: "HP Printer on network via usb to router"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-03-10
Hi all  
I am a new convert to Linux so know almost nothing at all.
I am Using Obuntu edgy BTW
I want desperately to dump windows but i need to get my hardware working before i can.


So I tried installing my DJ980c by downloading a file from HP and using the command line to install it. I got an error and it wouldnt work.  

This was before i realised that ubuntu had a graphical interface to install my printer and the driver as well!! which was a pleasant surprise. 
So I installed as a network Printer with the address as [http://192.168.2.1:1631/printers/My_Printer](http://192.168.2.1:1631/printers/My_Printer) (Which is the address that my US Robotics router tells me is correct)
and tried a test page and nothing happened? 
My printer is plugged in to my network router via usb BTW

I have also tried installing it as a local printer - plugging directly in to my desktop - this recognises the printer and installs perfectly except it still wont print anything??

This all works ok in Windows XP btw

help me to dump windows please 

Mike

---

### Post by localuser on 2007-03-11
Hi Mike, welcome to Linux and Ubuntu.

It will be best for you to try to get things to work by direct connection first, as you've done, so these questions relate to the non-network connection.

How are you connecting the printer to your system (usb?)

If usb, then is this the same usb port that worked in Windows?

What are all the things listed in your Printers window (System | Administration | Printing)

If you right-click on the printer in the Printers window, and view the Connection tab of the Properties, what do you have for printer type?

---

### Post by mpooley on 2007-03-11
Thanks

 I have since got the Local printer working by well i don't know how LOL
But Now it wont print text unless i use a colour for the font:confused: :confused: 
it will print a graphic (i used open office wordprocessor) and i have also printed the graphic in greyscale but if the text is black it doesnt print?

I thought maybe i was out of black ink but i used my laptop to print text from windows and it worked ok?

> **localuser said:**
> Hi Mike, welcome to Linux and Ubuntu.

It will be best for you to try to get things to work by direct connection first, as you've done, so these questions relate to the non-network connection.

How are you connecting the printer to your system (usb?)


Yes
> **localuser said:**
> 

If usb, then is this the same usb port that worked in Windows?


Yes
> **localuser said:**
> 

What are all the things listed in your Printers window (System | Administration | Printing)

New Printer
Deskjet 980c ready
Network Printer ready


> **localuser said:**
> 

If you right-click on the printer in the Printers window, and view the Connection tab of the Properties, what do you have for printer type?

Local Printer

Thanks again I do need help:KS

---

### Post by localuser on 2007-03-12
<edit>I forgot to mention that if you only have a single printer, then you should remove the Network Printer that you say is present in your Printers window.</edit>

Well, perhaps tackling this with one problem at a time would be of help.

Now that you have the printer semi-working locally, perhaps you can move it to the network and try to add it as a network printer.

System | Administration | Printing
Printer | Add Printer
Network Printer | HP JetDirect (In dropdown list)

From what you've written previously in this thread, try this for an address:
192.168.2.1

---

### Post by doncristobal on 2007-07-08
Maybe this can help: [http://ubuntuforums.org/showthread.php?t=369972](http://ubuntuforums.org/showthread.php?t=369972)
it's how i solved a very similar problem with my siemens router and hp printer

Good luck!

---

