---
title: "Error code of 21 after reboot"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by buddy w on 2007-02-07
Hi everybody I have just installed ubuntu every thing went very well!!! except when I did a reboot the system will not start and I get an error code of 21 What does this mean and what do I need to do to correct? I think it has to do with the Grub loader. When I boot I get system loading i.5 and then the error pops up and all comes to a halt. The live CD stil works very well or I could not write this distress call.

Thanks 
bw

---

### Post by Sef on 2007-02-07
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

What file system did you install Ubuntu on?

---

### Post by Turkey Pwner on 2007-02-07
I have had this error since I first installed Ubuntu Breezy Badger (I have installed Dapper and Edgy, all new installations - don't ask why).  I had installed Ubuntu Breezy and Dapper on a ext3 file system, and I have Edgy installed on a ReiserFS file system.  Ubuntu shares the computer with Windows, and Windows was installed before I installed Ubuntu...

I receive a message that Grub is going through step 1.5, and it gives an error 21 message.  I can reboot with ctrl+alt+del, and that loads to Grub, but I would like to load Grub properly, and not have to go through the "hassle" of pressing ctrl+alt+del... plus, I would like to load properly. :)  It's also kind of cumbersome, and it's annoying to my family. :B (parents, so they're like "why do you have Ubuntu if it's such a hassle?  You ruined the computer?  ftw? @_@)

Thank you for any help. :)

---

