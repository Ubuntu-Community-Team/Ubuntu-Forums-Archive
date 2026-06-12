---
title: "Uninstalling"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by CuriousTeen on 2007-04-06
Hi.

sorry. can u anyone send me a link on how to installed Ubuntu from my external 3.5" HD?

I don't know how to use linux. 

Thanks

---

### Post by xopher on 2007-04-06
Im not sure what you want, could you be more specific, thank you.

---

### Post by carverj on 2007-04-06
Just download the alternate CD from the ubuntu.com site.
Make sure when you boot that CD is first in the boot order in your BIOS settings.
Press enter to install. Follow the prompts.
Good luck and have fun

---

### Post by gimfred on 2007-04-06
I'm sorry, I didn't understand. :) 

Did you wish to
1. install Ubuntu on an external hdd 
2. uninstall Ubuntu which is on an external hdd? 
3. Is there a third option that you would like to do?

---

### Post by spinflick on 2007-04-06
If you downloaded to your external hd you can make a cd from there, reset your bios so cd boots first, put in your cd and install.
I hope that's what you meant? :)

---

### Post by CuriousTeen on 2007-04-06
sorry.

I mean how to uninstall.


tks

---

### Post by carverj on 2007-04-07
Oh, uninstall is not much different.
You simply install the operating system you would like to use right over the top.
Formatting a disk is often a step in installing an operating system.
Have fun!!

---

### Post by Ethangar on 2007-04-07
I'm curious about this to. 

I installed ubuntu on my old computer. It sat comfortably on its own drive. When I got the new machine I pulled some hard drives to put in this one. One of them was the Linux drive. When I went to format the old one all I got was GRUB load errors and the bootup stopped. I ended up after hours of searching and swearing found a post that said to use fdisk /mbr to get rid of the grub loader. Since it was a total re-install by that point it didn't matter at all to me. But I want to put Ubuntu on this one and don't want any surprises if at some point I have to un-install it. 

Will putting in the live CD lead to a clean uninstall? 
Will the partitioning tool let me join the linux partitions back to my windows drive or will I be left with 2 blank partitions?

Any help would be appreciated.

---

### Post by CuriousTeen on 2007-04-19
> **carverj said:**
> Oh, uninstall is not much different.
You simply install the operating system you would like to use right over the top.
Formatting a disk is often a step in installing an operating system.
Have fun!!

Do u have guide on how to uninstall Ubuntu 6.1 from my external HDD?

I afraid one mistake will cause my computer cannot start-up properly.

Thanks

---

### Post by CuriousTeen on 2007-04-20
Can anyone teach me to uninstall ubuntu pls?

Desperate to remove it.

Tks

---

### Post by Seisen on 2007-04-20
Is Ubuntu the only OS installed on the external harddrive?

---

### Post by CuriousTeen on 2007-04-20
> **Seisen said:**
> Is Ubuntu the only OS installed on the external harddrive?

External Drive total got 160GB, I use a partition program to separate to 130GB for Windows Backup and 30GB for Ubuntu.

---

### Post by JT673 on 2007-04-20
Use the partitioner to wipe out the Ubuntu partition (filesystem: ext3) and resize the Windows (filesystem: ntfs/fat) one.

---

### Post by loanrangie on 2007-04-21
> **JT673 said:**
> Use the partitioner to wipe out the Ubuntu partition (filesystem: ext3) and resize the Windows (filesystem: ntfs/fat) one.

 Do you delete the partitions that were used for Ubuntu ?  i went as far as confirming partition format but didnt want to go further in case i wiped my xp install by mistake.

---

### Post by jiminycricket on 2007-04-21
You also need to do fixmbr from a Windows XP recovery console in order to restore your boot MBR.

BTW I think your sdb problem is fixed in Feisty Fawn, CuriousTeen.  It uses libsata instead of libata, so there's no hda or hdb anymore, only sd*.

---

### Post by loanrangie on 2007-04-21
I deleted  the ext3 and swap partition but now i cant boot into windows as there is no grub installer and all i get is 'error 22' ?

---

### Post by jiminycricket on 2007-04-21
You need to run fixmbr from your XP recovery console, or a bartpe cd.

---

### Post by Tundro Walker on 2007-04-21
Wanted ot detail this out more in case you're iffy on using the Windows Recovery...

After wiping out Ubuntu partition, you resize your leftover Windows partition to be the whole drive, like Jiminy said.

Then, when you boot, go into your BIOS, and set it to boot from CD first, and HDD 2nd.  

Insert your Windows CD, save the BIOS settings and reboot.

When the boot screen shows up, you should get some options, one of which is to boot into "Recovery Console".  Select that one.  It usually takes a few minutes to come up.

In the recovery console, you should be at a prompt that lets you type in system admin commands, one of which is FIXMBR (again, pointed out by Jiminy).

This should wipe GRUB from the Master Boot Record of your drive and replace it with Window's bootstrapper.

Once it's done running, remove your Windows CD and reboot.  It should skip CD booting (no CD), and check the HDD, where it should find the fixed MBR and boot to Windows.

It should all go well.  With it done, you can set your BIOS to boot from HDD 1st, and CD 2nd.

---

### Post by antoz on 2007-04-21
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You will find all your answers in the above link,A

---

### Post by carverj on 2007-04-24
Oh, so you mean that you installed Ubuntu on an external hard drive and now you would like to have
that space back for regular storage?
What I would probably do is run the live CD in rescue mode (from memory, type just type rescue at boot prompt) , and use fdisk from the command line. Please give some more information about exactly what you are trying to do and wait for advice, there is no such thing as a stupid question here!!
Be carefulo with important data. Always back up first, no matter how long it takes!
Good luck

---

### Post by carverj on 2007-04-24
Sorry, ignore post above. I didn't see that the thread continued to page 2 so was answering question
from a week ago that has since been answered.

---

