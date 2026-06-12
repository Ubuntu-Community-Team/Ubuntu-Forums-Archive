---
title: "[SOLVED] viewing xrays on ubuntu"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by DarinB on 2008-04-03
I received a cd from a patient wth xrays on it... it won't run in ubuntu
it has an exe program. is there a linux program that can open it?

---

### Post by Tomatz on 2008-04-03
Type this in a terminal:

**sudo apt-get install wine**

then run the .exe with wine (usually just a double click)

---

### Post by ugm6hr on 2008-04-03
I've never used PACS medical systems on Ubuntu - only Windows.

Were there any other files other than the exe?

Presumably the exe is a self-extracting viewer for the images. but the raw images should be on there too.

With a bit of luck, the raw images are stored in a generic format.

---

### Post by DarinB on 2008-04-03
unfortunately i can't access the raw images

---

### Post by kombipom on 2008-04-03
The images are probably DICOM files.  There is an open-source java based viewer called imageJ.  It doesn't seem to be in the repositories but give it a google.  I don't think that more common image tools support DICOM but I could be wrong.

---

### Post by Tomatz on 2008-04-03
> **DarinB said:**
> unfortunately i can't access the raw images


Did using wine work???

---

### Post by DarinB on 2008-04-03
when i right click the .exe open with wine it says i need explorer 6 how do i add that????????

---

### Post by tangibleorange on 2008-04-03
you'd probably have to find a windows version of internet explorer 6 and install it in WINE as well...

---

### Post by Tomatz on 2008-04-03
> **DarinB said:**
> when i right click the .exe open with wine it says i need explorer 6 how do i add that????????

Follow the instructions on this page:

[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)  (it will download and install ie6)

I am only 50% sure that this will work with the .exe though.


Worth a try i suppose ;)

---

### Post by Ripfox on 2008-04-03
The IE4 Linux usually solves the problem, once installed don't try to run it though, it just has to "be there"

---

### Post by DarinB on 2008-04-05
i installed xmedcom from synaptic but i can't find it or figure out how to use it????
i can open the raw images with gimp but they are small and a inverted instead of a proper radiograph 
i would like to be able to use my pc instead of having to reach for an old beat up laptop to view patient films

---

### Post by ugm6hr on 2008-04-05
Hard for anyone to try to help without knowing exactly what the images are like.

Obviously you can't supply samples (confidentiality).

Not sure what else to suggest.

---

### Post by DarinB on 2008-04-06
yeah i am stuck can't publish patient films but i can say that it is a disk with a GE program (windows only) that brings up the plane film xrays large enough to see and a magnifier>>>>the raw images with gimp come out very small and the background is white with the bones black it can be used but i wouldn't stake anybodies reputation in court over them. not the best way to view films too bad i much rather enjoy old school (the films in my view box)
i have wine installed but i don't know how to pop in the cd and have wine open it when i right click and choose open with wine it says i need ie6 i installed ie6 via this forum but it doesn't do anything unless i am missing something simple.
i would like to get help using xmedcom it is in my pc from synaptic but from there i don't know what to do i don't even have it in the apps menu

---

### Post by ugm6hr on 2008-04-06
> **DarinB said:**
> i would like to get help using xmedcom it is in my pc from synaptic but from there i don't know what to do i don't even have it in the apps menu

Alt+F2 (or in Terminal):
```
xmedcon
```

Then try opening the image file.

This might help: [http://xmedcon.sourceforge.net/Docs/ProgramGUI](http://xmedcon.sourceforge.net/Docs/ProgramGUI)

Be interested to see how this works!

---

### Post by DarinB on 2008-04-06
it is a little difficult but it works with xmedcom
thanks

---

### Post by ugm6hr on 2008-04-06
> **DarinB said:**
> it is a little difficult but it works with xmedcom
thanks

Difficult in what way?  The program, or the way of launching?

xmedcon can be added to the menu manually to allow it to be launched easily.

If you right-click on an image, it should allow you to set the default program as xmedcon to launch it too.

That way, a double-click on the image should launch it automatically.

---

### Post by DarinB on 2008-04-06
how do you add an app manually??

---

### Post by ugm6hr on 2008-04-06
System-> Preferences-> Main Menu
Select "Accessories" under "Applications" (or wherever you want to place it)
Click New Item
Type: Application
Name: DICOM Viewer
Command: xmedcon
Comment: View DICOM images
Click OK
Click Close

It should now be in Accessories Menu

---

### Post by DarinB on 2008-04-06
great I'm good to go
thanks

---

### Post by ugm6hr on 2008-04-06
Good to know you won't you won't need either your Windows machine or medical malpractice insurance any time soon!!!

---

### Post by DarinB on 2008-04-07
Thanks LOL

---

### Post by ugm6hr on 2008-04-10
In case anyone else stumbles onto this DICOM thread...

[http://www.nongnu.org/aeskulap/](http://www.nongnu.org/aeskulap/)

Aeskulap is a good viewer too, and has an Ubuntu .deb (for 6.06LTS, but it seems to work with Gutsy too).

Specifically, it plays XA (coronary angiogram) films and echocardiograms stored in DICOM format too.

I've also found it in the Hardy repo :)

---

### Post by DarinB on 2008-04-11
I know I marked this as Solved, but Aeskulap is far SUPERIOR to xmedcom.
thanks 
D

---

### Post by ugm6hr on 2008-04-13
> **DarinB said:**
> I know I marked this as Solved, but Aeskulap is far SUPERIOR to xmedcom.
thanks 
D

I agree.

More intuitive interface, and better features.

---

### Post by DarinB on 2008-04-15
thanks
 loving Ubuntu everyday and the forums

---

### Post by scottslinux on 2008-04-15
I just viewed my dads coronary cath films the other day before his cabg surgery. it was an exe file DICOM viewer from GE.  It ran first shot but then I have crossover installed and IE6.

---

