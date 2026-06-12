---
title: "HP 2600n printing on a network"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by AiBo on 2005-12-28
Hello All,

I am new to Linux. The cost of software seems out of control, especially those living on a Chinese salary, I decided to make the switch to Linux.  Ubuntu seemed the most user friendly, and it is great so far....but....

I need to be able to print at the office.  This one point might force me back into the M$ trap.  Please help me overcome this, so I do have to return to the darkside!

We have a HP Colorjet 2600n connected to the network.  A search of google and others produces results that this printer does not work with Linux :(.  I hope this is wrong.  I have tried all of the work arounds i could find, but coupled with my inexperience with Linux and well....pretty much my inexperience, I get nowhere!

Thanks to all those willing to help.  This will go along way in converting our whole office as they all like what they see so far on my system!

Rob

---

### Post by AiBo on 2005-12-30
I have tried installing the foo2hp drivers from: [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/)

This printer is on the network.  I cannot even seem to find it.  I have tried using it IP address also with no success.  It doesn't even appear present.  Actually I have no printers listed as "detected printers"

Anybody?

---

### Post by thekiller on 2005-12-30
First of all, you need to know the IP of the network printer. Open up Firefox or a similar browser and type this into the location bar :

```

localhost:631

```

You will see a CUPS (Common Unix Printing System) website, from there select [COLOR="Red"]Manage Printers[/COLOR]. You should be able to see a network printer in there. Lookout for the IP and then on the top menu bar go to System -> Administration -> Printing. Then just add the printer. Hope it helps.

---

### Post by prizrak on 2005-12-30
You should go to your Printers dialog click on Global Settings>Detect LAN Printers that should allow your machine to see printers that are on the network. Since it's a networked printer it shouldn't have a problem with any OS.

---

### Post by linear on 2005-12-30
Was one of your sources this? (From [http://hpinkjet.sourceforge.net/faqs.php](http://hpinkjet.sourceforge.net/faqs.php))

> Q. Are drivers available for the Deskjet 710C, 712C, 720C, 722C, 820Cse, 820Cxi, 1000Cse, 1000Cxi; or LaserJet 1000, 1005, 1020, 3100; or Color LaserJet 1500, **2600** printers?
A. These are **non-standard host based **printers. Currently there are no plans to support these printers in HPLIP. Ghostscript print filters for the Deskjet products can be found at the pnm2ppa project at [http://sourceforge.net/projects/pnm2ppa/](http://sourceforge.net/projects/pnm2ppa/).

"Non-standard host based" is a little scary. I wonder what is missing from the printer?

---

### Post by AiBo on 2006-01-02
Thanks for the help so far...

The current situation is that I now can "see" the 2600n, both in firefox under localhost 631 and in the system->administration->printing.  The driver seems to install fine and the printer is added.  When I attempt to print a test page, it sends, nothing prints and it is gone, no error messages.  I am using the foohp2 driver.  Across the network I was not detecting a printer, but when I am USBed straight to it I "see" it.  Is there any way to access it directly through it's IP number?

Thanks for all the help!

---

### Post by ispmarin on 2006-02-21
It seems that the foomatic driver works fine for greyscale, but not for color. I found a solution, well, not very satisfactory, but is a solution here:
[http://casa.che-che.com/blog/2005/12/06/hp-2600n-printing-color/](http://casa.che-che.com/blog/2005/12/06/hp-2600n-printing-color/)
Let's see if it works.

Ivan

---

### Post by ispmarin on 2006-02-21
Hello again.
The gnome-cups-manager does not manage to change correcty the defautl page size, from Letter to A4 (when A4 is selected, the printer assigns the margins wrongly). You have to edit the /etc/cups/ppd/<printer>.ppd file and change this fields, from Letter to A4:
DefaultPageSize
DefautlPageRegion
DefaultImageableArea
DefaultPaperDimension
This works fine and prints correctly. (Well, the two printers, the Color and Greyscale...)

See ya! Hope it helps.

Ivan

---

### Post by ubernoob on 2006-03-17
I changed the fields to A4, but it doesn't seem to be able to write on the whole page. It is moved. Either on the top, or from the bottom.

---

