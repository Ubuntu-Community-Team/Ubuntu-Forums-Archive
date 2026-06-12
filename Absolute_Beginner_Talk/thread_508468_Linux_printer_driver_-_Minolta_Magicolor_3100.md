---
title: "Linux printer driver - Minolta Magicolor 3100"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-07-24
Hi

I am trying to get this printer to work using Fiesty 7.04. I have managed to get a connection using a shared service from a windows pc. (It means the windows pc must be on in order to print from Ubuntu)

How can I print direct from Ubuntu?

Kind regards
Bob

---

### Post by expatCM on 2007-07-24
looks like the printer is more or less supported
[http://openprinting.org/show_printer.cgi?recnum=Minolta-magicolor_3100](http://openprinting.org/show_printer.cgi?recnum=Minolta-magicolor_3100)

Have you added it as a printer to your system?   Are you going to connect it directly to your system or do you wish to print when it is still connected to the Windows box?  Not sure what is default settings options since my system gets changed a lot but if you look at System / Administration / Printing, can you identify the printer as a network device if you use the Windows PC IP as the location?

If it helps at all ...
[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)

---

### Post by bwallum on 2007-07-24
Hi, thanks for the response.

I downloaded the driver only to be told it was already installed! If seems to come as default with the printer wizard (system>admin>printing>new printer....). Absolutely terrific this Ubuntu stuff!

I think my understanding may be adrift though. The printer needs a print server I think (in my case it is the Windows pc) so I need to find out how to set the printer to be a LAN printer without a server, if that is possible. I may try to set it up as a local printer and see if that works.

Thanks again for the reply.

Kind Regards
Bob

---

### Post by steve.horsley on 2007-07-24
You should be able to just connect it by USB, turn it on, and in the Add Printer dialog you should see it in the Detect Connected Printers box.

The Ethernet connection claimse to support IPP amongst other protocols, and Linux supports IPP, you just need to know the URL to type in. If you're lucky, enabling Detect LAN Printers in the Global Settings will make it appear in the list box.

---

### Post by bwallum on 2007-07-25
Hi Steve

Thanks for the advice. I have the printer connected to a LAN via a hub. I know it's url. I have tried to connect to it using the IPP route but no luck. I have 'joined' the Windows workgroup (MSs quick way of setting up a network domain) and can see other comptuers on the LAN but I can't see the printer.

What is CUPS? Is it some sort of print server software?

Rgds, Bob

---

### Post by steve.horsley on 2007-07-29
Sorry, I've been away.

Cups is Common Unix Printing System it I remember right. It encompasses the spooler softare and the LAN protocols for shared printing.

If your orinter is on the LAN, then you should knoe the IP address and should be able to ping it. In this case, you don't need to connect to the windows domain, you shlould be able to talk directly to the printer.

I don't really know what to do from there, I'm afraid. If it were me, I would fire up the Wireshark protocol analyser and see what's happening on the LAN, but that's only a help if you're familiar with LAN protocols and analysers.

---

### Post by bwallum on 2007-07-30
ping works, all less than a millisecond, but the printer is not auto detected by Ubuntu.

I think the problem lies in that there is no print server. I don't know if Ubuntu has a built in one, hence the question re CUPS.

Thanks for your help anyway, it was worth a try.

Regards
Bob

---

### Post by steve.horsley on 2007-07-30
It would be interesting to find out if you can connet to TCP port 631 (the IPP service port) on the printer then. Try:
**telnet 1.2.3.4 631**
but replacing 1.2.3.4 with the printer's IP address. Don't expect a welcome message, just see if telnet actually connects. If it does, then the printer is listening for IPP connections. If the connection is refused, it's not listening for IPP and we need to thonk of something else.
May I ask for the URL you have? Does it containf the printers IP address?

---

### Post by bwallum on 2007-07-31
telnet: Unable to connect to remote host: Connection refused

That was the response using the command;

telnet 192.168.1.3 631

Then I tried this:

telnet> open 192.168.1.3
Trying 192.168.1.3...
Connected to 192.168.1.3.
Escape character is '^]'.

Minolta-QMS CrownNet  Rev  6.11ET 
magicolor 3100; Release 3.0.2; Processor MIPS; CROWN, 0;

QMS Console Manager
magicolor 3100->
magicolor 3100->Idle
magicolor 3100->Energy Saver
magicolor 3100->

and got a little further. 

In my Windows set up I have to establish a 'Crown Port' which I guess is a link to the onboard printer processor. I also use RAW format.

??

---

### Post by bwallum on 2007-08-08
I have resolved the connection and post this for anybody following:

Navigate to:
System>Administration>Printing 
Select New Printer
Select Network Printer and
Unix Printer (LPD)

In Connection tab:
Host 	192.168.1.3
Queue 	ps

NOTE 192.168.1.3 is my local LAN printer url address. It is included here to show format. You must insert your own printer url.

Use default driver for Minolta 3100

It worked for me although I did need to reboot a couple of times before it was flawless.

Bob

---

