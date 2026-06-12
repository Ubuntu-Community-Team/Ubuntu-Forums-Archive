---
title: "Gimp and printing photos"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2006-04-11
I am running Breezy and have been for a few hours now thanks to the help on this forum :D 
I have an Epson Photo 220 which appears to have been setup correctly in that it printed a test page, can print from Openoffice and printed a picture from gThumb.
The problem is that it cannot print from Gimp for some reason. I select print and choose all of the options I want (papersize etc) but all that comes out is a load of black text.
From reading the forums, i can see that a few people have reported similar things, but  cannot find a post with a solution. The only thing I was wondering miht be a problem is that it is using the 200 driver as I couldn't find a driver for the 220.

---

### Post by Kimm on 2006-04-11
I have the same problem with both my Printers, one Epson Stylus CX3500, and one HP LaserJet 5L. The first was not detected and I had to use an older driver but the later was detected right away (after running cups setup).

Though gthumb is good enough for printing pictures, and so is OpenOffice, so I didnt worry about it to much.

---

### Post by Twizzle on 2006-04-11
Thanks for the quick reply.

I have tried printing with gThumb but can't seem to find any settings to alter the picture quality. I am trying to print a photo onto glossy photo paper, and with gThumb I am getting a very grainy picture.

---

### Post by jeremy on 2006-04-11
have you set up your printer withing gimp?

File -> Print... -> printer settings

---

### Post by Twizzle on 2006-04-11
Yes, I have tried all of that, and my printer is selected. As it happens, since rebooting to XP and printing the picture and now coming back yo Ubuntu, I cant print anything!..... Think I am just going to give up till the morning now...

---

### Post by rayburn on 2006-04-16
I've just come across this thread while trying to solve exactly the same problem, and by clicking the setup printer button within Gimp I managed to find my printer (Stylus Photo R300) and it now works perfectly!

Hope this is of interest to someone.

---

### Post by kwyjibo on 2006-04-16
i've got a very similar problem, i have a lexmark x1185 printer (nightmare) using the z600 driver as recommended.  Test pages work, can print from thumb view, open office, etc.  But when I try to print from Gimp it goes in to the print queue, sits there for a bit and then dissapears as if printed although nothing has happened on the printer.

As far as i can see it's all set up right, and the fact it goes to the correct queue suggests it's mapped to the correct printer, so any idea why this might be happening?

I just had a look and it has printer model set to Postscript level 2.0, and out the list of printers neither my model or the z600 is listed, although to be honest if it's looking at the right driver and mapping (which it is), having it set to PS shouldn't matter... should it?

---

### Post by kwyjibo on 2006-04-17
sorry a little bump, just cos i've spent all day trying to find a solution.  Search these and other forums, google, and all i've found is that quite a few people have the same sort of issue, but there doesn't seem to be a solution anywhere  :(

OR, what is another good package that will let me print photos, choose quality and paper, and resample or resize images to print?

---

### Post by crazygerad on 2006-06-03
The way to go about it is this go to [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) find your printer model and get the ppd and save it where you like.

After going through the hellish proccess (I am using a HP PSC 1350 and I spent three hours and at the end I just turned the printer off and then on and followed the hplib people instructions and it worked. You can laugh at this) of installing your printer go to Gimp and select File > Print, here you will see a huge scary windows and look at printers and Select Setup Printer. In PPD select browse and select the PPD you downloaded, will that be all? No, it won't. Then click the standard command and select the command for your printer that appears in the list. If you are lucky it will be there. Then click ok and then PRINT AND SAVE SETTINGS so you dont have to set this again. 

I hope this has helped you and can anyone tell me how to tweak this thing because the images come crappy?

---

### Post by moontide on 2006-06-04
I had major problems with getting myEpson Stylus Photo 915 printer to work with  Breazy. I'm sorry I can't point to the thread, but the fix was as follows:
1) to stop my printer from moving to "pause", prior to printing I have to enter from the comand line (each time I start the computer) "sudo chmod 666 /dev/usb/lp0". That gets me a perfect print.
2) If I want to print photos from gimp (I only print photos from gimp). I have to select print/setup printer and then remove "-oraw" from the driver form field. I still find gimp printing not as reliable as usual. Cups still doesn't work for me and I even managed to access my printer from the cups website.

I have found Breazy to be the hardest linux distro to print from for me ever and I've been using linux for 8 years, although I still think ubuntu is a great distro.

---

