---
title: "How to start Gparted Live on a USB from Xubuntu on Mac 3.1"
date: 2016-01-02
forum: Apple Hardware Users
---

### Post by ineuw on 2016-01-02
Installed Xubuntu 14.04.3 desktop version on a newly installed SSD on a Macbook 3.1. (Trim was installed through Mac earlier, before I replaced the Hitachi drive ),  Only the 32bit Xubuntu OS version was recognized but this is fine with me.

Studied all the instructions relating to the installation for this model MacBook. Created a 100MB /boot/efi partition as demanded by the installation, (formatted as FAT32), and selected GPT as the partition table. In the end I didn't have to go through any special re-configuration after installation. Xubuntu boots, (fast) reboots and shuts down without any problems and all the installed software functions perfectly well. 

However, I wasn't comfortable that everything went so smoothly, and wanted to understand what I did, so ran Boot repair from within Xubuntu and these are the results: [http://paste.ubuntu.com/14364911/](http://paste.ubuntu.com/14364911/) 

My concern is with this line: WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Also, I have no clue when installing CPU or System related software, whether to choose 32bit or 64bit?

Finally, created a GParted live USB key but I have no idea which keys do I use to select the USB on boot.

Thanks in advance for any replies that would help me move on.

---

### Post by Elishasmantle on 2016-01-03
Hello,

From a quick search to boot from USB you " Simply reboot your Mac and hold the **Alt/Option** key on your keyboard as soon as you hear the Mac&#8217;s startup chime. "
The WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted I would ignore at this time since you are now going to use the gparted usb to manage/partition the drive.
From my experience 64bit has newer better features, but mostly why I choose it is because performance is better whether on a physical drive or a VM I am always a lot happier with 64 bit.

---

### Post by ineuw on 2016-01-03
Elishasmantle, thanks for your reply, but I detailed everything in my first post. The Alt/Option no longer does anything. The laptop has no relationship to the MAC OSX because the hard disk was removed. This laptop was intended to be dedicated to Xubuntu only. As for the 64bit Installation USB, it was not recognized by the firmware, but did recognize the 32bit Installation USB immediately through EFI. All my ISO's are checked with MD5 and they are OK. The laptop would not recognize a 64bit Boot Repair USB either.

---

### Post by gedakc on 2016-01-03
I believe that 32bit Xubuntu uses the older BIOS boot and MSDOS/MBR partition table scheme, and 64bit Xubuntu uses the newer UEFI boot and GUID partition table (GPT) scheme.

If the disk originally had a GPT, then likely there is still an old copy of the GPT at the end of the drive.  To remove the old GPT data, see [Wiping Out Old GPT Data]("http://www.rodsbooks.com/gdisk/wipegpt.html").

---

### Post by ineuw on 2016-01-03
gedakc, thanks for the reply. As I mentioned earlier, the SSD was straight out of the box, a 120GB Patriot LE. There was nothing on it, in fact when I plugged it in the first time, Macbook didn't recognize it. I had to update the Macbook firmware with Trim, [https://en.wikipedia.org/wiki/Trim_%28computing%29](https://en.wikipedia.org/wiki/Trim_%28computing%29) to recognize the drive. You are correct that being a 64bit, the MacBook has no BIOS and uses EFI and GPT to boot. I tried to install 64bit Xubuntu but the laptop didn't recognize it, so **I had to use** the 32bit. The install directed me to prepare a EFI boot partition (sda1) and all I did was to partition the rest of the disk. Formatting was done by the installation. Please look at the pastebin report. 

What I don't understand is how can the 32bit system boot in a laptop that has no CMOS, Also, I am repasting my original questions.

My concern is with this line in the pastebin report: _WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted._
Also, I have no clue when installing CPU or System related software, whether to choose 32bit or 64bit?
Finally, I created a GParted live USB key, but I have no idea which keys do I use to select the USB on boot. Alt/Function doesn't for boot source selection (but it should).

All I want is to understand and use Gparted to correct boot partition. and this must be done with the bootable Gparted Live.

---

