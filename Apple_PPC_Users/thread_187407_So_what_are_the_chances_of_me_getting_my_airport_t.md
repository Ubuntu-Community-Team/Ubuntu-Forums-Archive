---
title: "So what are the chances of me getting my airport to work?"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by alx1507 on 2006-06-02
Am I better off just sticking to os x until broadcom releases some information? or until someone creates a solution?  

Or is there a solution i'm not aware of?

EDIT: airport card, not the base station itself

---

### Post by user1397 on 2006-06-02
[quote=alx1507]Am I better off just sticking to os x until broadcom releases some information? or until someone creates a solution?  

Or is there a solution i'm not aware of?[/quote] First of all, what type of mac do you have (especially interested in processor).  If it is a PPC (PowerPC), then download the PPC ubuntu dapper LTS desktop cd, and try it out.  See if it connects automatically, and if it doesn't, look around for help and you'll probably find the answer.

---

### Post by ipstone on 2006-06-02
Actually last weekend, I installed the dapper LTS mac edition onto my ibook,
the system runs great, even it seems that sleeping works to some extent

but, I cannot get the wireless network working (enrypted), I guess no password network might work, but my wireless network really need password protection

the other thing kept me back is the lack of the dual boot selection , I didn't see a dual boot selection even though I installed dapper onto another partition on my harddrive, so after some tries, I gave up configuring yaboot, ... but I have to use mac os x install CD to restore my mac os boot ...


so these are the two thing kept me back from ubuntu on my ibook G4 14, if these two are solvable, I will move my ibook to ubuntu

---

### Post by alx1507 on 2006-06-03
[QUOTE=erik1397]First of all, what type of mac do you have (especially interested in processor).  If it is a PPC (PowerPC), then download the PPC ubuntu dapper LTS desktop cd, and try it out.  See if it connects automatically, and if it doesn't, look around for help and you'll probably find the answer.[/QUOTE]

I have a powerbook G4 (ppc obviously since its G4) and I have the live CD of 6.06 LTS.  My airport card doesn't work, and it has no password protection on it.  I've heard that older airport cards work, but newer version don't. 

I'm also having trouble installing LTS on my external firewire, but thats another story...

---

### Post by user1397 on 2006-06-03
[quote=alx1507]I have a powerbook G4 (ppc obviously since its G4) and I have the live CD of 6.06 LTS.  My airport card doesn't work, and it has no password protection on it.  I've heard that older airport cards work, but newer version don't. 

I'm also having trouble installing LTS on my external firewire, but thats another story...[/quote] Did you try the live cd yet? especially the internet?

---

### Post by alx1507 on 2006-06-03
yes i've tried the live cd, i've used it, i've played around in it, but my airport card doesn't work, I can't access the internet.

---

### Post by n00bWillingToLearn on 2006-06-03
I have a 17'' powerbook with Airport Extreme and I just got it working.

I followed these instructions using the link given to download the drivers and wifi-radar as opposed to Network-Manger ( you don't need either but they automatically detect / connect to wireless networks );

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

Extra info if you want it:

The howTo is not meant specifically for Airport cards, or PPC but it worked for me ( with Airport Extreme on PPC I don't know about plain Airport ( the older version ) or using it on intel based macs) basically Ubuntu already has the drivers to use Airport ( and all other broadcom based cards ) but for legal reasons are not allowed to have the firmware to use those cards installed by default so you are getting the firmware from the windows driver ( you are not using the windows driver like you would with NDIS wrapper ) and using the drivers Ubuntu already has to do the rest.

---

### Post by n00bWillingToLearn on 2006-06-03
So to answer your question "what are the chances of me getting my airport to work?" I would say almost guarenteed as I have gotten several to work and have never heard of anyone who was NOT able to get thier Airport working using the broadcom firmware. The only reason I pointed you to a new thread which is not Airport specific is because I think the instructions are more updated for Dapper and easier to follow. But thier is also a wiki showing how to do it @ [https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29](https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29).

---

### Post by savantelite on 2006-06-04
All these wiki's keep leading me to Windows drivers. I HAVE A MAC!!!

I have a powerbook g4 500. it has a regular airport card, but ubuntu 6.06 does not detect it. I am using the decktop cd (LIVE CD)

I really want to install ubuntu on my book but it is pointless if I can not access wireless internet.

Show me I can catch something in lake ubuntu before I move there. please help me with my wireless

---

### Post by n00bWillingToLearn on 2006-06-04
[QUOTE=savantelite]All these wiki's keep leading me to Windows drivers. I HAVE A MAC!!!

I have a powerbook g4 500. it has a regular airport card, but ubuntu 6.06 does not detect it. I am using the decktop cd (LIVE CD)

I really want to install ubuntu on my book but it is pointless if I can not access wireless internet.

Show me I can catch something in lake ubuntu before I move there. please help me with my wireless[/QUOTE]

[Edit] I am sorry I may be misunderstanding what hardware you have by regular airport card do you mean it is not an airport Extreme?

---

### Post by JackosKing on 2006-06-04
I added a part in the airport extrem wiki page:
[https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29](https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29)

(Sorry for my english)
have fun!

---

### Post by n00bWillingToLearn on 2006-06-04
Ok, I have only ever set up Airport Extreme cards in Ubuntu but I have never tried to set up a regular airport card. I have looked into it and it seems that there are two different kinds of plain airport cards, one is made by broadcom and the other by Orinoco. I believe the one made by Orinoco should work by default but the broadcom deosn't. Since you implied that your card is a broadcom card and it doesn't work by default then it probably is.

The problem with broadcom cards is not that Ubuntu doesn't have the drivers, it does, it is that it doesn't have the firmware. Frome what I understand, the wireless needs to get it's firmware from the computer every time it is turned on because it is only being stored in volitile memory on the card so it is lost when the card is not being powered. The firmware that the card needs is the same whether the card is being used on a mac PPC or windows X86 ( or mac X86).

 SO YOU NEED THE WINDOWS DRIVERS EVEN ON A MAC.

 You are not using the part of the driver used by windows on the computer itself but only extracting the firmware and disguarding the rest.

I don't know if which version of the firmware you need for an older airport card so I would search around / post a new thread specifically asking what drivers / firware version to use and then follow the guide I linked to already but with the windows drivers you find you need and not the ones he links to.

The thread about getting broadcom cards to work in Ubuntu is again @ [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

[edit] I didn't know this because I found the correct firmware version in the windows drivers but you can ALSO get the firmware from OSx and then you'l be sure that it is the right version because if it weren't your Airport card wouldn't be working in OSx iether. The directions for setting up an Airport Extreme card say to look in /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2 

to find the drivers but I don't know if that is the driver for plain Airport, Airport Extreme, or both so, again, I would make a new thread specifically asking how to get the correct firmware for a broadcom, plain Airport card.

---

