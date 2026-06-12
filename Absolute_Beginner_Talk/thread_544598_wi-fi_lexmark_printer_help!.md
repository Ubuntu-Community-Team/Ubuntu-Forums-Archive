---
title: "wi-fi lexmark printer help!"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-09-06
I have just got hold of one of these new lexmark x4550 all in one printer, scanner things. Its supposed to have wi-fi printing but so far, im a little bit stuck as to how im supposed to get it to work.

According to the printer's diag sheet (printer can be found here by the way [http://www.lexmark.com/uncomplicate/...370_en,00.html](http://www.lexmark.com/uncomplicate/...370_en,00.html))
it cant find a wireless network. I have a Fujitsu Siement Amilo PA1510 with wireless and as far as I am aware there are no issues with it as it connects to my broadband livebox via wi-fi. I'm really not sure where to start. The instructions are for windows only so no help there, though it does suggest that even in windows, you have to 'ping' the printer. Does anyone have any ideas? Anything would be appreciated as I said, I really dont quite know where to start!

Having done a quick search seems there is only one thread concerning this printer and it was a general 'any ideas' thread - if ive missed something please let me know...

---

### Post by dwhitney67 on 2007-09-06
If your printer can connect to your WiFi router, then more than likely there "must" be a way for you to examine the IP address assigned to the printer.  Perhaps the printer has an LCD display or perhaps you can look at the status via your router.

Once you know the IP address, then you should be able to ping it with a command like this:

[FONT="Courier New"]$ ping <IP address>[/FONT]

If you are successful with this, then I would recommend that you add that IP address to your */etc/hosts* file so that you can designate an alias (i.e. a name) for it, thus obviating the need to remember the IP address for other purposes.  So,

[FONT="Courier New"]$ gksudo gedit /etc/hosts[/FONT]

Then add an entry like:

*<IP address>  LexmarkPrinter*

Anyhow, once you have the IP address you can set up your system with a networked printer.  Goto **System -> Administration -> Printing** where you can create a new printer handler.

Now whether a printer driver is available for your Lexmark is the $1,000,000 question.  Linux and Lexmark is synonymous with Oil and Water from what I have read elsewhere... they don't mix.

---

### Post by dwhitney67 on 2007-09-06
Btw, if there is no way to interface with the printer (to connect to your WiFi equipment), then that is probably why the instructions require you to use Windoze to run some app that will allow you to configure the printer settings.  Heed that advice if you are stuck otherwise.  No doubt Lexmark will not provide support for Linux.

---

### Post by MikeSz on 2007-09-07
Many thanks for the help - il give that a go.

As a side point however, I have tried the USB connection for it (abandoned the idea of wi-fi for the present in favour of establishing whether the thing works or not in the first instance) and it would seem that there isnt a specific x4550 driver. Alas, the two nearest drivers dont work so I cant even get it working via USB :(

---

### Post by dwhitney67 on 2007-09-07
See if it is possible to return the printer to the vendor; perhaps you can exchange it for a Linux-friendly printer (e.g. HP) with similar capabilities.

---

### Post by MikeSz on 2007-11-07
Kept the printer as I like it and it works ok on my other Windows machine.  I just installed things like open office etc on that box and put my files on a memory stick but it would be nice to use the wi-fi capability within my Ubuntu laptop.  

found this link on the Lexmark Website - [http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html)

Has anyone had a play with this to get their printer working?  I had a bit of a go but it quickly got beyond my capabilities!

---

### Post by MikeSz on 2007-11-19
Bump....

anyone had a go at this? I like the printer and it works on my windows machine so didnt want to take it back - has anyone managed to get a driver working yet? Mine is an all in one 4550 and just will not work in Ubuntu 

On the point of the IP address - I think I managed to find that ok from printing the status of the printer through the menu - the printer also shows as a "print server" in the wifi bit - if that helps at all?  (dont exactly know what to do with it from there though...)

---

