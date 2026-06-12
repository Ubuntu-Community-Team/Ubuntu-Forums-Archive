---
title: "Completely successful install - almost"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Damo1976 on 2007-03-26
Hi Guys,

Thanks to all the help from you all I haev (on my third attempt) managed wha seems to be a very successful install.
I have now got my ATI X1800 card working, wireless, etc.

All that is left is the process of transfering all my work from the Windows partition to to Linux.

On setting up all my files were visible, but read only.
I saw a programme on Synaptic which was supposed to allow read and write access to ntfs discs.
It did something to the mounting of the disks (not sure what), and the upshot is that all my stuff has vanished from view. 

I can still boot into Windows, but just can't access that partition anymore from Linux.

My plan is to begin by using Outlook either in VMWare or Wine, then migrate fully later on.

I also want to run MS Office in Linux, just for those one or two things I haven't found in OO yet.

SO... I need a programme name or instruction to allow me to see and hopefully edit all my old stuff.

Any suggestions?

Damo

---

### Post by docshawnc on 2007-03-26
hmmm, I'm guessing the prog that you got via syanptic was call ntfs -3g?  If so, did you edit your /etc/fstab?  If so, what is in it? (type cat /etc/fstab and post)

---

