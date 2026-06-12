---
title: "Any hope of decent photo printing?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2007-10-30
Well I've been trying for some time now and can't seem to get any decent photo printing done.

I've installed the latest hplip software for my HP PSC 1410 printer.

I can't seem to get Gimp to recognise the printer at all.  Spent ages with that but it just sulks.  Even sending a test print takes about 5 minutes.

From a networked laptop running XP I get instant response.

Following other threads I can print photos by inserting them in to a OpenOffice document.  Using the HP toolbox, I can then set the paper to glossy photo and the printing to 600dpi full bleed etc.

This is very laborious and the results are poor compared to the same printer driven by XP.

Finally, my question is.....is it worth trying any further, is there anybody getting good results with a similar setup or am I doomed to dual booting Widows for all the techy stuff.

Thanks

---

### Post by timcredible on 2007-10-30
i have an hp c4280 and it prints great from digikam - i have the 4x6 photo paper insert thing, and the pictures are the same as when printed from windows.  try digikam instead of gimp for printing.  you can change the printer settings from within digikam.

---

### Post by steve.horsley on 2007-10-30
I have a print queue called Deskjet_1280 which on Gutsy simply appeared when I turned the printer on (in earlier versions, I had to use the menu System->Administration->Printing and create the queue by hand). 

To use the print queue in the GIMP, I had to open a picture and select File->Print then click Setup Printer. I found the best approach is to leave the printer as postscript level 2, and then select the appropriate PPD file. I had to install package hpijs-ppd to get the exact PPS definition file. Certainly for me, the GIMP has never had problems finding my print queue.

---

### Post by Phosphoric on 2007-10-30
Thanks for the replies folks.

Selecting postscript printer 2 is not very intuitive but it works!:)
 
I've set the best possible print options separately in HP Device Manager and got a reasonable print.  So thanks to Steve for that one.

I've also downloaded DigiKam but couldn't get a print function.  Downloaded some plugins (it's all blind isn't it) and now have a print option.  Couldn't find an easy way of selecting the exact print size in digikam so will load a new image and try again.
Thanks timcredible for your advice.

Report back later.

---

### Post by Phosphoric on 2007-10-30
OK, bit more playing around and I find that I can indee change the print size relatively easily in digikam and a big plus, I can alter the print paper and resolution directly within the application.

Haven't found a way to change printing aspects from within Gimp yet.  

Just waiting for Gimp to print out the same image for comparison......

There appears to be a very, very minor difference in print quality, Gimp being the better.  However digikam was easier to set up and is a photo handling and printing solution in one.

Which to go for?


Well. Gimp cost me nothing and Digikam cost....nothing also.

Linux Ubuntu makes life so hard. :)

Thanks for the inputs, when I can be really bothered I will try a 3 way contest against a Windows driver and HP application.


:KS:KS:KS

---

### Post by drmatty on 2007-11-18
It would be nice if the photo programs could automatically select the photo paper tray and highest quality print output when printing. Making it "just work" would be very helpful in getting people to "just switch".

---

### Post by kelvin spratt on 2007-11-18
I use photoprint it will print a single image to a sheet or multiple images and if you save default settings, Will keep the printer settings for you, It can be found under search in synaptic just type photo.

---

### Post by Benbow on 2007-11-18
I have also made several posts on this subject. I have a Canon MP170 and always go back to xp for my photo printing.
I have tried (and bought!) Turboprint which gives better results with basic b&w and colour printing but for quality, forget it.
I was under the impression that HP printers were the bees knees with Linux, but perhaps not.
Never mind, one day...........................

---

### Post by drmatty on 2007-11-18
> **kelvin spratt said:**
> I use photoprint it will print a single image to a sheet or multiple images and if you save default settings, Will keep the printer settings for you, It can be found under search in synaptic just type photo.

Thanks, I'll try. I have an HP that I can print with, wireless, but I just can't get great photo output.

---

