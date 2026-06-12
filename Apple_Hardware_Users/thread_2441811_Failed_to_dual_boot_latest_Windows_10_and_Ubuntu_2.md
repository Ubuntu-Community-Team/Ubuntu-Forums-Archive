---
title: "Failed to dual boot latest Windows 10 and Ubuntu 20 LTS on 2015 Macbook pro."
date: 2020-04-27
forum: Apple Hardware Users
---

### Post by flyingosprey on 2020-04-27
Are there anyone who can dual boot latest Windows 10 and Ubuntu 20 LTS on 2015 Macbook pro?

This is what I did:

1. Create a Windows 10 USB GPT stick.
2. Create a Ubuntu 20 GPT stick.
3. Boot with Windows 10 stick. Clean partition table, using diskpart. Install Windows 10 on 1st 100GB. (Windows 10 creates EFI and system partition before this 100GB automatically.)
4. Boot with Ubuntu 20 stick. Create 8GB swap in the end of the disk. Install Linux on the space left. Grub is the installed to the disk, not to a partition.

After installation, Ubuntu 20 can boot/load, while Windows 10 cannot boot/load.

I've done this multiple times to dual boot Windows 10 and Ubuntu 16 LTS (did not try Ubuntu 18 LTS) in the past. So I think my steps are correct.

On the other hand, I can dual boot Windows 10 and Fedora 31 with same steps. (But I don't like Fedora because it does not provide LTS version. Too much upgrade.)

Really stuck. Any suggestion? Thanks.

---

### Post by wildmanne39 on 2020-04-27
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by oldfred on 2020-04-27
Do not know Mac.

But is Windows fast start up off? Note what Windows will keep turning that back on with updates.

Those that know Mac may want more details.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by gsahli on 2020-04-28
I've recently used boot-repair. It's great and is the easiest way. So follow oldfred's advice. And tell us if it works.

BTW - does the Mac built-in bootloader allow you to boot linux? (holding "option" at startup)

---

### Post by oldfred on 2020-04-28
I have seen a lot of users with Mac use rEFInd.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) &
[https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions](https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions)

It is a fork of refit.
And Mac used UEFI long before Windows, so now some with PC use rEFInd. 
I found rEFInd a good emergency boot loader as it found all my installs and offered to boot them. 
So I have a couple of my so old as to be too small for just about anything, used a rEFInd emergency boot flash drives.

---

### Post by flyingosprey on 2020-04-29
Yes I can boot linux. After grub, windows cannot load.

---

### Post by flyingosprey on 2020-04-29
Install rEFInd on linux, however rEFInd same as grub cannot load Windows.

---

### Post by oldfred on 2020-04-29
Does Boot-Repair's report work on your Mac?
Run report if so.

---

### Post by gsahli on 2020-04-30
You didn't say, so I ask -
Did you run sudo update-grub again to see if grub could find Windows and create a boot menu that has a Windows choice?

---

