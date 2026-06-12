---
title: "Sharing printers to Windows boxes"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by lgmdaniel on 2005-12-19
I'm running both windows and Utuntu on my machine at home, but my wife's PC just runs windows (XP). Now I want her to be able to network print to the printer (HP DJ 5150) is this something that possible? Can I use CUPS, and if so are there any ports that I will need to enable? or setting a need to set?
I'm running 5.10 Gnome at the moment though I'm looking to switch to KDE.
I'm getting fed up with rebooting into windows to allow her to print at this rate I'll just move the printer to her machine.  I have tried a few things myself but Gnome and admin access seems a little restrictive.

---

### Post by MartinG on 2005-12-19
You need to install samba and set it up to share your printer. NB this means samba proper, the server package, not just smbclient which only allows you to browse Windows boxes, not to share your files or printers. Easy with KDE, I don't know about Gnome.  Then on the Windows box you should be able to find the printer in the normal way.  Once it's set up right, samba is first-rate.

If you've got a firewall set up you need to open the relevant ports. Using Firestarter to manage the firewall, there is a pre-defined rule set that covers the necessary ports (137-139, 445).

If you're having difficulty getting it all to work (I've been there!), turn off the firewall till you're sure you've got samba working as it should, then address the firewall issue.

---

