---
title: "Triple Booting: OSX/Win7/Ubuntu"
date: 2009-12-27
forum: Apple Hardware Users
---

### Post by morph3k on 2009-12-27
I made 3 partitions.  I have an iMac so OSX is on here by default.  I installed Win7 with no problems.  However, I go through the entire install process for 9.10 and it says it's completely installed however when I reboot and go to choose it it isn't there.  Then when I check the partition it's empty.  I really need some help with this please.

---

### Post by mwolfer1 on 2009-12-27
1) Did you try to boot with the 'Option' key pressed to see all possible boot options?
2) Did you try to use ReFit (a really nice boot manager for Macs) [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
3) Where did you install the boot manager for your Ubuntu partition?

---

### Post by morph3k on 2009-12-27
> **mwolfer1 said:**
> 1) Did you try to boot with the 'Option' key pressed to see all possible boot options?
2) Did you try to use ReFit (a really nice boot manager for Macs) [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
3) Where did you install the boot manager for your Ubuntu partition?

The option key only displays mac and windows.

rEFit also only shows the 2.

when i'm installing ubuntu i have to reformat the partition to ext3 or ext4 because I can only format the to Mac/MS-DOS through Disc Utility.  The GRUB of Ubuntu wouldn't let me boot up OSX and that's when I just had those 2 on there.

---

### Post by morph3k on 2009-12-27
Also when I finish installing it asks me to reboot.  I click reboot it ejects the CD and asks me to press enter to reboot then it says:

"1791.944793 Restarting System" and freezes there.  I have to shut it down by the button.

I installed it this time with GRUB.  Holding down option(alt) gave me a choice between Mac and Windows.  Mac boots fine by default w/o pressing option.

When I select Windows it loads GRUB and within 1 second loads up Ubuntu.  I can't even access Windows.  I had to delete the partition it was on and luckily it didn't corrupt either OSX or Win7.  I think maybe it is just not compatible with OSX and win7?

---

### Post by mwolfer1 on 2009-12-27
Sorry, I didn't ask the right way. 

At the end of the Ubuntu installation process you can select advanced options and can see where the boot loader is being placed - by default into hd0. If you instead select the partition you just installed into (for instance hd0,3) you should be able to see it as a bootable partition with refit. I assume at first boot time  you would need to have refit's partition manager update the settings. 
I got it to work this way on my MacBookPro.

BTW the hangup at shutdown seems to be a feature with Karmic.

---

