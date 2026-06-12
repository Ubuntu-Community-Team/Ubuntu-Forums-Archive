---
title: "Help with boot-repair Mint"
date: 2013-01-18
forum: Any Other OS
---

### Post by 9CWgT00MmY on 2013-01-18
Hi everybody first of all let me start by saying that I'm a new (trying to be) user of linux (haven't installed it permanently yet.. won't boot.

I installed Linux Mint 14 32-bit on an old computer that I had using an usb driver install. It's an Hp pavilion from circa 2005 it has 512 MB ram and 80 GB of memory, it's far from a good computer. The reason why I wanna try linux is well.. It has always interested me but I didn't have any knowledge of what computer was. Today I'm 20 and thanks to my computer science I'm rapidly learning how a computer works. 

So basically the reason I wanna have linux is to try and understand how it works and how it operates while doing my computer science class and also learn a lot of new stuff.

I did manage to install it.. (I think) the message that told me to restart the computer never appeared but after a while a 80 GB volume appeared on the desktop full of stuff that is unknown to me right now.

Anyways after trying to restart and having the removed the usb-key and making sure that the hard drive was the disk used at start.. I would get a black screen with "beeping" underscore at the top left corner.

I tried to use boot repair I installed it using this guide "https://help.ubuntu.com/community/Boot-Repair" using the Terminal
But it gave me an error telling me to enable a repository containing the grub2. (no idea what this is)
Anyways I took the test thing so see what the problem is and it sent me here to get some help.

would really appreciate some help. I've tried everything I could of thought off.

here's the link:
[http://paste2.org/p/2770464](http://paste2.org/p/2770464)

---

### Post by oldfred on 2013-01-19
Moved to your own thread.

You should just run the suggested repairs. You do not have grub installed to MBR and it looks like it is totally missing, so Boot-Repair is suggesting a total re-install of grub.

---

### Post by 9CWgT00MmY on 2013-01-19
is that when installing from the usb key or just using the boot repair?

I think it might be cause the install didn't finish like I said I never got a message that said that the install was ready and my cursor had a loading animation. But after 30 mins i was probably done?

Or maybe the PC can't handle it?

There is so many possibilities of what could be the problem :l

---

### Post by oldfred on 2013-01-19
When grub is missing it says install did not finish. It may just be grub or it could be other install issues. If Boot-Repairs fixes to grub then do not solve boot issues, it says install did not finish. Reinstall may be easiest, but you may be able to chroot into a broken install and fix it.

How much RAM? Full Ubuntu needs a fair amount nowadays. Do not know much about Mint.

---

### Post by xenopeek on 2013-01-19
Normally, if the install completed successfully, the GRUB boot loader would be installed to the MBR of your primary hard disk (/dev/sda). If for some reason it didn't, you can reinstall GRUB to /dev/sda with Boot Repair from the installation DVD / USB stick (you need to add the PPA as shown on the Wiki, and install Boot Repair before you can use it).

It seems more likely that your install didn't complete. You are just about matching the absolute minimal system requirements, which depending on some factors not be enough for the installer.

If the Boot Repair route doesn't work, I'd do a fresh install. Before you start the installer, open a terminal and run the following command. This removes the introductions shown during installation and is  reported by some users as solving installation problems for them.
```
apt remove ubiquity-slideshow-mint
```Another alternative is to enable swap before starting the installer. This will get quite detailed quickly, please ask if you need additional help. This is basically the same as the steps available on the Ubunty Wiki SwapFaq ([link]("https://help.ubuntu.com/community/SwapFaq")), so you may consult that also for further help.

[LIST=1]
[*]Before you start the installer, launch GParted from the menu. Make sure it has your hard disk selected, then select Device > Create Partition Table. This will wipe the current partitions on the hard disk.
[*]Then select Partition > New to create a new partition, and set 'new size' to 2048 MiB and 'file system' to linux-swap. Then select Edit > Apply All Operations.
[*]Right-click the created swap partition, selection information, and copy the value after 'UUID:'. Should be something in the format like '0f39a009-5d83-4cd6-a6bd-f09e4556ff7f'.
[*]Open the terminal and run the command:```
gksudo gedit /etc/fstab
```
[*]At the end of that file append a line like the following, replacing the UUID value with the one you copied from GParted:```
UUID=0f39a009-5d83-4cd6-a6bd-f09e4556ff7f none swap sw 0 0
```
[*]Save and close the file and run the following command to activate the swap:```
sudo swapon --all
```
[*]Run following command to confirm swap is active, it should show on the last line of output that it has a total of 2048 MiB of swap:```
free -m
```
[*]Now start the installer, and at the 'installation type' step of the installer select to install alongside existing partitions. It will then do the installation with this swap active, which is reported by other users with little system memory as making installation possible.
[/LIST]

---

### Post by YannBuntu on 2013-01-19
> **fsma92 said:**
> here's the link:
[http://paste2.org/p/2770464](http://paste2.org/p/2770464)

Some system files seem broken, so that Boot-Repair can't purge grub. I would use a Mint disc to fix them: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
Or simply reinstall Mint.

---

### Post by 9CWgT00MmY on 2013-01-19
The desktop environment is xfce and it's on mint 14 32bit also thanks a lot for all the replies.
As for the ram it has 512 MB but I read that it was enough, for the 32bit version anyway..

It really shows how nice the Linux community is.

And even though you gave me so many possible answers most of the slang your using is unknown to me I will try to redo the install as soon as I can.

---

### Post by xenopeek on 2013-01-20
I've made the steps a bit easier with knowing that you have Nadia Xfce. I'd suggest you try to follow the steps, I hope it is more clear when you have the applications open in front of you.

---

### Post by YannBuntu on 2013-01-20
> **xenopeek said:**
> Normally, if the install completed successfully, the GRUB boot loader would be installed to the MBR of your primary hard disk (/dev/sda).

(FYI, this is true for old computers, but new computers (since Windows7/8) don't use MBR any more, they use UEFI instead. See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) )

---

### Post by xenopeek on 2013-01-20
Yes, UEFI will make it more complex. But I doubt OP has UEFI ;)
> **fsma92 said:**
> I installed Linux Mint 14 32-bit on an old computer

---

