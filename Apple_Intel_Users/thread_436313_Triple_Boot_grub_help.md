---
title: "Triple Boot grub help"
date: 2007-05-07
forum: Apple Intel Users
---

### Post by AWerner32 on 2007-05-07
Using a first generation macbook 2 ghz core duo and two gigs of ram. I, using boot camp, installed vista business. a few weeks ago i using diskutil i made space for a ubuntu partition. Also i have rEFIt installed. After installing ubuntu when i go to windows it takes me to the grub loader but the vista  loader fails to load vista.

---

### Post by benanzo on 2007-05-07
did you run the partition tool at the rEFIt menu?  I think your MBR and GPT tables are different.

---

### Post by AWerner32 on 2007-05-07
under the gpt list there is normal data at the end which ought to be my windows partition but is absent on the mbr list what does this mean and how can i remedy this? thanks

---

### Post by ronocdh on 2007-05-07
> **AWerner32 said:**
> under the gpt list there is normal data at the end which ought to be my windows partition but is absent on the mbr list what does this mean and how can i remedy this? thanks
Well I recall that in XP (I don't use Vista) that it was possible to insert the installer disc and type "fixmbr" or something to that effect; however, I believe this would remove Ubuntu from your MBR, requiring you to boot into the live CD and edit the GRUB file again. 

=/ I think that might be going in circles. Have you found triple booting guides for OS X/Ubuntu/Vista? Surely any would address this issue.

---

### Post by AWerner32 on 2007-05-09
It appears that the Ubuntu install deleted the MBR of the vista partition does anybody have any idea how to remedy this?

---

### Post by ronocdh on 2007-05-09
As per my post above, I believe it is possible to repair the MBR with the installation disc for Vista.

The specific command was **fixmbr** in XP, IIRC.

---

### Post by jsc1959 on 2007-05-12
I ran into the exact problem you did. You need to reboot off of the vista cd and run repair. It will fix the booting problem for you. Then either reinstall ubuntu and specify your ubuntu partition as the root partition for grub using the advanced menu on the very last step... IE for mine i specified (hd0,4) which corresponds to sda3. Or run grub and reinstall grub to sda3 prior to fixing vista and it should work fine. I never did figure out how to get grub to work well with refit though. Grub hangs up alot ... but it still boots ubuntu using the default settings... oh well.

---

