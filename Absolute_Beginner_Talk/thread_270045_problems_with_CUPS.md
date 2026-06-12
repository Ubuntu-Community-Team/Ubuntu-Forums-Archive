---
title: "problems with CUPS"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-10-02
Hello there,

somehow it doesn't print right. :) I have a SuSE box in my network running CUPS and successfully accepting and handling print jobs coming from XP (iieeh) machines. Now I tried to print from ubuntu for the first time and it doesn't go well. I configured the printer to be found at ipp://192.168.0.1/printers/BrotherHL1250 which is I'm sure the right address. I try to print a test page say from my local CUPS administration page, I see in the cups log of the print server that the job was accepted and everything seems to be correct, but what comes out of the printer is:

@PJL JOB NAME="Ghost"
@PJL SET ECONOMODE=OFF
@PJL SET MEDIATYPE=REGULAR
@PJL SET RESOLUTION=300
@PJL SET RAS1200MODE=OFF
@PJL ENTER LANGUAGE=PCL
126A126A...(a long weird code)

Same thing happens when I try to print an actual document. 

What now?

---

