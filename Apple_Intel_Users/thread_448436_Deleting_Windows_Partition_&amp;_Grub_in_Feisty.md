---
title: "Deleting Windows Partition &amp; Grub in Feisty"
date: 2007-05-19
forum: Apple Intel Users
---

### Post by eggplant parma on 2007-05-19
Hi,

Apologies if this has been covered elsewhere, but I haven't been able to find this exact scenario explained anywhere and I'm not feeling *too* adventurous just yet...

I've got a Macbook currently dual-booting OS X and XP, and I'd like to replace XP with Ubuntu Feisty. Am I correct in assuming I can just delete the XP partition in Ubuntu's installer and then create two new partitions (root and swap) as normal? [This guide](http://thedarkmaster.wordpress.com/2007/04/06/ubuntu-feisty-beta-on-intel-mac-mini/) doesn't mention a bootloader, so can I presume Grub installs fine in the latest Feisty?

Thanks for any responses.

---

### Post by ronocdh on 2007-05-19
> **eggplant parma said:**
> Hi,

Apologies if this has been covered elsewhere, but I haven't been able to find this exact scenario explained anywhere and I'm not feeling *too* adventurous just yet...

I've got a Macbook currently dual-booting OS X and XP, and I'd like to replace XP with Ubuntu Feisty. Am I correct in assuming I can just delete the XP partition in Ubuntu's installer and then create two new partitions (root and swap) as normal? [This guide](http://thedarkmaster.wordpress.com/2007/04/06/ubuntu-feisty-beta-on-intel-mac-mini/) doesn't mention a bootloader, so can I presume Grub installs fine in the latest Feisty?

Thanks for any responses.
Feisty does add nice GPT compatibility, so you're right on that count. As for nuking your XP partition, I would try first in OS X with the Disk Utility. If that doesn't work due to permissions or something, you can try the GParted live CD, or iPartition, which I hear works better on the Mactels. Last, you should be able to reformat the XP partition from the graphical Ubuntu installer running off the Live CD. You'll have to select that partition, choose "format," then "apply" the changes, and slather the installer with reassurances that you really mean to kill it.

Also, you don't really have to create a dedicated swap partition. Depending on the amount of RAM you have and the programs you typically run, you may be fine without it. (Feisty will ask you about swap space, but will install fine even if you refuse to define any.) If you decide you want it, you can create a swap file after installation; just remember to add that much more space to the partition, e.g. 1GB or 2GB or something.

Good luck!

---

### Post by eggplant parma on 2007-05-19
Thanks, ronocdh.

I'm just burning the AMD64 version now, as suggested by your post in that other thread.

If I don't *need* to specify a swap partition, this just got a lot easier. My previous experience with Feisty was running the beta on 256mb of RAM, so I'm sure 1GB will suffice!

With any luck I'll be posting from Ubuntu next ...

[edit: worked fine! Thanks again. Now to sort out the keyboard and mouse and resolution, oh my...

---

