---
title: "Please Help...Printer Problem"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by splendid on 2006-04-15
I have a Brother HL 2070N printer that is connected to my router.  I am trying to configure it to work with Linux and am having difficulty.  Can someone help me, Please.....

Thanks,

:)

---

### Post by user1397 on 2006-04-15
[quote=splendid]I have a Brother HL 2070N printer that is connected to my router.  I am trying to configure it to work with Linux and am having difficulty.  Can someone help me, Please.....

Thanks,

:)[/quote] I'm not sure, but I don't think ubuntu can detect printers connected to a router. does it even autodetect it in system>administration>printing>global settings>detect LAN printers?

---

### Post by splendid on 2006-04-15
I tried the auto detect.  No dice.  On the network printers, it asks for URL; etc.  Does not even ask for an IP.  Not sure how I can get this working.

---

### Post by user1397 on 2006-04-15
[quote=splendid]I tried the auto detect.  No dice.  On the network printers, it asks for URL; etc.  Does not even ask for an IP.  Not sure how I can get this working.[/quote]
did you try addprinter>local printer>use autodetected printer?

---

### Post by splendid on 2006-04-15
Yes, I get back "No Printers Detected".

---

### Post by user1397 on 2006-04-15
Try this for the URI: http:/aa.bb.cc.dd:631/ipp

---

### Post by splendid on 2006-04-15
Tried what you suggested.  I get the following message:  

Printing: Unable to connect to IPP host: Success

---

### Post by user1397 on 2006-04-15
[quote=splendid]Tried what you suggested.  I get the following message:  

Printing: Unable to connect to IPP host: Success[/quote]
Success? so it prints???

---

### Post by splendid on 2006-04-15
No, it say's that it is printing, but nothing comes out.

---

### Post by splendid on 2006-04-15
I really appreciate your help!  Any other ideas???

Thanks,

Rob

---

### Post by user1397 on 2006-04-15
[quote=splendid]I really appreciate your help!  Any other ideas???

Thanks,

Rob[/quote]
right click on your printer in "printing" ( system>administration>printing ) and click properties.
what do you see under the driver tab?

---

### Post by splendid on 2006-04-15
Manufacturer:  Brother
Model:  HL2070N for CUPS

Driver:  Standard     Suggested

---

### Post by user1397 on 2006-04-15
[quote=splendid]Manufacturer:  Brother
Model:  HL2070N for CUPS

Driver:  Standard     Suggested[/quote]
i'm not sure if this will work but i have heard it work in similar cases:
go to synaptic, search "hpijs"and install:

- foomatic-db

- foomatic-db-engine

- foomatic-db-hpijs

- hpijs

- hplip-ppds

- libijs-0.35

Then try to print any blank document (openoffice writer, text editor, etc.)

---

### Post by splendid on 2006-04-15
All of those packages were installed on my system already.  I went to Open Office and tried to print something.  Nothing happened.

---

### Post by Compucore on 2006-04-15
Seems like a straight forwards thing for me. Or at least from what I am interpreting it. Usually of the printer is on the network and from my understanding of network itself. When you had initially installed it. Was there ever a queue name for it that comes from your router itself. I can only go from what I know over here. Under most netowrked printers. Whtether they are HP printers, or even my own  Apollo 2150 printer that I had set to share on my dell machine. There was the a name attached to it as well as the name of the printer. So when I want to do a print from my other -machines which are both linux boxes. A del Optiplex GX 150 and an aptiva . They know that the Apollo printer is attached to my oly windows dell computer. Which has a queue name of my windows machines. So it should be similar to that if it is connected to the router itself. There should be a queue name of some sort that is related to the printer on the router itself. 

When I had first installed the printer drivers for my Apollo drivers for it on my breezy badger one. It would not detect it at all. I would literally have to tell it to literally say okay. Here is the name of where it is located on that computer. And here from the set of drivers that are available use these drivers for it. And it worked. Some cases like this the autodetect will not do the job. You need to tell it where it is located in my case it was on my windows machine. So basically I told it the computer name and luckily the drivers are available for the printer for it. And the printer is set to share for all my networked computers. 

Compucore

[QUOTE=splendid]Manufacturer:  Brother
Model:  HL2070N for CUPS

Driver:  Standard     Suggested[/QUOTE]

---

### Post by splendid on 2006-04-15
I am using a computer with a Raid 1 setup (Windows) and my third hard disk is my Linux distrubtion.  Tried giving i the name of the Windows network like you suggested, but I am not having any luck.

---

### Post by user1397 on 2006-04-15
[quote=splendid]I am using a computer with a Raid 1 setup (Windows) and my third hard disk is my Linux distrubtion.  Tried giving i the name of the Windows network like you suggested, but I am not having any luck.[/quote]
Your case is definitely a toughie, I have been exhausted of all ideas!

---

### Post by splendid on 2006-04-15
erik.  Thank You very much for all your help.  I appreciate it!!!

---

### Post by Compucore on 2006-04-16
Ah Splended it's not the network name it is the name of the computer itself. If you are using windows 2000 pro or windows XP. It would be a right click and properties to view the computer name. In this case it would be someting similar to like the name of the printer that is hooked up to your router. Is there a web page that you can log onto to your router. So you can see your setup for the network and for your printer that is hooked up to your router? The example that I was giving was an example that I had to do becuase I had the printer set up on my windows computer and not on my ubuntu system. 

Compucore


[QUOTE=splendid]I am using a computer with a Raid 1 setup (Windows) and my third hard disk is my Linux distrubtion.  Tried giving i the name of the Windows network like you suggested, but I am not having any luck.[/QUOTE]

---

### Post by charon79m on 2006-06-07
Well, first we need to establish how your printer is connected to your router.  Based on the model, I'd guess it is via an ethernet connection.  If that is correct, it's probably using the HP Jet Direct style connection.  That is, you'll choose the Jet Direct printer setup.  There you will need to give it the printer's IP address.  The default port 9100 should be fine.

If it is connected via a parallel cable, you may need to check the router/print server's  directions.  Most I've seen are Jet Direct or Samba style print servers.

I hope this helps.

Charon79m

---

