---
title: "SSD Dual Boot Win7 - Ubuntu 12.04 weird issue"
date: 2013-05-01
forum: Any Other OS
---

### Post by HughJorgen on 2013-05-01
Hi,

I am having the "error: no such partition. grub rescue>" issue with a dual boot installation on an intel 520 series 120GB SSD.



[LIST=1]
[*]The SSD has been securely erased using intel's SSD toolbox (on another PC). 
[*]GParted was used to create two partitions.  (I have also tried it with three, manually creating the swap partition). 
[*]Windows 7 Ultimate 64-bit was installed.  No issues. 
[*]System was rebooted.  All good. 
[*]Ubuntu 12.04 (also tried it with 12.10) 64-bit was installed from CD/DVD. 
[*]No issues until restart, where I was confronted with the dreaded **"error: no such partition. grub rescue>"** message. 
[*]I power down the laptop and power it up. 
[*]I am then greeted by the familiar Grub screen and can boot into Win 7 or Ubuntu.  Huh??? 
[*]Restarting (without powering the system down) from either Ubuntu or Win 7 gives the **above** mentioned error.  **Powering down** and back up gives no problems.  Very strange. 
[/LIST]

I have searched for solutions but have not been able to sort this problem.  I have performed the install a number of times but to no avail.

**The strange thing is, I have already performed the install - Win 7 and Ubuntu 12.10 - on the same PC (wife's laptop) with its original Fujitsu mechanical HDD and it worked perfectly!**

Is this purely coincidental or is there something that I am missing when it comes to dual booting with an intel SSD?

Any help would be greatly appreciated.


Thanks in advance.

[Edit] Please note: This is an older dual core HP laptop.  It's not a UEFI Bios if that makes any difference. [/Edit]

---

### Post by oldfred on 2013-05-01
Grub often defaults to install to sda, is sda the SSD? If not change boot in BIOS and see if it boots.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by HughJorgen on 2013-05-02
Thank you for your prompt reply.

This is what I get when I run boot-repair:

[http://paste.ubuntu.com/5625589/](http://paste.ubuntu.com/5625589/)

I then attempted the recommended repair and got this:

[http://paste.ubuntu.com/5625597/](http://paste.ubuntu.com/5625597/)

but the problem persists.  I ran it once more and got this:

[http://paste.ubuntu.com/5625615/](http://paste.ubuntu.com/5625615/)

Still no joy.  Of course, everything is fine if I power down the laptop and then power it up.  It's just those blasted restarts that give the same error message.


Many Thanks.

---

### Post by oldfred on 2013-05-02
I do not see anything wrong. So it does boot from a cold boot just not a warm reboot? Seems like BIOS setting.

Some old BIOS seemed to only boot systems in the first 137GB and some newer now seem to be similar but 100GB.
Do you have BIOS set to AHCI, not IDE nor RAID. If you do not have AHCI at least LBA or large.

---

### Post by HughJorgen on 2013-05-03
oldfred, you're a genius!

Thank you very very much for taking the time to help.  It is very much appreciated.

It was exactly as you suspected.  The BIOS setting "Hard Disk Translation Mode" was set to Bit-Shift.  The only other option on the laptop was LBA-assist.  Once I changed it to LBA-assist and did a clean install of Win 7 and Ubuntu 12.04, everything was fine.

The only difference here that caused the error was going from an 80GB Fujitsu mechanical drive running dual boot perfectly to an intel 520 series 120GB SSD.  Now all runs well on the SSD.

Once again many thanks for your help.

---

### Post by oldfred on 2013-05-03
Glad you got it working, bit-shift is a new one to me.

It was my understanding that you needed AHCI for trim to work. But you may want to look into fstrim and a cron task. Not sure about Windows and SSDs.

  trim does need ahci in BIOS
kernel version >=2.6.33. It does not work with ext3; (10.04 was 2.6.32)

   fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by crjackson on 2013-05-05
I think Intel just posted a firmware upgrade for your drive too.

---

