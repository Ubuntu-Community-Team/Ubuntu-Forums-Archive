---
title: "yaboot doesnt´boot ubuntu just macosx"
date: 2005-04-03
forum: Apple PPC Users
---

### Post by bzzzbip on 2005-04-03
Hello!
I´ve just installed macosx and ubuntu on my ibook g4. the first stage of installation seemed to work fine. But when i try to boot linux (choosing "l" from the yaboot menu) nothing happens. I receive a message saying "loading kernel..." or so, and then "l command not found". Surprisingly, if I type x, macosx initializes without problems.
I have to add, that when i made the partitions, i put the ubuntu partition at the begining of the disk. 
Thanks and cheers

---

### Post by Grock on 2005-04-03
Try reinstalling, and print out the partition map here if it still doesn't work.  Ubuntu's handling of yaboot was exceptional in the install phase it found everything.
Maybe it's a partition error.

---

### Post by bzzzbip on 2005-04-04
The partitioning map goes like this:

IDE1 master (hda) 60.0GB FUJITSUMHT2060AT
#1  32.2 kb                            Apple
#2  1.0 MB                             Boot            Boot 
#3  15.7 GB                            Ext 3          Ubuntu        /
#5  512.2 MB                         swap            swap          swap
#4  43.76 MB                          hfs+            apple_HFS_UN
       8.1kb                               Free space

Notes: In the boot partition i´ve chosen "new world boot partition"; and the mountpoint of The ubuntu partition is "/".
Thanks!

---

### Post by bzzzbip on 2005-04-06
I don't know if anybody else has experienced the same.....I turn on the ibook, the yaboot menu appears, if I press "x", the macosx starts, if i press "l" nothing happens and whatever I type, I get a message saying "command not found" .But if I don't type anything on the yaboot menu, and  wait, Ubuntu starts by its own. Is it that the correct proceedure? 
If I turn on the computer pressing alt, I get a graphic menu, that does the same, by default the linux icon is pressed, and the computer starts.

---

