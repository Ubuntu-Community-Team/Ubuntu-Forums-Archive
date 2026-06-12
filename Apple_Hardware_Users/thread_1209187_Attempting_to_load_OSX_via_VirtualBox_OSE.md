---
title: "Attempting to load OSX via VirtualBox OSE"
date: 2009-07-10
forum: Apple Hardware Users
---

### Post by reddog4063 on 2009-07-10
I have a working OSX 10.4.6 DVD that I am trying to create a virtual image of via VirtualBox OSE. My operating system is Ubuntu 9.04. Has anyone gotten this to work? When I attempt to load the ISO file I get error:

 p, li { white-space: pre-wrap; }     Medium [COLOR=#0000cc]'/home/brian/ISO/Mac OS X Install DVD.iso'[/COLOR] is not accessible. Could not access the image file [COLOR=#0000cc]'/home/brian/ISO/Mac OS X Install DVD.iso'[/COLOR] (VERR_FILE_NOT_FOUND).
 
    Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  Console
   Interface: 
  IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


Thank you in advance for any advice, tips, tricks or comments.


Joseph

---

### Post by Clorow on 2009-07-11
You can't, since that's virtual hardware, and the DVD installer only recognizes Apple hardware. I even tried bootstrapping it with the famous boot-132 disk, but that doesn't work either, sadly.

Thank goodness you didn't try it directly onto a non-Mac computer, which would have corrupted the MBR! :(

---

### Post by Richardcavell on 2009-07-11
I've just been discussing this on IRC.

I am quite sure that OS X simply cannot be virtualised without elaborate technical wizardry. It's possible that someone with that wizardry might give it a go and get it to work under a virtualiser or emulator (probably not VirtualBox), but I doubt that Apple or Sun will help them do it.

Richard

---

