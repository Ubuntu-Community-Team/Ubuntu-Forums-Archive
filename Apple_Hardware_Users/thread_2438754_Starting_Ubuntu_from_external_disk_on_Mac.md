---
title: "Starting Ubuntu from external disk on Mac"
date: 2020-03-17
forum: Apple Hardware Users
---

### Post by dorpapst on 2020-03-17
Hey friends,
Some weeks ago, I installed Ubuntu on an external disk, including a swap partition (if this is important). This external disk also has an external macOS and one other Linux on it, which I do not want to destroy. 
I installed it while using a MacBook and now, if I boot this one, It automatically shows four operating systems:
- the built in
- the three external ones named above

This is correct.

Now, I would like to boot the Ubuntu operating system from a different MacPC for some reasons, but it does not show many any of the three other while booting.

Do I need to configure something here on that external disk? 

I am honestly not sure about this and I am in fear of destroying the other two systems on disk or the starting functionality of the disk on the Pc where it works at the moment.

Is there anybody who can explain me how this works and tell me how I can boot the disk from that second MacPC?

Many greetings and thanks

---

### Post by dragonfly41 on 2020-03-17
Since I have no experience on MacBook I did some digging.

[https://www.quora.com/Why-is-there-no-UEFI-BIOS-setup-for-Apple-Mac-Macbook](https://www.quora.com/Why-is-there-no-UEFI-BIOS-setup-for-Apple-Mac-Macbook)

Sure enough the loader I now use (rEFInd) on my Dell is mentioned in that thread.
The reason your external drive does not boot is probably because the boot info is buried in MacBook1.

If you create a small partition in your external drive (size about 500 MB with boot flags) and install rEFInd *on that external drive*, you should be able to boot with either MacBook1 or MacBook2.  You can also edit refind.conf (as I did on my Dell) to give priority to external device (SSD).

But I would wait until you get other responses from MacBook users and meanwhile just read about rEFInd.

---

### Post by oldfred on 2020-03-17
Do not know Mac either.

But Ubuntu's ubiquity installer only installs grub to internal drive, so you can only boot using internal drive.
You need to add ESP - efi system partition to external drive.

And internal drives all boot in UEFI mode from /EFI/boot/bootx64.efi.
And the full install of grub renamed to bootx64.efi needs to also have /EFI/ubuntu folder. 
You probably can just copy from internal drive's ESP to external drive's ESP. Or reinstall grub to external drive.

---

### Post by dorpapst on 2020-03-20
Hey, Thanks to both of you. It is working now, it really was the missing ESP causing this. 
Thank you! 
Have a wonderful day.

---

### Post by slickymaster on 2020-03-20
*Thread moved to **Apple Hardware Users**.*

---

