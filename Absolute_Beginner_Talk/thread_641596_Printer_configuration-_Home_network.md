---
title: "Printer configuration- Home network"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by ghoran on 2007-12-15
Hi everyone,

I have not yet installed Ubuntu 7.10
I have run it off my 2 desktops from the live CD with no problem.

In other words, I am trying to plan everything out by reading a book "Beginning Ubuntu" and getting used to the "thread life"

Here is my question:

Both my desktops have removable master hard drives. Something like this: 
[IMG]http://www.datacity.net/dci7b.jpg[/IMG]

Here is the detailed llink of something LIKE what I have. Mine is 15 years old.
[http://images.google.com/imgres?imgurl=http://www.datacity.net/dci7b.jpg&imgrefurl=http://www.datacity.net/removable-hard-drive-kits.html&h=230&w=320&sz=16&hl=en&start=4&tbnid=zg0NP8TYmMOeKM:&tbnh=85&tbnw=118&prev=/images%3Fq%3Dhard%2Bdrive%2Bcaddy%2Bdesktop%26gbv%3D2%26svnum%3D10%26hl%3Den%26sa%3DG]("http://images.google.com/imgres?imgurl=http://www.datacity.net/dci7b.jpg&imgrefurl=http://www.datacity.net/removable-hard-drive-kits.html&h=230&w=320&sz=16&hl=en&start=4&tbnid=zg0NP8TYmMOeKM:&tbnh=85&tbnw=118&prev=/images%3Fq%3Dhard%2Bdrive%2Bcaddy%2Bdesktop%26gbv%3D2%26svnum%3D10%26hl%3Den%26sa%3DG")

How this works:
Mounted in the case is a part that is screwed into the area that the hard drive would go (FRAME). Power and data cables run from this to the motherboard. Each hard drive that I would want to use is put into a case not much bigger than the hard drive.(SHELF) This means that I can physically pull out the hard drive (it is in a case{shelf}) and change the hard drive (I have multiple hard drive cases). Of course, the computer must be off.
My main computer has Windows XP on the current hard drive.
I am going to install UBUNTU 7.10 on a new hard drive.

My question is with the printer that I have.

The printer is an HP PSC 1507- All in one. It is attached to this computer through a USB port.

I checked [http://hplip.sourceforge.net/supported_devices/inkjet_aio.html]("http://hplip.sourceforge.net/supported_devices/inkjet_aio.html")

and found my printer
[FONT="Courier New"]
Model Name 	Min. HPLIP Version 	Parallel 	USB 	Network or JetDirect1 	Print Class 	Scan to PC3 	Photo Card Access4 	PC Send Fax5 	PC Initiated Copy6 	Services and Status7 	Driver Plug-in
PSC 1507	0.9.5 	No	Yes	No	DJGenericVIP 	Yes	No	No	No 	Yes	No[/FONT]

My question is, once I get the computer that it is attached to see the printer, how do I get the other computers on the network to see it. I have both Windows computers(laptops- One ME and one XP) and another computer that I will be putting UBUNTU on.

I have seen some things about IPP, CUPS and  Samba (I believe that the printer is attached to a windows machine in this case). The documentation I saw talks about how to connect to a print server broadcasting one of these but, not how create one and which is the best to create

I see that HPLIP uses a version of CUPS ([http://hplip.sourceforge.net/tech_docs/overview.html]("http://hplip.sourceforge.net/tech_docs/overview.html"))

Should I be using HPLIP? Anyone have comments about that software?

In addition, is there a common protocol that I can use so that when I change the swappable drive, on what I will call the print server, from Ubuntu to Windows all the client computers will not have to change?

Thanks
Gary

---

### Post by TheLions on 2007-12-15
WOW a lot text to read!

if i understand you, you want to share printer between windows and ubuntu?

i have printer pluged in Vista pc and shared to ubuntu.

How to do that?

install printer in windows, enable file and printer sharing

in ubuntu install samba, configure samba and then go to system-->admiistration-->printer

there press new printer then select windows printer over samba and press search

after that select your printer, print!:)

---

### Post by ghoran on 2007-12-15
Thanks!!

I was actually going to put UBUNTU on the machine with the printer attached to it. 
I also wanted the ability to switch that machine to windows and share the printer (You answered that)

How would another computer see the printer if I am running UBUNTU on it?

---

### Post by ghoran on 2007-12-15
Hey everybody,
I did not get the answer to my original questions.

1. Does anyone have any HPLIP experience
2. How would I make a printer attached to a machine running UBUNTU available to the other machines on my network (Windows ME, Windows XP and UBUNTU)

---

### Post by dstew on 2007-12-15
I think HPLIP will automatically install with 7.10. If not, you can install it using the Synaptic package manager. If you have HPLIP installed, you will name your printer hp://*whatever* in the printer installation dialog. That is, you use the **hp** prefix, I believe.

You can share the printer that is connected to your Ubuntu machine with the other Windows computers. See [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

