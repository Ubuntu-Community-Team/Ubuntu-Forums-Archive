---
title: "Install printer"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-07
I just got ubuntu installed on my hard drive.  I am totally new at this.  Now how do I get it to recognize the printer.  I have an HP 5150.

---

### Post by tc101 on 2007-01-07
I found out how to install a printer here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_a_printer](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_a_printer)

There is lots of useful info in general in this wiki

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by meng on 2007-01-07
tc101: did you solve the problem yet? If not, how is your printer connected - by USB, parallel, network or other?

---

### Post by Head of Stone on 2007-01-07
I have  a simliar problem i will not reconize a printer attached to a window network via a router. 
Printer:Brother MFC-7820N

It see the network but not the printer. Solutions

---

### Post by L Campbell on 2007-01-07
> **tc101 said:**
> I just got ubuntu installed on my hard drive.  I am totally new at this.  Now how do I get it to recognize the printer.  I have an HP 5150.

This is what I did:-

You click on System (top of the screen, left side), then Administration then Printing then double click New Printer.

The Add a Printer opens and you don't see your printer shown, so you click Forward.

Another window opens, 'Step 2 of 3: Printer Driver'.

You now see:-

Manufacturer:

Model:

Driver:

Are you still with me?     :-)

OK, you click the down arrow of the Manufacturer line and click on YOUR BRAND OF PRINTER

Now you look at the Model section and scroll down to find your model number.

Click on your choice of model an you should then get information in the Driver box.

You may need to re-boot after this step.

Now, when you click on 'File' - 'print', you should be able to see your printer.

Hope this helps.

---

### Post by Head of Stone on 2007-01-07
Thanks for the help but it seems that it is not listed in the list of brother printer. Alos this printer is attached to a windows network. Any more help

---

### Post by halitech on 2007-01-07
Head of Stone,

check here for info on getting Linux drivers for your Multifunction device.

[http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html")

According to here: [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

it looks like they have developed a driver for Debian which should get you working.

---

### Post by Head of Stone on 2007-01-07
> **halitech said:**
> Head of Stone,

check here for info on getting Linux drivers for your Multifunction device.

[http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html")

According to here: [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

it looks like they have developed a driver for Debian which should get you working.

What if i am using edgy?

---

### Post by halitech on 2007-01-07
it "should" still work. Ubuntu is based on Debian so any deb file that works in Debian should, in theory, work in any version of Ubuntu. 

now, if it does blow your system up, blame Brother for not testing their drivers, not me ;)

---

