---
title: "Need help connecting to Windows printer"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2006-11-26
Hey, this is my first time attempting to connect to a network using samba.  I downloaded and installed samba, then I typed in the terminal **gksudo gedit /etc/samba/smb.conf** and changed Workgroup=MSHOME to Workgroup=Tsunami (Tsunami is the name of my workgroup network.  How do I go about installing and connecting to a shared printer on a Windows 2000 computer?  Thanks.

---

### Post by peppy.ch on 2006-11-30
hey, to install your printer try to use the system->administation->printers tool box.
There enter a new Microsoft (SMB) network printer and type in the name of the computer that shars the printer and the printer name.
this solution works well for me ;-)

---

### Post by novice1 on 2007-03-13
Don't work for me! Can't get past the window "gnome-cups-add" displaying "Loading printer data base" FOREVER running!!

---

### Post by tondebruijn on 2007-08-25
Hello,


Don't know if this will help anybody but I'm using 
Ubuntu 7.04 - the Feisty Fawn - released in April 2007
The AMD 64 bit version. I have a couple of windows XP and Windows 2000 computers networked in a windows workgroups network.
On one of those computers I have a Laserprinter attached and I set it to a network printer under windows. 
Anyways I just go Places - Network Windows Network and all of my Windows workgroups network computers show.
After I checked this I just went to System-Administration-Printing and I clicked on new printer and added "new printer".
That  It pops up a screen where you can select Network printer and next to it it lets you select windows printer (SMB). After that I had to enter my Windows workgroups username and password  and I also had to select the computer it was attached to. 
This showed me all the printers I had ever installed on that windows workgroup computer and I selected the one that is currently connected.
In the next screen I had to select the printer Manufacturer and Model in my case a Brother HL2040 which wasn't on the list but somewhere else on this forum it said Brother 2060 would work too so I selected that one and it works fine.
Hope this helps people if I entered this in the wrong community the Mods can delete it.
Cheers

---

