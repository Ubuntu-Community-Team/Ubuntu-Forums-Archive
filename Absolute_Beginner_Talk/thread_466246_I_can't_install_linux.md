---
title: "I can't install linux"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by sowski on 2007-06-06
I've tried to install ubuntu linux on my already windows XP computer, i used a burnable DVD and nero burning software, and i told my computer to boot from the linux cd in my cd drive and it siad disk boot error, someone help me

---

### Post by meng on 2007-06-06
Either the disk is burnt wrongly or the drive doesn't work properly. Also make sure you didn't tell Nero to burn a "bootable disk", that will not work either.

---

### Post by fastpakr on 2007-06-06
Did you verify the checksum of the file after downloading, then burn it at the slowest rate your burner supports?

---

### Post by steeleyuk on 2007-06-06
DId you burn the ISO file as an image (as it should be) or a file directly to disk (as it shouldn't be)?

---

### Post by sowski on 2007-06-06
> **steeleyuk said:**
> DId you burn the ISO file as an image (as it should be) or a file directly to disk (as it shouldn't be)?How do burn it as an image rather than a direct file?

---

### Post by meng on 2007-06-06
> Insert a blank CD into the CD writer. 
Launch Nero. 
In the File menu, select "Burn CD image". 
Choose as file type: all files (*.*), since Nero expects files with the NRG suffix. 
Select the ISO image file. 
You will see a dialog box asking if you want to supply detailed image parameters. Enter the following parameters: 
Type of image: Data Mode 1 
Block size: 2048 bytes per sector 
File precursor and image trailer: 0 length 
No scrambled and no Swapped. 
Click on "burn". If the program complains that there are errors in the image file, click on the button "Ignore" and launch the burning. 
Sadly Nero is rather unintuitive (based on its expectation of NRG files as the default format). Many users report difficulties using it probably.

---

### Post by p_quarles on 2007-06-06
> **sowski said:**
> How do burn it as an image rather than a direct file?
1. Get ImgBurn [[http://fileforum.betanews.com/detail/ImgBurn/1128426215/1]](http://fileforum.betanews.com/detail/ImgBurn/1128426215/1])
2. Put in a disk
3. Run ImgBurn, choose "burn .ISO" (or something similar to that), and point it the Ubuntu file.

EDIT: Sorry, I missed the part that said you were using Nero. I think ImgBurn is an easier app for this specific task, and it's free. But the instructions for Nero will work too.

---

### Post by strabes on 2007-06-06
oops, ignore

---

