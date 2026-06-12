---
title: "Can't See Ubuntu Partition After Install....Help!"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by neweraforfire on 2008-12-16
Hi guys, i am trying to dual boot my machine so i can run OS X 10.5 and Ubuntu 8.10. I have read what seems like every forum or guide that google has offered me, but still no luck. These are the stages i have gone through:

[LIST]
[*]I partition the amount of space I want Ubuntu to have using BootCamp, which is 20Gb.
[*]I then reboot my machine, and with the Live CD i made earlier hit 'C'.
[*]When the machine has booted into Ubuntu i hit the 'Install' icon on the desktop.
[*]I now go through the install choosing my Location, Keyboard Layout and so on.
[*]When i get to the partition option, i click manual.
[*]I can now see my BootCamp partition, which is called dev/sda3, and formated in Fat32.
[*]I click on this partition, and click edit.
[*]Where it says format, i choose 'ext3' and for the mount point '/'.
[*]After this I click next and carry on with installation (I do get a message about not having a swap partion, but even when i made one before, Ubuntu wouldn't boot)
[*]After filling out my name, password etc, I get to a window showing me what Install options I have choosen.
[*]I press the 'advanced' button and choose 'dev/sda' as the boot loader (A guide on the web said to do this, but again have tried without changing this option, and nothing)
[*]So after all this is good, I click install Ubuntu.
[*]After the install is complete i click 'restart now'.
[*]I reboot my machine holding down the 'alt' key after the chime, and Bang....................Only Macintosh HD availible.
[/LIST]

_My Machine Configuration:_
[LIST]
[*]MacBook (Black)
[*]Santa Rosa Chipset
[*]2.4Ghz
[*]Intel Core 2 Duo
[*]250Gb HD
[*]2Gb Ram
[/LIST]

Any help is much appreciated........Thanks.

Oh and please don't mention rEFIt, I know its possible to do it without. I think its proberbly a boot loader issue.

---

### Post by cyberdork33 on 2008-12-16
> **neweraforfire said:**
> Oh and please don't mention rEFIt, I know its possible to do it without. I think its proberbly a boot loader issue.
Actually, you need refit. but since you don't want to hear that as the answer...

(Oh, it is covered in the the FAQ by the way:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677))

---

### Post by Chrisj303 on 2008-12-16
> **cyberdork33 said:**
> Actually, you need refit. but since you don't want to hear that as the answer...
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677))

Yes.

And anyway, why would you not want to use rEFIt? Not only does it make this possible, but its just as fast as holding down the alt key and prettier! 

Fantastic piece of software, IMO....

---

### Post by neweraforfire on 2008-12-18
Hay guys thanks for the help, turns out i did need rEFIt.....LOL!

---

