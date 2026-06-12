---
title: "Peculiar Network Printing Problem"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by kneewax on 2008-04-01
Hi Folks,

I am having a peculiar printing problem.  I have a HP Photosmart 2575 PSC networked printer-cum-copier-scanner.  The printer is setup on a static IP address and is wired to my router.  The laptop I am using is currently wired in, but I also use the printer via the wireless when I decamp from my study with the PC.  

I set it up using the System-Administration-Printing dialogues it is currently identified as a Photosmart 2570 and it seemed to work fine, the test print worked and the documents I have needed to print also seemed to work fine.  However the problem comes when I try to print any document that is mor complicated than basic text and coloured borders etc.  

If the doc (in this case an OOo ODT) contains a table or embedded pictures the job simply goes to the print queue and sticks there forevermore.

I can't seem to work out why.  Cany anyone shed any light on this?

Ta

---

### Post by bumanie on 2008-04-01
Did you use the native ubuntu hplip to install your printer or did you go to the hp linux site and use hp's self extracting installer? I have always used the latter and found the printer to do everything it's meant to. I however have not tried wireless as yet (but plan to try soon!).

---

### Post by kneewax on 2008-04-01
I thought had used the native hplip, but ooking at the Printer again it seems I had used CUPS, but after your post I went back and followed the HP instructions - which worked a treat - the sudo hp-setup command ran and detected the printer no problem and I now have it working properly.

Many Thanks bumanie.

---

