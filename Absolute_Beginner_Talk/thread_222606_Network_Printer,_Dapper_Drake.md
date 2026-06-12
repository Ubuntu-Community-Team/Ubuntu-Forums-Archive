---
title: "Network Printer, Dapper Drake?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by raene on 2006-07-25
I had a hard time choosing which forum to post this in, whether in the Beginner Talk forum or hardware forum.  I hope this is the right one since I'm pretty much really new to Ubuntu (or linux in general).

I am currently using Dapper Drake, and I want to connect to an IBM Infoprint 21.  

My problem when I go through System --> Administration --> Printing and try to add a printer, is I have no idea what a "URI" is, or where the driver for the printer is (the closest thing that shows up is the IBM Infoprint 12, and when I tried to search for the driver on the website, I think I found a .rpm for Red Hat?  But it didn't work for Ubuntu, so I'm guessing that it's for other linux distros).

I have tried to read websites such as: 
- [http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)
- and [http://occy.net/printing](http://occy.net/printing)
but I cannot for the life of me understand what to do.  When I try to edit the config files, some of those.. values? that the sites tell me to edit aren't even there.  I hope that means that they're using a different version of Ubuntu.

Can someone help please?

---

### Post by ProjectGod on 2006-07-25
when you say network printer... do you mean a printer stuck directly on the network or on a network computer's local printer port that is shared on the network?

---

### Post by raene on 2006-07-25
A printer that's connected through the ethernet, and stuck directly on the network I believe (since there aren't any computers near it really).

---

### Post by ProjectGod on 2006-07-25
this may work... using the same GUI utility... 

try global settings > detect LAN printers. select yes to opening port 631.

---

### Post by raene on 2006-07-25
Didn't work :\

---

### Post by raene on 2006-07-25
By the way, what would I put for the URI?

---

### Post by brentoboy on 2006-07-25
the ip address of the printer

you can get that by pushing the little button next to the ethernet plug on the computer.

(I dont have that exact model, but that is the way my ibm infoprint works)

most network printers have a button that will print off network info.

--
once you know what it's IP address is, we can go the next step and set it up.

---

### Post by raene on 2006-07-25
It says that it's 10.10.11.2, so would I put that, or would I put ipp://10.10.11.2 (as seen from [http://www.ubuntuforums.org/showthread.php?t=30920)?](http://www.ubuntuforums.org/showthread.php?t=30920)?)

---

### Post by brentoboy on 2006-07-25
just give it the ip adress,and let it doctor it up with colins and slashes etc.

and tell it to use the infoprint 12
it is a fairly geneiric infoprint driver, and works from my infoprint 1116

we'll try the one you downloaded before if the driver for the infoprint 12 doesnt cut it

---

### Post by justicerulesok on 2006-07-25
You would put [http://10.10.11.2](http://10.10.11.2) or depending on security on the network http**s**://

Good luck finding the driver if you need a specific one - cant help with that.

I've just set up some printers & I installed Ubuntu last week for the first time as network printers & beleive me thers nothing like the inner glow as you pick up your test page with 'ubuntu' on it from the printer.

Justice.

---

### Post by taurus on 2006-07-25
We have a bunch of HP (and some Dell color) printers on the network and it is real easy to configure it.  You only need to know the static IP address and the model of your printer.  Then, System -> Administration -> Printing -> New Printer -> Network Printer and pick UNIX Printer (LDP) from the drop down menu.  In the Host: field, enter the IP address of that network printer and in the Queue: field, enter lpr.  Click Forward to install a driver for your printer...  Basically, just follow the instruction the on screen now.

---

### Post by raene on 2006-07-25
Okay, currently using Infoprint 12's "pxlmono" driver.

It tells me that the state of the print job is "Printing:job-printing," but nothing's happening with the printer.

---

### Post by raene on 2006-07-25
@ Taurus: UNIX Printer?  I was under the impression I needed to use CUPS

---

### Post by brentoboy on 2006-07-25
> **raene said:**
> Okay, currently using Infoprint 12's "pxlmono" driver.

It tells me that the state of the print job is "Printing:job-printing," but nothing's happening with the printer.

is this the first time you have ever used the printer? is it fresh out of the box?  or is it just new to your ubuntu box?

---

### Post by raene on 2006-07-25
It's just new to Ubuntu, I suppose.  All the other Windows computers here work fine with it.

---

### Post by brentoboy on 2006-07-25
use cups

---

### Post by taurus on 2006-07-25
> **raene said:**
> @ Taurus: UNIX Printer?  I was under the impression I needed to use CUPS
I use lpr (UNIX Printer) for all my network printers (HP LaserJet 4200, Dell ColorJet cn310, and Ricoh printer/copy machine that I can do duplex, staple, and three-hold puncher) and they all work great!  ;)

---

### Post by raene on 2006-07-25
Heh, I just tried the UNIX way - the jobs didn't even show up :(

---

### Post by justicerulesok on 2006-07-25
I installed all my printers as windows printers & they work fine...

---

### Post by brentoboy on 2006-07-25
ok,
I just checked my infoprint settings on one of my pcs, and I used the hpjetdirect driver to get it to work.

hpjetdirect is a protocol for networkable printers, *not* necessarily a way of saying "an hp printer on a network"  It appears that the infoprint printers have an hp network card, or at least a network card with a compatible chipset or protocol.

anyway, try setting it up as an hpjetdirect printer.

---

### Post by raene on 2006-07-25
Hm.  Apparently, one of these methods was right since I have 2 printed Ubuntu test pages now.  Thanks everyone for your help :)

However, I'm not sure which method it was, and it also looks like it takes more than 10 minutes to process the print job?  That's can't be right.

---

### Post by brentoboy on 2006-07-25
you should pick a method that probably works,
make sure that there are no other jobs pending somehow,
and then print the test page. -- and time it.

then, repeat it for the other way of printing.

Maybe one works, and the other doesnt. and the one that didnt work clogged up the pipes.

---

### Post by cantormath on 2006-07-25
I use
System>Administration>Printing

click new printer

choose network printer
change from cups to Windows if its windows


select host
type admin username and password in
Select printer, 

select printer manufacture
then model, or the one closest

Give it a name and description if you want

that should be it.

---

### Post by justicerulesok on 2006-07-25
this is word for word what I did & it works.

---

### Post by brentoboy on 2006-07-25
if it is still slow, after playing around with it, we should setup the drivers from the rpm you downloaded from ibm that is meant for redhat.

They might be better.

---

### Post by raene on 2006-07-25
It works smoothly now :)  Apparently, it was a printer problem that made it slow - too many other jobs from other computers, and not having a sufficient amount of paper even though there was still a bit left.

For anyone who's curious about how I got it working for the IBM Infoprint 21 connected on a network:

1) System --> Administration --> Printing
2) Printer --> Add Printer
3) Network Printer, CUPS
4) URI: IP Address (ex: #.#.#.#    or in my case, 10.10.11.2)
5) Manufacturer: IBM, Model: Infoprint 12, Driver: pxlmono
6) Add description/location if you would like

Thanks to everyone for being so helpful :)

---

### Post by RaBiT on 2006-07-25
> **taurus said:**
> We have a bunch of HP (and some Dell color) printers on the network and it is real easy to configure it.  You only need to know the static IP address and the model of your printer.  Then, System -> Administration -> Printing -> New Printer -> Network Printer and pick UNIX Printer (LDP) from the drop down menu.  In the Host: field, enter the IP address of that network printer and in the Queue: field, enter lpr.  Click Forward to install a driver for your printer...  Basically, just follow the instruction the on screen now.

OK. What about if the printer is using a queue?

I have a Red Hat 7 box working as the print queue. All of the RH9 boxes can print to the pritners. Ubuntu can't.

The problem is it refuses to retain the queue setting whether I go through the CUPS Web interace or just use the System->Administration->Printing Printer box to add the printer. It retains the print server host name but not the queue name.

Thanks.

Bruce

---

