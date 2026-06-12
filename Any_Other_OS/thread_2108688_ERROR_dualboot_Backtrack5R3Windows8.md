---
title: "ERROR dualboot Backtrack5R3/Windows8"
date: 2013-01-25
forum: Any Other OS
---

### Post by bayjay on 2013-01-25
Hello friends,

I have an new SONY-VaioSVE1512E6EB-Laptop with Windows 8 64 bit. Yesterday I burned a Backtrack5R3-KDE-64bit-iso LiveCD. In the BIOS I changed the bootoption from UEFI to Legacy, so I could boot from this iso-CD. When I booted in Backtrack I wanted to install it. I choosed "Install them side by side, choosing beetween them each startup" and I gave 50 GB for Backtrack. I installed it and everything worked perfect. I rebooted and then there where 6 options to choose:
```
Ubuntu, with Linux 3.2.6
Ubuntu, with Linux 3.2.6 (recovery mode)
memory test (memtest 86+)
memory test (memtest 86+, serial console 115200)
Windows Vista (loader) (on/dev/sda2)
Windwos Vista (loader) (on/dev/sda3)
```
There is "Windows Vista" but I choose Windows 8 !?!? Anyway, when i choosed one of the Windows-Vista-Items (I tried both), there was an ERROR-Message:
```
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem

1. Insert your Windows installation disc and restart your computer
2. Choose your language settings, and then click "next"
3. Click "repair your computer"

If you don't have this disc, contact your system administrator or computer manufacturer for assistance.

File: \Boot\BCD
Status: 0xc000000e

Info: The boot configuration data for your PC is missing or contains error.
```
Is there any way to get my new Windows 8 back? I have many high-payed license-programs like Microsoft-office-2010 on it. It makes me really sad, when I think about this:-( Please help me.

Thank you so much for your help,

Ben

---

### Post by oldos2er on 2013-01-25
Moved to Other OS/Distro Talk.

---

### Post by oldfred on 2013-01-25
You cannot chain load from a BIOS install to a UEFI install or vice-versa. And I doubt if Backtrack has a UEFI with secure boot capability. It may have a UEFI capability.

        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

---

### Post by bayjay on 2013-01-25
Before I booted the Backtrack Live CD I disabled secure-boot. What do I have to do to get my Windows8 back?
Thanks

---

### Post by oldfred on 2013-01-25
You should just have to boot in UEFI mode from UEFI menu. Should work with secure boot on or off. If you are going to install anything else make sure you have turned fast boot off. Some computers can only get to UEFI menu from Windows with fast boot on.

If still issues from UEFI menu:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bayjay on 2013-01-25
But how do I get Windows8 back? How do I get in UEFI Menu? I turned UEFI off and turned it to Legacy before I installed Backtrack. How do I turn off fast boot? Sorry...I am completely new in Ubuntu. It is the first time I use it! But thank you so much for your help.

---

### Post by oldfred on 2013-01-25
Every system varies, but Microsoft documented the most common. Otherwise look at your system manual or vendors documentation on line.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Do you get a grub menu. They recently added anew entry at the bottom that should let directly load to UEFI menu.

---

### Post by bayjay on 2013-01-26
Hey I solved it! I had to boot in the bios and chnge the boot-mode again from legacy to UEFI. Then Windows8 started again. Thank you!

---

