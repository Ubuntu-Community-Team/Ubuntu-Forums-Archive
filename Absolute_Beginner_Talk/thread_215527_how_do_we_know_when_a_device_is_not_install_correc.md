---
title: "how do we know when a device is not install correctly?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by qdvubun on 2006-07-14
usually in windows you go into device manager and if something's wrong there's a yellow question nark next to the device name. I went into the Ubuntu devices in Admin--> devices and didn't really understand. 

Thanks

---

### Post by richbarna on 2006-07-14
In ubuntu, when a device isn't installed properly, it doesn't work. It's the same as windows, only the not working part is a bigger clue than the yellow question mark.

---

### Post by ChrisDerson on 2006-07-14
> I went into the Ubuntu devices in Admin--> devices and didn't really understand. 
Scary isn't it?  Don't worry though - the chances of you ever needing to look at this list (let alone understand it) are very close to 0.
Anyway, you've asked a very good question.  As far as I know there is no direct alternative to the Windows Device Manager in Linux.  I could suggest that this is because Linux is so much more reliable than Windows, that attached devices always 'just work', although that's not a very good answer - even if it does tend to be the case ;).
In a sense Linux has an unfair advantage.  When Windows was developed devices often needed tweaking by hand to work together, and it was easier for support staff to use the Device Manager than to go digging.  Modern devices do much more self-configuring, and so the need for an 'easy' diagnostic tool is reduced.
The other thing is that Linux tends to do device discovery each time the machine boots, and so the boot messages should tell you if a device is working or not, so you can look in the system logs to see if any errors are being reported.
For the techy type people, the main diagnostic tools are run form a command line/virtual terminal and include:
[LIST]
[*]dmesg - lists Kernel boot messages
[*]lsmod - lists 'drivers' loaded by the kernel
[*]ifconfig - lists network devices and status
[/LIST]

I hope this helps.

---

