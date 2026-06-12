---
title: "Enviroment Variables?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-12
Just installed Grip and setting it as the default CD player/ripper.  In System > Preferences > Removable Drives and Media the command for "Play audio  CD discs when inserted" is "sound-juicer -d %d".  In the terminal Help for the command "sound-juicer" the line for option -d reads:
```
-d, --device=DEVICE             What CD device to read
```
I don't understand why in the long form of this option one uses an equal sign and (I presume) a device name like "hdc" (or does it need the path, e.g. /dev/hdc?)  I'm guessing the the %d in the command above means something like "the device that started the application" but don't really know.  Where can I find a listing of variables like this?  The Help for the particular command itself doesn't give this information.

Thanks for your help,
Buck

---

### Post by adaptr on 2006-12-12
> **Buck2348 said:**
> Just installed Grip and setting it as the default CD player/ripper.  In System > Preferences > Removable Drives and Media the command for "Play audio  CD discs when inserted" is "sound-juicer -d %d".  In the terminal Help for the command "sound-juicer" the line for option -d reads:
```
-d, --device=DEVICE             What CD device to read
```
I don't understand why in the long form of this option one uses an equal sign
Because that is part of the long form.

>  and (I presume) a device name like "hdc" (or does it need the path, e.g. /dev/hdc?)
A device name *is* the full path to the device - it won't work without it.

>   I'm guessing the the %d in the command above means something like "the device that started the application"
No, it means "fill in the string that was passed from the command line" - in this case, the shortcut to the application, which was called by clicking on a CD drive.
The shell (or desktop) filled the device name of the CD drive into %d, which the application read and used.

> but don't really know.  Where can I find a listing of variables like this?
In the documentation for your desktop environment, hopefully.
This method is usable with any command executed from the desktop, so you could make it do whatever you want.


>   The Help for the particular command itself doesn't give this information.
Of course it doesn't: the application merely reads the value, it does not provide the mechanism for filling it with something you clicked.
That is done by the desktop environment (or the shell).

---

### Post by Buck2348 on 2006-12-12
Thank you for your reply.

Buck

---

