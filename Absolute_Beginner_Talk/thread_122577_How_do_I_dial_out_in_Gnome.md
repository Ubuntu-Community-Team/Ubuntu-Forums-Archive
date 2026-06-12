---
title: "How do I dial out in Gnome?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by cosmic_nomad on 2006-01-28
How do I access dialup networking in Gnome?  In KDE it's just KPPP but in Gnome, I cannot find it.

Also, I don't know if my modem is supported in Ubuntu.  It works in Linspire..where can I find a list of supported modems and if it's not on the list, where can I find drivers for Ubuntu.  Modem is PCTEL HSP56 modem.  Linspire sees it as Smartlink Softmodem.

---

### Post by super on 2006-01-28
try this: system->administration->networking. select 'dial-up networking/ppp' and click 'configure'. you should be able to just fill in the information. when it asks for a location of the modem the most common is /dev/modem. the critical part is if your modem is supported by linux or not. many 'win/softmodems' are not.

if your modem is a softmodem it gets a bit trickier.
visit 'linmodem' for supported modems and their drivers. download and install with the given instructions. if that still doesn't work, download 'scanmodemhere' (you may need to download this in windows then copy it in linux) and run it from the terminal.

it will report the make of modem in the file called modem**.txt in the same place where ur scanmodem script is.

If u cant still make out, send them your modems1.txt to [http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html) and they can give you better instructions.

---

### Post by cosmic_nomad on 2006-01-28
Ah. Thank You.  

It would not autodetect my modem from the Live CD.
I am wondering if it would from a full install?
  
I ask because Linspire will find my modem fine from a full install but it will not see it at all if I run the Live CD.

Thank you for the links, linux is a lot of reading and a steep learning curve but you people really help quickly and that helps a lot.

---

