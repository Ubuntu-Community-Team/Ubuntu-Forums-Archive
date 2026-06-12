---
title: "Mounting a MiniDVD Video Camera"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2008-01-29
I have a Sony DVD450 MiniDVD video camera that I would love to get working on my 7.10 Gutsy Gibbon machine. I have the camera connected via a USB cable and the camera is in search mode looking for the PC but Ubuntu seems to have no knowledge of its existence. Nothing shows up in Nautilus or anywhere else I can find.  

How can I get the camera disk to mount as a drive so I can transfer the mpeg video files to my PC?  I did a little searching on the board first and noticed people were posting the results of a lsusb command in Terminal. Not sure if that helps in this situation, but here it is:

Bus 002 Device 003: ID 413c:3016 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 054c:0254 Sony Corp. 
Bus 001 Device 006: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 009: ID 0d49:7010 Maxtor 
Bus 001 Device 007: ID 0644:0200 TEAC Corp. 
Bus 001 Device 008: ID 04a9:221c Canon, Inc. 
Bus 001 Device 003: ID 03f0:1812 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

This line definitely references the device (it goes away when I disconnect the camera):

Bus 001 Device 010: ID 054c:0254 Sony Corp. 

Thanks.

---

### Post by spiderbatdad on 2008-01-29
this thread may help:[http://ubuntuforums.org/showthread.php?t=652849&highlight=mount+camera](http://ubuntuforums.org/showthread.php?t=652849&highlight=mount+camera)

You may also be able to have it actually mount by plugging in before you power on. Then, too there is creating a mount point and using mount commands...which will require some reading.

---

