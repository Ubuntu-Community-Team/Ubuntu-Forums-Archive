---
title: "Ubuntu on Macbook questions..."
date: 2006-10-02
forum: Apple PPC Users
---

### Post by newbie builder on 2006-10-02
I've got a macbook that is currently set up to dual boot with windows XP but I'm finding I really don't even need XP for work related stuff and I want to get rid of it....and replace it with ubuntu. I've downloading all the files, but want to make sure I do it right before I install everything. I already have a 7.5 gb partition that I'd made for windows, so when I put in the ubuntu CD will I be able to say erase and use that partition? My other question is about the actual booting- I've downloaded rEFIt but when it says to, "Drag the efi directory from the disk image to the root of your MacOS X drive." I don't know where the root of the Osx drive is.
Thanks for the help on the newbie questions- just don't wanna mess it up.

---

### Post by undead-monkey on 2006-10-02
Ok, with ReFit, the root would be the first window you see when you click on your HD (contains your system, applications, users folders.)

as for your windows partition, when you come to installing ubuntu, you can delete your windows partition, then back track a window or two and install "on largest free space" which is where windows once was.

---

### Post by newbie builder on 2006-10-03
Thanks very much for that. Now I've got everything ready to go and I've downloaded the files, but when I try to burn it onto a disk it says "Unable to burn 'ubuntu-6.06.1-desktop-i386.iso'. not recognized."
Then when I try to burn it not using disk utility, it says the file is to big for a 700mb CD-R.....
What'd I do?

---

### Post by mikkas on 2006-10-03
I burnt my image in Windows XP with Nero.. It did fit on a CDR 700.. Um, maybe try that. I'm sure someone else will reply if you can wait, with a linux solution though.

---

### Post by newbie builder on 2006-10-03
Well I re-downloaded it and have now succesfully burned a disc- time to try it out. I'll post back with the results.

EDIT:
It worked to boot from the disc, but when it said "boting the kernel" I got an error....."Kernel Panick: Not Syncing" and MP-Bios Bug: 8245 timer not connecting."

Any ideas?

---

### Post by undead-monkey on 2006-10-03
You will get kernel panics from time to time during boot, just restart, mabey more than once, and it should work.

---

### Post by hajk on 2006-10-03
There's lots of info in these forums on how to install Ubuntu to the HD, for example my notes on it (see sig). In your case, once you start the installer, first delete the Windows NTFS partition to get unallocated space, then back up two pages and install Ubuntu in the largest unallocated space. There will be problems with Grub not working, but you can use LILO instead.

It all works fairly well, except for wireless which doesn't come up automatically and requires annoying handtuning every time you boot. The problem is in the new madwifi-ng drivers. I got so fed up with it that I have now switched to installing Ubuntu in a Parallels VM running under OS X.
Anyway, you decide for yourself.

---

### Post by newbie builder on 2006-10-05
hajk- thanks for the help.
I printed out the the notes in your isig and had one question- what does it mean to "uncomment the varoius lines for the universe repository"? I got to that point in the installation but didn't know what that meant so I had to stop since my interenet also wasn't working.......

---

### Post by hajk on 2006-10-05
> **newbie builder said:**
> hajk- thanks for the help.
I printed out the the notes in your isig and had one question- what does it mean to "uncomment the varoius lines for the universe repository"? I got to that point in the installation but didn't know what that meant so I had to stop since my interenet also wasn't working.......

A comment in the /etc/apt-get/sources.list file is any line starting with #, so to uncomment such a line means to remove that token.

Internet not working? That is probably the wireless interface giving problems. There are some suggestions later in my notes as to how to deal with that -- the problem is in the madwifi-ng drivers (in the restricted-modules package matching the kernel version).

---

