---
title: "Remove grub bootloader /fixmbr and /fixboot not doing anything"
date: 2014-06-28
forum: Any Other OS
---

### Post by Ryan_ on 2014-06-28
I tried out Ubuntu on a dual boot and i decided dual booting was not working for me, so i'm trying to remove it and get back to normal. So i followed a few tutorials online and deleted the swap and ubuntu partition, and then I make a recovery USB using windows 8's 'Create a Recovery Drive' tool, and then restarted my computer. Upon booting, i was greeted with Grub's command interface. Unsure what to do, i googled it and someone suggested using the exit command and i was brought to a screen where i could choose different devices to boot from, i tried the windows bootloader option, and that worked, I tried the Ubuntu option and that brought me back to the grub command line, and i tried the USB option and that brought me to a recovery screen for windows where it asked me to choose a language just like in the tutorials. The part that is different and i don't understand is on the tutorials, the next screen is always where it gives you an option to install windows 8 or repair windows 8. I don't get that option. For me, it is either troubleshoot or continue to windows 8. In the troubleshoot menu, i found my way into the command prompt just like in the tutorial, and executed ```
bootrec.exe /fixmbr and bootrec.exe /fixboot 
``` both of these said they were successful, so i exited out of the command prompt and clicked continue to windows 8. Doing this brought me back to the grub command line. I tried restarting my computer to see if that would work, but it too brought me to the grub command line. What am i doing wrong and how can i fix it? I want grub bootloader gone and for my computer to boot into windows normally.
Any help or suggestions is greatly appreciated. Thanks.

---

### Post by oldfred on 2014-06-28
Did you run Boot-Repair's rename or buggy UEFI fix?

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

If that is not the issue, run the BootInfo report and post link.

---

### Post by Ryan_ on 2014-06-28
Do i need to be ubuntu for the Boot-Repair to work?

---

### Post by oldfred on 2014-06-28
You can install Boot-Repair to Ubuntu or Ubuntu live installer or download a CD Lubuntu based Boot-Repair.

---

### Post by Ryan_ on 2014-06-29
Ok, i will try boot repair in the morning.

---

### Post by Ryan_ on 2014-06-29
ok, so i put the boot-repair on a bootable usb using unetbootin and when I booted from the usb, grub came up asking what i wanted to boot into, and i chose the boot-repair option (the only option) and then the screen went black. It stayed black for 30 mins until i held down the power button to turn off my laptop. Why did this happen and how can i get it to boot? Is it because i deleted my ubuntu partition? Do i need to re-install ubuntu to get this to work? I just want grub gone and my laptop back to normal, so i would rather not re-partition my hard drive and re-install ubuntu. Any suggestions? Thanks.

---

### Post by oldfred on 2014-06-29
What video card?
Did you have video issues with the original Ubuntu installer? If not may be better to use it as it is a newer version and works better with many new UEFI systems.

You may need nomodeset or other boot options.

At grub menu, press e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

### Post by Ryan_ on 2014-06-29
I have an nvidia GeForce GT 750M. No, i didn't have any problems with the original Ubuntu Installer. I will try your suggestion.

---

### Post by Ryan_ on 2014-06-29
Replaced quiet splash with nomodeset, pressed f10 to boot and the same thing happened. Black screen. If im trying to use the live usb for boot-repair I don't need ubuntu installed do i?

---

### Post by oldfred on 2014-06-29
No you should not need Ubuntu installed.

Is this a dual video system? Or does it actually boot with Intel video?
Then nomodeset usually does not work, but you need different boot parameters.

What system, model is this?

       Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Ryan_ on 2014-06-30
This is an Alienware 14. I tried the boot options that you linked and they did not work either. Any other ideas? And thank you for the help so far, I appreciate it.

---

### Post by oldfred on 2014-06-30
Different model but it may have some of the same issues?
        
 [SOLVED] UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

And some of the issues here they say apply to all Intel based systems.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

---

### Post by Ryan_ on 2014-06-30
Looked at the links and checked to make sure i had the 64 bit iso and i did, also wiped the live usb and put the iso on it, and I tried a different USB port. Unfortunately none of these things fixed the problem. Is boot-repair the only way to go about fixing my issue? Because it seems like it isn't going to boot successfully. Any other suggestions?

---

### Post by oldfred on 2014-06-30
Is it booting with nVidia which works with nomodeset or with Intel video chip which usually needs different boot parameter?
Some systems let you set which video mode you boot with, others are muxless or automatic?
       Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

