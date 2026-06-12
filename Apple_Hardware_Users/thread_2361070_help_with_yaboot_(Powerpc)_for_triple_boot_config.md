---
title: "help with yaboot (Powerpc) for triple boot config"
date: 2017-05-11
forum: Apple Hardware Users
---

### Post by gsahli on 2017-05-11
I have a MDD 1 GHz powermac with Tiger installed on sda, Leopard on sdb, and ubuntu MATE 16.04.2 on sdc. I am unable to get the yaboot config set to be able to boot into sdb (Leopard) from yaboot.
If I go to Mac side System Prefs > Startup disk, the Tiger and Leopard start options are available (but not ubuntu in this case).
If I go into Open Firmware, I can boot into sba or sdb using the full paths to the BootX loader.
If I hold Option key after gong sound, I get all 3 drives available to choose and boot.
But if I enter the sdb (Leopard) full path in the yaboot.conf file and do ybin, when I startup and press the x for macosx (second Macos choice in the yaboot selector menu), it just jumps back to the yaboot selector menu.
Any ideas, please?

---

### Post by walterav on 2017-05-14
Forget yaboot for chainloading I'm not saying its impossible but it didn't work for me. The trick is to use a openfirmware based bootscript thats the thing that gets installed and even loaded before yaboot when booting ubuntu on a ppc. In this script you can edit in text style additional openfirmware boot devices/partitions aka "zip / ultra1/ultra0 hd0:,\\tbxi etc" with a timeout and a asci art logo. This will let you boot OS 9, OS X or linux from any disk/partition from that menu.

Its even possible to have this bootscript being selectable in "System Prefs > Startup disk" by blessing that file (probably is already) and adding some additional empty files/folders on the yaboot/linux boot partition resembling a Mac OS X install, like adding "mach_kernel" and "/System/Librarby/CoreServices".

Sorry I couldn't be more specific since I did it a while ago on a G3 BW, but now there is a G4 waiting for me and will update here as soon as that one is working.

---

### Post by gsahli on 2017-05-14
yaboot is itself an open firmware boot script generator, so that sounds do-able. Let me know if you find a template.

---

