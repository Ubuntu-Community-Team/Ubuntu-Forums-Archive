---
title: "mount hfsplus partition in rw mode"
date: 2008-10-06
forum: Apple Hardware Users
---

### Post by vanwarantion on 2008-10-06
i saw some threads saying current kernel doesn't have journaling support for hfsplus.

My problem is i am not able to boot into osx now. I have to edit some files in hfs partition.

Is there any way (or tool like "*$ sudo diskutil disableJournal force /dev/somedisk*") to stop hfs journaling under ubuntu?

---

### Post by cyberdork33 on 2008-10-06
> **vanwarantion said:**
> i saw some threads saying current kernel doesn't have journaling support for hfsplus.

My problem is i am not able to boot into osx now. I have to edit some files in hfs partition.

Is there any way (or tool like "*$ sudo diskutil disableJournal force /dev/somedisk*") to stop hfs journaling under ubuntu?
not that I know of, but you might be able to from the OS X install dvd... of course you might be able to just edit the files from there too.

---

### Post by vanwarantion on 2008-10-06
actually i am using an osx86 and i was able to boot into command line to fix my issue with Boot.plist file..
i was also surfing on kerneltrap.org and google for development news about hfsplus rw support but i think i dont know where to look..

anyway.. is there anything i can do to reach my hfsplus partition with write access?

---

