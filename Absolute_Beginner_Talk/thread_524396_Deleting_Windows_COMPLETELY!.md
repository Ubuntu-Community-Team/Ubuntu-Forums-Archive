---
title: "Deleting Windows COMPLETELY!"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by sachill on 2007-08-13
Hi

I am so happy with Ubuntu that I no longer need Windows.  Is it possible for me to delete the Windows partition and give all that space to my already existing Ubuntu partition with reinstalling Ubuntu on the ENTIRE harddisk which is what I now want??

Thanks

---

### Post by Kobalt on 2007-08-13
It is [possible]("https://help.ubuntu.com/community/HowToRemoveWindows").

---

### Post by sachill on 2007-08-13
Thanks, although that link, with its clear warnings (!) only seems to show how to REDUCE the size of Windows....can I not delete it entirely?

---

### Post by Hopeless on 2007-08-13
download gparted live cd... worked for me...

\\:D/

---

### Post by AtrejuT on 2007-08-13
I think this should be easy to do from either an Ubuntu LiveCD or the suggested gparted live CD.
Just boot one of these, run gparted, select your windows partition and delete it with the right mouse button - context menu - delete. 
Then select your ubuntu partition, choose 'resize' in the context menu and stretch it to cover the whole disk.

The warnings given in the link above should not be taken too lightly, messing around with your partitions is always dangerous but usually works fine.

---

### Post by Kobalt on 2007-08-13
You can follow AtrejuT's advice to remove your windows partition, but if you're that happy with Ubuntu then I suggest you use your spare space to [make a separate Home partition]("http://psychocats.net/ubuntu/separatehome"). This way you'll keep all your personal data and settings safe from a system crash. you'll be able to reinstall Ubuntu (or any Linux distribution) without losing them. With Gutsy coming, I think that would be a fine idea...

---

