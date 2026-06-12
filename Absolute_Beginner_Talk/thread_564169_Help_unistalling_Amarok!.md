---
title: "Help unistalling Amarok!"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by stavaroti on 2007-09-30
Hi all,

I would like to uninstall amarok primarily because it didn't work the way i thought it would. Since i am running ubuntu, not kubuntu, the installer installed a whole bunch of dependencies that i definitely do not need, since my ubuntu installation worked just fine without them, now i would like to remove amarok and all the dependencies it installed.

The problem is that when i open up the terminal and type sudo apt-get remove amarok it says that amarok is not installed. If i use the add/remove feature or synaptic, it says that amarok is not installed, but amarok opens up just fine from the applications menu and runs fine.

Is there anyway that i can remove amarok and all the dependencies and kde applications that were installed? Also before trying to uninstall amarok i 'cleaned up' ubuntu using recommendations from this forum [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Any help would be appreciated.


Thanks everybody.

Ubuntu 7.04
Dell 700m intel 1.8Ghz

---

### Post by mikewhatever on 2007-09-30
Try removing Amarok regularly and then run 'sudo apt-get autoclean'. That should get you rid of the dependencies.

---

### Post by stavaroti on 2007-09-30
How do i remove it regularly?  I tried via the terminal, synaptic, and add/remove.  Sorry, but i am a noob so i dont quite know how to remove it regularly.  I originally installed amarok using the following command: sudo apt-get install amarok.  

Thanks for your help.

---

### Post by mikewhatever on 2007-10-01
Try > sudo apt-get remove amarok

---

### Post by dptxp on 2007-10-01
> **mikewhatever said:**
> Try

Please read the OP
This command did not work.

Try autoremove , not remove.

---

