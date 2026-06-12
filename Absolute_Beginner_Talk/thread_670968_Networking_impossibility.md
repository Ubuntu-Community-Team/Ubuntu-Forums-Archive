---
title: "Networking impossibility?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by sladigar on 2008-01-18
I am relatively new to the Linux experience, and have not had much time to get around the new ways of thinking. I have managed to only reload once, and I'm kinda proud of that. In the month or so that I've been using Ubuntu 7.10, I have gotten the layout pretty much how i want it, I have figured out what multimedia software i prefer, I have even gotten a printer/scanner to work. Not bad for a n00b. My most recent accomplishment was getting into my winbox through my linux box. I did this by setting up a new network in windows, and refreshing the network location in linux, easy peasy. But I can't reverse the process. I would like to access both hard-drives in my linux box through my winbox, for win specific programs. Any suggestions?

---

### Post by charleseddy on 2008-01-18
Absolutely.  Your hard drives on Linux are most likely ext2 (extended 2) partitions, as opposed to NTFS or FAT32--which are probably those used on your Windows hard drive.

To be able to recognize ext2 hard drives in Windows, install Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)).  This should take care of your problems with not being able to read Linux drives.

If you have any more issues, feel free to reply and let me know.

ce

---

### Post by Dynaflow on 2008-01-18
Are these Linux and Windows drives in the same computer, or, when you say "Winbox," do you mean an entirely separate computer?

---

### Post by sladigar on 2008-01-18
two completely separate, and old, computers. the windows computer has two harddrives, and the linux computer, which used to be windows, also has two, larger, harddrives. the second drive in my linux computer is ntsf format, so win should not have a problem seeing it, right?

---

### Post by sladigar on 2008-01-18
> **charleseddy said:**
> Absolutely.  Your hard drives on Linux are most likely ext2 (extended 2) partitions, as opposed to NTFS or FAT32--which are probably those used on your Windows hard drive.

To be able to recognize ext2 hard drives in Windows, install Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)).  This should take care of your problems with not being able to read Linux drives.

If you have any more issues, feel free to reply and let me know.

ce

which computer should it be installed on?

---

### Post by Dynaflow on 2008-01-18
You're probably looking to set up [SAMBA]("http://en.wikipedia.org/wiki/Samba_%28software%29").  Look here and see if it's what you're after: [https://help.ubuntu.com/community/ComprehensiveSambaGuide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide")

---

### Post by Dynaflow on 2008-01-18
> **sladigar said:**
> which computer should it be installed on?

I think he was under the impression that you're dual-booting.  If these machines are separate units, however, you won't have to worry about that.

---

