---
title: "Aficio 2022 network printer"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by loksipan on 2005-09-30
I am trying to hook up my Ubuntu machine to an office network printer.

We have a Ricoh Aficio 2022.  

There are 2 drivers listed in the printer-install-manager-thingy - Aficio 2022 PS and Aficio 2022 PXL.   The PS
one appeared after I did an Ubuntu update but the PXL one I installed previously myself from linuxprinting which listed it as  the pdd for Aficio 2022 and noted it "works perfectly".

Trying both I use the URL [http://192.168.2.7:550/printer/](http://192.168.2.7:550/printer/) in the CUPS setup.

With this URL, if I send a test page to the printer I get the following error :

"Printing: Network host '192.168.2.7' is busy; will retry in 30
seconds..."

....only the printer isn't busy :-(

192.168.2.7 is the IP address of the printer.  The printer has a
separate hostname "RNP7E28AC"  but if I use this in any configuration, I get a "printer does not exist error".

Our gateway is 192.168.2.1 

A port scan of 192.168.2.7 reveals the following.

21 open ftp
23 open telnet
80 open www
139 open netbios-ssn
514 open shell
515 open printer
631 open ipp

I tried the recommended URL [http://192.168.2.1:631/ipp/](http://192.168.2.1:631/ipp/)  which seems more logical but I get a printer does not exist error.  The same if I use the other URL formats offered:-

ie. 
[http://hostname:631/ipp/](http://hostname:631/ipp/)
[http://hostname:631/ipp/port1](http://hostname:631/ipp/port1)
ipp://hostname/ipp/
ipp://hostname/ipp/port1

Can anyone help?

Thanks

loksipan

---

### Post by loksipan on 2005-09-30
I managed to get my Ubuntu printing on our network Aficio 2022 printer.  For the record here's how.

System->Administration->Printing
Add Printer.
Network Printer - Unix Printer(LPD)
Host: 198.162.2.7        {this is the printers ip address}
Leave Queue empty
Choose Aficio 2022 PXL printer driver (can be downloaded from linuxprinting

It doesn't print the test page for some reason but documents, spreadsheets, email etc seem to be all okay.

I doubt this is the proper set up but if it works I'm not complaining.:razz:

Loksipan

---

