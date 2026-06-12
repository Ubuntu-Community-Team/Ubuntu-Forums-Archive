---
title: "printer installation"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by bert_p on 2005-10-17
Greetings from an absolute beginner in linux.  I got hold of a copy of Ubuntu installation CD.  To test its features, i had installed it in one of our computers.  The software installation seems okay but I have one problem.  I cannot print.  I am using an Epson dot matrix printer.  What part in the installation did i made mistake?  How can i remedy it?  Your assistance would be very much welcome.

---

### Post by xmastree on 2005-10-17
Go to **System > Administration > Printing** and select "New Printer"

From there you can select local printer, and assuming it's not detected, 'Use another...'

Select the port e.g. Parallel Port #1 (EPSON) then 'Forward' and see if the exact model is listed. If not try either 24 pin series, 9 pin series, or dot-matrix.
(FWIW, I just tested my old Epson LX-300 and it works better with Dot-Matrix rather than 9-pin Series)

You can print a test page by right clicking the printer and selecting properties.

---

### Post by bert_p on 2005-10-17
xmastree,

I followed the instructions you gave and printing is now okay.  Thank you.  Another problem that i encounter is i cannot access my floppy disk drive.  Can you assist me on this? What commands will i do to be able to access it?

---

### Post by xmastree on 2005-10-17
The floppy drive should be accessible via the places menu.

**Places > Computer**

---

### Post by bert_p on 2005-10-17
Thank you once again.  I now can access my floppy drive but why is it that if I accesssome file in the floppy drive in using the open office application, the floppy drive is still not accessible? How can i open my file in the floppy using the open office?

---

### Post by patrick295767 on 2005-10-17
[QUOTE=xmastree]Go to **System > Administration > Printing** and select "New Printer"

From there you can select local printer, and assuming it's not detected, 'Use another...'

Select the port e.g. Parallel Port #1 (EPSON) then 'Forward' and see if the exact model is listed. If not try either 24 pin series, 9 pin series, or dot-matrix.
(FWIW, I just tested my old Epson LX-300 and it works better with Dot-Matrix rather than 9-pin Series)

You can print a test page by right clicking the printer and selecting properties.[/QUOTE]


Hi, i am using Fvwm ...
Is there a way (not using kde and gnome) ?? I tried apsfilter but not big suceess unfortunately ..

thank you 

Pat'

---

### Post by rabosajr on 2006-10-14
Hi, Im relatively new at linux and trying to switch from windows exclusively to ubuntu/kubuntu.
I just got my old pc running with kubuntu, it is now wired to a windows pc with an epson lx300+.
Everything seems to be working fine except for two things:
First, i was able to install the driver for epson Lx300+ and now able to print. However, when I print on continuous paper the first line of the second page leaves a larger margin from the edge of the paper. I am having a problem setting things up. There is not much options for the paper either in the printer setup in openoffice or in the printer settings in kubuntu. 
Second, though entirely not related to the present thread ill just post it here in the hope someone can help, while the kubuntu can see the files in the windows pc, the windows pc cannot browse the folders on the kubuntu pc.

Thanks.

---

### Post by pediatracancun on 2006-11-02
> **bert_p said:**
> xmastree,

I followed the instructions you gave and printing is now okay.  Thank you.  Another problem that i encounter is i cannot access my floppy disk drive.  Can you assist me on this? What commands will i do to be able to access it?

I'm using Ubuntu Edgy 6.10 final version. I've an Epson LX-300+ dot matrix printer; under Ubuntu 6.04 and even Edgy 6.10 Beta versions, my printer worked perfectly, using the Driver for Epson 9 pin dot matrix.
Now with Edgy 6.10 final version, the driver doesn't work. No matter which combination using the generic parallel port or the Epson parallel port, with the different drivers for dot matrix printer, the printer didn't print the form being used. 
I tried several other drivers, and finally the one that works is with a generic parallel port, the Generic IBM Dot Matrix printer. 
Hope this helps some one else.

---

