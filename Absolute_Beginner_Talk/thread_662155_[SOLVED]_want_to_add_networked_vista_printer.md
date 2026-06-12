---
title: "[SOLVED] want to add networked vista printer"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by warthogism on 2008-01-08
Just as the title says, i'm trying to add a network printer that's connected to a vista pc.  I've gone to the the system -> admin -> printing.  I go to the network via SAMBA option and find my vista pc, but the printer does not show.  any help? 

Do I need to install SAMBA?  i was under the impression that that was not necessary.

 TIA.

---

### Post by Pevichaey5 on 2008-01-08
i had this problem on my home network, have you enabled file and printer sharing on vista, also is it viewable from other windows machines, (the printer that is)

on my Linux box, System>>Administration>>Printing

then i clicked New Printer

then 'Windows Printer via Samba' and clicked browse, this scans the network for shared printers and it should be fine, however depending what printer it is, you may need to get hold of a driver, i did for my brother printer/scanner/copier

hope this helps

---

### Post by warthogism on 2008-01-09
> **thexero said:**
> i had this problem on my home network, have you enabled file and printer sharing on vista, also is it viewable from other windows machines, (the printer that is)

on my Linux box, System>>Administration>>Printing

then i clicked New Printer

then 'Windows Printer via Samba' and clicked browse, this scans the network for shared printers and it should be fine, however depending what printer it is, you may need to get hold of a driver, i did for my brother printer/scanner/copier

hope this helps

everything is fine on the vista end.  Other xp computers on my network print just fine.

I did just as you describe above; I find the vista computer via samba, but the printer does not show up.  where and how do i install said driver?  on the vista machine? or the linux one?

---

### Post by yabbies on 2008-01-09
Just a suggestion, make sure your printer is compatible with Linux.
Have a look[ here]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters")

I know for sure Lexmark is notorious for not making any open source drives.

---

### Post by Pevichaey5 on 2008-01-09
what printer is it? i think brother provide driver for their printers for linux thats how i got mine 2 work, but the printer was showing up before i installed the drivers, but i had to install the driver when i came to the final adding of the printer

---

### Post by warthogism on 2008-01-09
I got it working (at least the test page printed out).  

It turns out that the printer was being shared, but it needed a username and password (though I never had to actually enter any info on my other xp machines when i needed to print).  So I turned off the name/pass requirement. now the printer shows up when trying to add via SAMBA.

So I added it and picked the appropriate PPD driver.

Thanks for the help guys.  Esp. Thexero.  when you said you had the same prob, i knew i was close and just needed a bit of tinkering.   \\:D/

PS it's a samsung ML-1740

---

### Post by cmcfarland21 on 2008-01-09
I have a desktop that has Win XP on it.  My HP printer is connected to it.  I have a laptop with XP that was printing through my wireless network to the same printer.  I recently added Ubuntu 7.10 to the desktop on a second hard drive.  When I boot into Ubuntu, my laptop does not see my cpu therefore I can not print   I think this is simple fix but I have no clue.   FYI, My desktop with the printer and Ubuntu loaded CAN see my laptop through the network.

---

### Post by Pevichaey5 on 2008-01-09
glad you got it fixed :D

good luck for the future

---

