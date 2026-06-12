---
title: "Network Drive Issues"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Sq322 on 2006-05-22
I posted this in the Dapper forum but realized it might be better suited to be here.

Ok, I am a total NOOB here.
I have run Dapper off of the live Beta 2 CD a number of times now. I have played around with it and LOVE it. I am having one issue that needs to be resolved before i install and take the plunge for good.
I have searched the forums for a solution to my question to no avail. Sorry if i missed one inadvertantly someplace.
My scenario and question is this.
I use my laptop at work. I connect to a network drive [Y:] where some of the programs i need are stored. These programs run under windows.
I need to be able to run these programs thru Linux. I have installed wine and tried to use that, but cannot seem to figure out how to get it to recognize and run programs in that [Y:] directory.
I have had no problem getting it to run things in the [C:] directory.
Also, I am trying to find a way to automount and have access to 2 other network directories [Z:] and [\\sys\Company]
any help getting me thru this and enabling me to go forward with installing Linux would be most appreciated...
Hope i explained this well.

Thx in advance

---

### Post by Sendervictorius on 2006-05-23
Th "Y:" drive is a windows file server, the c: drive is your local hard disk.

To connect to the Y: drive you can use:
Places->Network Servers, or
Places->Connect to Server , and choose "service type: windows share"

You should then be able to navigate through the file system

Whether you can use wine to run the windows programs... you will just have to see. Not all programs will run under wine.

---

### Post by Sq322 on 2006-05-23
Thx,
Is there another option if Wine will not run the program ?

BTW..Love the Asterix avatar....

---

