---
title: "Unable to start Windows XP after Unbuntu install"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by raul99 on 2006-01-04
Tonight I installed ubuntu on my machine for the first time.It was installed to the first partition of a second HD that held no other data. Windows Xp was on the first HD. The install went well and I am able to select a working Ubuntu 5.10 from the grub boot loader. However when I try to select Windows Xp from the loader I get a black error screen informing me that "windows did not start sucessfully and that a recent change in hardward or software might have caused this" I am given options of restarting windows in the following fashions:
Safe mode
Safe mode with networking
Safe mode with command prompt
Last known working configuration

any and all of these choices result in a blue error screen. Any suggestions for help. The only error I can think of was failure to disable "go back program prior to install. Is it possible to remove the grub loader from the Windows HD via the ubuntu OS?
Thanks

---

### Post by dickohead on 2006-01-04
Try booting just the windows drive without the Ubuntu one attached, It may just be a hardware conflict.

If you can boot windows with the ubuntu drive disconnected then we know it's not windows.

But if you still get the same error then you've got a windows problem with your hardware.

You can remove the GRUB boot loader all together, but if windows is still toast you will need to know how to re-enable it first - so before you disable it, make you know how to re-enable it!

---

### Post by raul99 on 2006-01-04
When I disconnect the second Hd ( the one containing linux) I get a graphic of a receding " go back " bar followed by black screen, Go Back internal Error, press any key to reboot. I am unable to acess Safe Mode at bootup via F8

---

### Post by raul99 on 2006-01-04
Do you think a reinstall of windows would be helpful or even possible on the first HD?:confused:

---

### Post by Sef on 2006-01-04
Yes a reinstall is possible, but you'll need a linux boot disk to reinstall GRUB.

---

### Post by daki on 2006-01-04
Sorry to hear about what happened.  The install on the first drive is possible, just be aware that the win xp install overwrites your master boot record, which would basically overwrite grub, so you wouldn't be able to boot ubuntu anymore.  Well you could, but it wouldn't be as easy, since you wouldn't get the option screen like you do now, but it would just boot xp.  So, after you get xp installed, what you will need to do is rewrite grub to the mbr.  You can do this by running the command grub, and once in their, run root(hd1,x) where x is the partition of your boot partition minus 1, or if you didn't create a boot partition, then it will be just the same as the root partition.  For example, if your boot directory is located on hdb1 (I assume it's not hda, since you said it was your second hard drive) then it will be root (hd1,0).  After you issue that command, you will need to issue the setup (hd0) command.  Then the quit command, to exit the grub setup.  This will rewrite the mbr, and you will have your bootloader when you turn on your computer again.  Hope this helps.

---

### Post by daki on 2006-01-04
Oh, and like Sef said, you will need a linux boot disc before you can actually issue these commands.

---

### Post by raul99 on 2006-01-04
Thanks for all the help, tonight I will try to reinstall windows on Hd0, if sucessful I will be able to get my data from that drive and back it up. 
worse case will by reinstall of ubuntu to Hd1. will post results

---

