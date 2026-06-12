---
title: "WHY WON'T MY WIN 2000 PRO BOOT PROPERLY?? ( yup, next question )"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-13
OK, thanks for all your help in the last few threads I made. :)

Now, after reinstalling my ubuntu, I have a problem...
I try to boot my windows 2000 pro, and it tells me that it's missing some driver, application, or something like that, and that I need to reinstall it ( question is, how, if it doesn't boot in the first place? -_- ) and then I usually have no exit or anything, just that message there, I always need to press the restart/power button to get anywhere.
Why is it showing me this and how can I get rid of it so it'll boot again? 
Thanks if anyone can help me....

---

### Post by PriceChild on 2006-10-13
Could you tell us the exact message and when it occurs?

Its important to tell that it is windows giving you the error.

---

### Post by Ryupower on 2006-10-13
Oh, yeah, that'd be helpful no? ;)

OK, it says ( translated from German ):
[I]
Windows 2000 could not be started, since the following file is missing or broken
<windows2000 root>\system32\ntoskrnl.exe

Install a copy of the above named file again.[/I]

great, kernel...

anyways, any help here?

---

### Post by JayTee on 2006-10-13
boot from your Windows CD and then choose Recovery Mode. Windows Setup will provide a prompt asking you to choose a new install or Recovery Mode. Choose a new install (Don't Panic!). Setup will then find your existing Windows partition and current installation. It will then give you the options to _press R to Repair_ or Esc to not repair. You want to repair. It will start copying system files to replace any potentially damaged ones. It will also seem like it's installing a completely new install BUT IT ISN'T. All your applications will still be there and will be usable. You will have to enter your regional settings info and your product key though. This takes less time than a new install and you shouldn't take the time estimates seriously. It's usually less than 20 mins on most computers and less on the newer, faster ones. There is a command you can run from the command line in Recovery Mode to copy a new ntoskrnl.exe to your system partition but I recommend the above method as it takes care of any other corrupt or missing files and avoids numerous reboots to the system running again. Good luck!

---

### Post by Ryupower on 2006-10-13
THANKS! 
Only thing I'm worried about now:
It's gonna kick my Linux out of the boot menu again...

---

### Post by PriceChild on 2006-10-13
Then follow this:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

(Second post)

---

### Post by Ryupower on 2006-10-13
Ah, I read an article on that one. I tried it, and that's how my ubuntu partition got screwed up in the first place...:(

BTW: how am I supposed to know which partition is "/" and " /boot" ?
Just a stupid newbie question...

---

### Post by ifouane on 2006-12-02
Hi, I got the same error message after Ubuntu installation, but W2K repair is not working. It does not retrieve the previous W2K installation and says all my initial FAT32 and NTFS partition are damaged or unknown format, altough they still appear correctly in Linux

---

### Post by ifouane on 2006-12-11
Hi, I finally understood what what happening:
While installing Linux in the disk free space, I was creating a new primary partition which in turn changed the number of my windows partition (it is a partition inside an extended partition). The result was that the windows boot.ini file was no more pointing to the right partition. Simply editing this file solves the problem

---

