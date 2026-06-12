---
title: "Microsoft Office 2007 Enterprise on Wine?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-06
I have the Office 2007 Enterprise disk. 

Can it work on Wine? 
Is it even possible? 



Thanks,
Tom :KS

---

### Post by saj0577 on 2008-03-06
Give it a go.
Doubt it as the licenses and everything might make it have a few problems.

give it a go let us know :)

Saj

---

### Post by Tom--d on 2008-03-06
It doesn't work because you need the code for xp or vista etc..

---

### Post by smurphy_it on 2008-03-06
Why would you even bother with Microsoft Office ?  Did you try openoffice ?   Better product, can open MS files, is open source and is more compatible.  Not to mention a free download (might already be installed if u r using Ubuntu.

---

### Post by Origin415 on 2008-03-06
What exactly is it asking for? It shouldnt need the Windows key, only the Office key.

---

### Post by Whiffle on 2008-03-06
Nope doesn't run afaik.  Best place to check is [www.winehq.org](www.winehq.org).  


On another note, office 2003 works pretty much perfectly with  vanilla wine.

---

### Post by justin whitaker on 2008-03-06
> **Origin415 said:**
> What exactly is it asking for? It shouldnt need the Windows key, only the Office key.

No, it's hooked in deep into Vista and XP SP2 code. 

[quote="Microsoft"]Certain inking features require running Microsoft Windows XP Tablet PC Edition or later. Speech recognition functionality requires a close-talk microphone and audio output device. Information Rights Management features require access to a Windows 2003 Server with SP1 or later running Windows Rights Management Services.

Connectivity to Microsoft Exchange Server 2000 or later is required for certain advanced functionality in Outlook 2007. Instant Search requires Microsoft Windows Desktop Search 3.0. Dynamic Calendars require server connectivity.

Connectivity to Microsoft Windows Server 2003 with SP1 or later running Microsoft Windows SharePoint Services or Office SharePoint Server 2007 is required for certain advanced collaboration functionality. PowerPoint Slide Library requires Office SharePoint Server 2007. Connectivity to Office SharePoint Server 2007 required for browser-enabled InfoPath forms and additional collaboration functionality. Groove Messenger integration requires Windows Messenger 5.1 or later or Communicator 1.0 or later. Includes a 5 year subscription to the Groove relay service.

Some features require Microsoft Windows Desktop Search 3.0, Microsoft Windows Media Player 9.0, Microsoft DirectX 9.0b, Microsoft Active Sync 4.1, microphone1, audio output device, video recording device (such as a webcam), TWAIN-compatible digital camera or scanner, Windows Mobile 2003 powered Smartphone or Windows Mobile 5 powered Smartphone or Pocket PC, or a router that supports Universal Plug and Play (UPnP). Sharing notebooks requires users to be on the same network.

Internet Explorer 6.0 or later, 32 bit browser only. Internet functionality requires Internet access (fees may apply).

Connectivity to Office Communications Server 2007 is required to enable the full functionality of Office Communicator 2007.[/quote]

Its all here:

[http://office.microsoft.com/en-us/products/HA101668651033.aspx](http://office.microsoft.com/en-us/products/HA101668651033.aspx)

Basically, it needs WIndows Desktop search, .Net 2.0, and a bunch of other crap that Wine does not support yet.

---

### Post by funkameleon on 2008-06-09
I managed to install MS Office 2007 on ubuntu 7.04 Feisty Fawn, using wine-1.0-rc1

here is the howto:

[http://sudosys.be/?q=office2007_wine](http://sudosys.be/?q=office2007_wine)

---

