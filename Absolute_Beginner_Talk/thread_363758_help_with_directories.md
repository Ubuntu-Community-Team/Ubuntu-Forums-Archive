---
title: "help with directories"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-02-17
I am attempting to install drivers for an HP printer. I downloaded an installer that is now sitting on my desktop. The next step in the instructions is:

After downloading make sure to put the hplip-1.7.1.run file in the directory you will want the hplip directory to be created.

How do I know what directory I want this in? How do I access that directory? What is a directory? You help will be appreciated greatly.

---

### Post by meng on 2007-02-17
Which printer? You may be trying to do it "the hard way". And which version of Ubuntu? HPLIP may already be installed.

---

### Post by paydaydaddy on 2007-02-17
> **meng said:**
> Which printer? You may be trying to do it "the hard way". And which version of Ubuntu? HPLIP may already be installed.

Dapper Drake. HP 2210 PSC

---

### Post by Tilex on 2007-02-17
These drivers are included in Ubuntu.  Go in Settings -> Printers -> Add printer -> "choose how the printer is connecter to your computer" -> "in the list of Manufacturers, choose HP  and then PSC 2210".

---

### Post by Maestro23 on 2007-02-17
> **Tilex said:**
> These drivers are included in Ubuntu.  Go in Settings -> Printers -> Add printer -> "choose how the printer is connecter to your computer" -> "in the list of Manufacturers, choose HP  and then PSC 2210".

Beat me to it. To the OP, why make the easy things hard.;)

---

### Post by paydaydaddy on 2007-02-17
> **Tilex said:**
> These drivers are included in Ubuntu.  Go in Settings -> Printers -> Add printer -> "choose how the printer is connecter to your computer" -> "in the list of Manufacturers, choose HP  and then PSC 2210".

I went through that process and stopped partway through because I thought the system was looking for drivers that were not there. I get to the point where I click the "install driver" button then I am told to "select a PPD file". I don't know what to do at that point.

---

### Post by meng on 2007-02-17
Most modern HP printers are excellent illustrations of how much easier it is install printers on Ubuntu compared to Windows. Windows requires an install disk and 200+ MB of installation (mostly crap, you don't get a choice) to get the printer run. Ubuntu uses a driver included in the installation. The only potentially confusing thing is specifying the connection method (e.g. USB, parallel cable, network), that is, if the connection type is not auto-detected (it often is).

---

### Post by paydaydaddy on 2007-02-17
> **meng said:**
> Most modern HP printers are excellent illustrations of how much easier it is install printers on Ubuntu compared to Windows. Windows requires an install disk and 200+ MB of installation (mostly crap, you don't get a choice) to get the printer run. Ubuntu uses a driver included in the installation. The only potentially confusing thing is specifying the connection method (e.g. USB, parallel cable, network), that is, if the connection type is not auto-detected (it often is).

I'm sure that If I knew what I was doing I would agree with you.

---

### Post by meng on 2007-02-17
System > Admin > Printers > Add Printer

and tell us how it's connected too.

---

### Post by paydaydaddy on 2007-02-17
> **meng said:**
> System > Admin > Printers > Add Printer

and tell us how it's connected too.

Network. The printer is connected to an XP machine on the network.

---

### Post by ubuntu27 on 2007-02-17
> **paydaydaddy said:**
> I went through that process and stopped partway through because I thought the system was looking for drivers that were not there. I get to the point where I click the "install driver" button then I am told to "select a PPD file". I don't know what to do at that point.


You need to select or install a DDP files when you don't have the desired driver installed.

In your case, the drivers that perfectly fits to your printer is  "hpijs" which is already installed in Ubuntu (If it's not, look it on Synaptic Package Manager)

So, make sure tu select "hpijs" and click ok. You do not need to look for a DDP file yourself. :)


Enjoy!

MORE INFO:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2210](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2210)

---

### Post by Tilex on 2007-02-17
> **paydaydaddy said:**
> I went through that process and stopped partway through because I thought the system was looking for drivers that were not there. I get to the point where I click the "install driver" button then I am told to "select a PPD file". I don't know what to do at that point.

Are you sure you did exactly those steps?  Because I just did the same and I got to the end asking to print a test page...That looks pretty much the end to me.

---

### Post by paydaydaddy on 2007-02-17
My little BB sized brain made me think that the "install driver" button needed to be clicked. I have now clicked "forward" and the wiz now want "description and location". Is this as straightforward as it seems? I.E.:

description: HP 2210 PSC
Location: maindesk/printers/hp 2200 series

or is there something else that should be entered?

---

### Post by Maestro23 on 2007-02-17
> **paydaydaddy said:**
> My little BB sized brain made me think that the "install driver" button needed to be clicked. I have now clicked "forward" and the wiz now want "description and location". Is this as straightforward as it seems? I.E.:

description: HP 2210 PSC
Location: maindesk/printers/hp 2200 series

or is there something else that should be entered?

Just follow the bread crumbs man, you are making this harder than it should be.:)

---

### Post by paydaydaddy on 2007-02-17
> **Maestro23 said:**
> Just follow the bread crumbs man, you are making this harder than it should be.:)

Uh, is that a yes or a no?

---

### Post by Maestro23 on 2007-02-17
> **paydaydaddy said:**
> Uh, is that a yes or a no?

Name your printer and then put in the location if you want to. Location is not required, it is more for your reference.

---

### Post by Tilex on 2007-02-17
The location is the location in your house, it's just for description purposes.  Like "Bedroom" or "basement" and the name is the same thing.  You can name it "HP 2200" or "Headache" if you want ;)

When you'll print out something from, say, OpenOffice, you'll see the printer with Name: Headache, Location: Basement.

In a university, it's nice to see the type of printers, out of the 100s, and the floor on which the printer is located.

---

### Post by paydaydaddy on 2007-02-17
> **Tilex said:**
> The location is the location in your house, it's just for description purposes.  Like "Bedroom" or "basement" and the name is the same thing.  You can name it "HP 2200" or "Headache" if you want ;)

"Headache" sounds about right. I followed the Wiz and guess what. No Worky! LIke I said, this would be easy if I knew what I was doing.

---

### Post by meng on 2007-02-17
You don't have to press the "install drivers..." button, that button is only for when you can't find a matching printer in the list. You just make sure the appropriate model is highlighted in the list, then press OK or Next or something. Stay away from the "install drivers" button, it's the equivalent of "install from manufacturer's disk" that you might see in Windows.

---

### Post by meng on 2007-02-17
> **ubuntu27 said:**
> You need to select or install a DDP files when you don't have the desired driver installed.

In your case, the drivers that perfectly fits to your printer is  "hpijs" which is already installed in Ubuntu (If it's not, look it on Synaptic Package Manager)

So, make sure tu select "hpijs" and click ok. You do not need to look for a DDP file yourself. :)


Enjoy!

MORE INFO:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2210](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2210)

and this is just to highlight that you were ALREADY given the same advice. Read carefully!

---

### Post by steve.horsley on 2007-02-17
> **paydaydaddy said:**
> I went through that process and stopped partway through because I thought the system was looking for drivers that were not there. I get to the point where I click the "install driver" button then I am told to "select a PPD file". I don't know what to do at that point.

It's a badly worded dialog. Don't click the Install Driver button - just click OK. The Install Driver button should really be named Install Different Driver or something like that. The fact is, you wouldn't find the printer name in the list of printers if the driver wasn't already there.

---

### Post by meng on 2007-02-17
Agreed, it is confusing, the same problem has tripped up many users before. The OP is correct, in that it's very easy and obvious once you've done it!

---

### Post by paydaydaddy on 2007-02-17
Okay, fine guys, I have been throught the wizard and can't print. Sorry to be such an obvious idiot, but for some of us noobs (at least me) all the choices and answers are not so obvious. I will attempt another run-through on the wizard and enter some different answers to the choices and see what happens.

---

### Post by meng on 2007-02-17
It's connected to a Windows computer on the network, but can I confirm with you that it is a network-capable printer that can be accessed directly by its IP address?
(If not sure, you can use firefox and enter the printer's IP address in the address box and see if the HP printer info comes up.)

Choose HP JetDirect as the connection type, then enter the printer's IP address in the appropriate box (I think it's URL).

However, if you're sharing the printer with Windows over samba, it may be more complicated, I don't have any personal experience with that.

---

### Post by paydaydaddy on 2007-02-17
> **meng said:**
> It's connected to a Windows computer on the network, but can I confirm with you that it is a network-capable printer that can be accessed directly by its IP address?
(If not sure, you can use firefox and enter the printer's IP address in the address box and see if the HP printer info comes up.)

Choose HP JetDirect as the connection type, then enter the printer's IP address in the appropriate box (I think it's URL).

However, if you're sharing the printer with Windows over samba, it may be more complicated, I don't have any personal experience with that.

I don't have the slightest idea if it has it's own IP address. It is not connected to a router, it is connected directly to one of the XP machines in the house. Printing from another XP machine is no problem. I would like to be able to print from a linux machine without changing the printer connection. I do not have Samba installed.

---

### Post by meng on 2007-02-17
Then instead of HP JetDirect option, you need the Windows share (SMB) option, and you should specify the IP address of the computer to which the printer is connected. Samba is already installed on your machine.

Hopefully this will work, although as I said I've never tried this. It is more complicated than setting up a true network printer or a directly connected one.

---

### Post by meng on 2007-02-17
Sorry, only just realized you have two threads going on this issue. I'm going to shut up now.

---

### Post by paydaydaddy on 2007-02-17
actually my original question has not been answered.
What is a directory and how do I access one?

---

### Post by Maestro23 on 2007-02-17
> **paydaydaddy said:**
> actually my original question has not been answered.
What is a directory and how do I access one?

cd = Change directory

EX: /home is a directory.  
     /etc is a directory.
    /username is a directory.

This site will help you understand terminal commands and linux file system.  

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by paydaydaddy on 2007-02-17
Thanks for the link. I will read through it (more than once I'm guessing).

---

