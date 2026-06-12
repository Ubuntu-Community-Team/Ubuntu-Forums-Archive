---
title: "Printing from Gimp"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by cheeseborough on 2007-06-02
I am slightly puzzled as to what is going on on my computer. I have my HP 3920 printer configured in the Ubuntu Printers successfully, I can print the test page successfully, and I can print from Open Office and Firefox.

The problem comes when I try to print from Gimp Image Editor. When you go into the print dialogue you have to specify the printer driver again, only there isn't a HP 3920 in the list. I've tried with a couple of different HP printers HP DeskJet 3820 and 1200C for instance but although the job appears on the printer list with a "Job Printing" status, nothing comes out of the printer - the printer's light just blinks frenetically - and the job doesn't appear to progress.

The command that Gimp is using to send the print job is 
lp -s -d 'DeskJet-3920'  -oraw

---

### Post by starcraft.man on 2007-06-02
Hmmm, ok I'm no GNU Image Manipulation Program expert but, I think I see what your doing....

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/screenshot1.png[/IMG]

It looks like you have to set up a new printer cuz the dialog has a nice big space where I guess your expecting to see printer icons, however it seems to me the important part is the dialog box I point to (red arrow).

It should default to your printer, it did to mine (I even printed a test page through it to make sure it was right). If there is a problem with your printer (I wouldn't know its specifics, I'm still new to the program overall) you can always save the image out as whatever format you like, open it in any other program (Image Viewer for instance) and print that way to your regular printer :).

Oh and, yay for Beryl and Annotate plugin, that was real easy to draw arrow and crop SS :D

Edit: And if someone knows better feel free..... >.>

---

