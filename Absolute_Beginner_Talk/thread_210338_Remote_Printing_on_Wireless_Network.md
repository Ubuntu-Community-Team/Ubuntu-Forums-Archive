---
title: "Remote Printing on Wireless Network"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by JerryC on 2006-07-06
I am running ubuntu 6.06 64 bit with an Epson CX 3810 printer connected by USB.  My machine is direct connected to a wireless router and then to a cable modem.  My wife's machine is running Win XP Pro and is connected to the wireless network through a USB device.  Is it possible to make it so she can print to the printer connected to my machine?

JC

---

### Post by AndyCooll on 2006-07-06
Yes it's possible to do so.

[Network Printing With Ubuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

:cool:

---

### Post by JerryC on 2006-07-06
That answer has to do with ubuntu 5.10.  Are we pretty sure it will work with 6.06?

JC

---

### Post by persev on 2006-07-07
Well this worked on 2 of my networked computers, one wireless laptop and one desktop, but on a laptop that was "upgaded" from Breazy to Dapper and is ethernetted I get and error "The CUPS server could not be contacted.". I made sure CUPS was installed and reinstalled it via Synaptic but still get the same error. Any ideas? I should say that I have Dapper installed on 4 computers at home 2 desktops and 2 laptops.

---

### Post by mssever on 2006-07-07
> **JerryC said:**
> That answer has to do with ubuntu 5.10.  Are we pretty sure it will work with 6.06?

JC

It was a breeze for me in Dapper (clean install) with an HP printer. I just went to the add printer menu on my Dapper desktop and added my printer--worked without any configuration needed. Then I installed Samba, setup the machine name and workgroup in /etc/samba/smb.conf and ran "sudo smbpasswd -a <username>". Then I went to my WinXP laptop and used the add printer wizard to add a network printer (I did have to use the printer driver CD here). Now, printing works.

---

### Post by JerryC on 2006-07-07
OK.  One of you sent me to the document "Network Printing With Ubuntu".  Besides being very skeptical about just copying a bunch of text into what appears to be a very important file, later on, in the section on setting up the Win XP machine, it says to point the WinXP machine at "http://PRINTSERVERNAME:631/printers/PRINTERNAME".  Where do you get the printservername and the printername?  Don't get me wrong.  I believe this will work if I knew what I was doing, but I don't yet.  I just need a bunch of hand holding.  Then someone suggested the use of samba.  What does samba do for you?  Thanks for the help.

JC

---

### Post by persev on 2006-07-07
I resolved my problem after searching many threads by editing /etc/cups/client.conf, after "Server" I changed to text to "localhost".

---

### Post by JerryC on 2006-07-07
I thought I would learn something about samba, so I downloaded samba-doc-pdf.  Now I can't find it.  Where did it go?  I even used slocate as root from the root.

JC

---

### Post by mssever on 2006-07-07
Before you can use [FONT="Courier New"]locate[/FONT] to find a file, you have to update the index. This is done by running [FONT="Courier New"]updatedb[/FONT] as root. Your computer probably runs [FONT="Courier New"]updatedb[/FONT] automatically avery 24 hours.

If you use Synaptic, you can click on a package name and click properties. There will be a list there of the files that package adds.

The way I used to learn about using Samba was simply by going to Samba's website. Probably the documentation you downloaded is identical to docs available on the website.

Briefly, here's what Samba does. Samba makes Linux computers work on Windows networks. So, you can share folders on your Linux box and access them from Windows (using the syntax \\machinename\sharename) or you can share printers that are attached to your Linux box and use them from Windows computers. It also works the other way. You can access windows computers and printers attached to Windows computers. I've never done this part, however.

---

### Post by RaZer0r on 2006-07-09
About the "http://PRINTSERVERNAME:631/printers/PRINTERNAME" link: it goes as folowing: http://"ip adres of printserver":631/printers/"The name of the printer you have".
You can find the printername in: System --> Administration --> Printing and make sure you use capitals wherever needed. the /printers/ part is just the same at any system.

Make sure you set the printer to default device (rightclick, Make Default)

In my case it makes: [http://192.168.0.3:631/printers/Deskjet-710C](http://192.168.0.3:631/printers/Deskjet-710C)

---

### Post by JerryC on 2006-07-10
OK everybody; thanks for the help.  I'll study all of this and give it a shot.  I'll be back later with either an update or some more questions.

JC

---

### Post by JerryC on 2006-07-10
To RaZerOr:

> You can find the printername in: System --> Administration --> Printing and > make sure you use capitals wherever needed. the /printers/ part is just the > same at any system.

> Make sure you set the printer to default device (rightclick, Make Default)

> In my case it makes: [http://192.168.0.3:631/printers/Deskjet-710C](http://192.168.0.3:631/printers/Deskjet-710C)

I have found the correct printer name: Stylus-CX3810.  Where do I find the IP number?  I tried all of them in the cups file which didn't work.  I even tried your 192.168.0.3 which, as expected, didn't work.

JC

---

### Post by stricevics on 2006-07-20
> **RaZer0r said:**
> About the "http://PRINTSERVERNAME:631/printers/PRINTERNAME" link: it goes as folowing: http://"ip adres of printserver":631/printers/"The name of the printer you have".

In my case it makes: [http://192.168.0.3:631/printers/Deskjet-710C](http://192.168.0.3:631/printers/Deskjet-710C)


What happens when that IP address is assigned by DHCP on the router? How do you configure linux to connect to the printserver with dynamic IP?

---

