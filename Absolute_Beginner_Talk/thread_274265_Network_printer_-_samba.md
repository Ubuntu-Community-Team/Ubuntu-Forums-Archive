---
title: "Network printer - samba"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by SorenM on 2006-10-09
Hi

I need help regarding setting up LAN printers.
I filled in these informations:
The Network is Windows local LAN, Workgroup name is "mshome", The Server name is "Com1" and the Printer sharename is "Lexmark4".
I did filled it in as "marked" but i didn't work.
Then I tried to install "Samba", and found that I should just write "sodu opt - get install samba" on the command line - but I couldn't find the "Command line"
Can anybody give me a hint here??
  
Best regards
Soren

---

### Post by sKuarecircle on 2006-10-09
All I can do is tell you what I did.

My comuter is set up to network with a XP Box, no server, so maybe this won't help.

All I did and i kid you not was go to printers, new  printer, click on the network printer radio button, pick windows printer from the drop down box, put in the IP address, picked the first thing i saw on the drop down box, it was "Printer 1" followed the prompts and hey presto.

Piont is the first time i installed Ubuntu I went and Installed Samba and configured it yada yada.

This time ( I had to reinstall) I went to places/network servers on the off chance that it was working. AND IT WAS!! Straight after installation it had picked up all my network computers and the printers. I just clicked on them and ta da! It seems that before you go throiugh the =hassle and make things unesicarily difficult try the simplest thing, you will be surprised at how easy ubuntu is to work on.

Assuming you didn't know all this already

---

### Post by ImpelGD on 2006-10-09
After reading this topic I tried adding my HP Deskjet which is plugged in to a Buffalo LinkStation. System > Administration > Printing > Add Printer... I left the password fields bland when asked to connect to the Windows LAN and it works fine.

---

