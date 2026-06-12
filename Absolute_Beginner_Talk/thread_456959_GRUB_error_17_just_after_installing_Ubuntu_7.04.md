---
title: "GRUB error 17 just after installing Ubuntu 7.04"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Altered Reality on 2007-05-28
I tried to install Ubuntu (v7.04) on my non-gaming PC, following the [walkthrough](https://help.ubuntu.com/community/GraphicalInstall) for the graphical installation.
That machine is quite old: it's a PIII 800 MHz, with 384 MB of RAM and two hard disks: the primary one has a 10 GB partition where Windows 98 is installed, followed by 70 GB of unallocates space; the secondary is a single FAT32 partition containing data.
My intention was to use the unallocated space for Ubuntu to get a dual-boot system, so I selected "Use the largest continuous free space" in the disk selection screen. The installation apparently went on smoothly until the end, when I was asked to reboot. I removed the live CD from the drive, and at the moment of loading the OS, I got error 17 from GRUB. I googled for a solution, and I got a lot of pages mentioning that error as something that may occur when **uninstalling** Ubuntu, while I had just finished **installing** it.
Anyway, those pages said that to restore the MBR with Windows 98 I had to boot with my Windows 98 CD and run the command "fdisk /mbr", so I did and rebooted. Since no OS could be found at the next boot (despite the fact that every file was still present in the hard disk) I reinstalled Windows 98, then I booted again with the Ubuntu live CD and used Gparted to delete all Ubuntu-related partitions, to bring the hard drive back to the original state.

Now I still want to install Ubuntu, and I still want to have a dual boot system, so can anyone explain what I did wrong and what I should've done instead?

---

### Post by Borzo on 2007-05-28
error 17 means that grub cannot recognize a partition. it could be that grub had an error in it's settings.

---

### Post by Altered Reality on 2007-05-28
> **Borzo said:**
> error 17 means that grub cannot recognize a partition. it could be that grub had an error in it's settings.
So how do I check its settings, and how do I know if they are correct?

---

### Post by omkarwagh on 2007-05-28
use your live CD and type the following
fdisk -l

this will output all of your partitions. then if your ubuntu partition is say /dev/hda6 type the following:-
sudo mount /dev/hda6 /mnt

this will mount the drive on /mnt
now go to /mnt/etc and check you fstab and mtab and see if they match with the stuff you got from the fdisk -l command.

after this go to /mnt/boot/grub
now type sudo vim menu.lst

scroll down to where the ubuntu loader is entered. in there check whether the same partitions are being declared as the boot drive as you saw in the fdisk -l and your fstab and mtab.

once you make sure that everything matches reboot with your hard disk. your friendly grub screen should now be there for you.

also in the menu.lst file if your change the titles, then you can have grub display for you somehting like "Enter at you own risk" or "This is my Computer so stay away" instead of the standard boring old "Ubuntu 6.06 i386 blah blah blah".

hope this helps.
omkar

---

### Post by Southbound on 2007-05-28
Omkarwagh, I tried to follow your instructions but the mount command brings up the error saying I must specify a file system type.  I tried "sudo mount -t vfat /dev/sda5 \mnt" but then got the message "mount: wrong fs type, bad option, bad superblock on /dev/sda5."  Is there some other way to do this?

---

### Post by Famicommie on 2007-05-28
from the live CD, run this command:
```
sudo mkdir /media/Ubuntu && sudo mount -t ext3 /dev/<partition> /media/Ubuntu
```

Instead of <partition>, but the actual location of the partition, which you can find out by running the command:
```
sudo fdisk -l
```

It will be the entry with the type Linux. While you're at it, paste the results of fdisk to a forum post so that we can help further. In Linux, middle mouse copies/pastes, and to copy or paste from a terminal with a keyboard use Ctrl+Shift+C instead of the normal Ctrl+C (which is reserved for the quit command). Terminal works differently, you see.

From THERE, use the following commands to get some more information to post to the forum. Run them one at a time.

```
gedit /media/Ubuntu/boot/grub/menu.lst
gedit /media/Ubuntu/etc/fstab
```

With the results of your fdisk, menu.lst, and fstab, we should be able to get you all sorted out.

---

### Post by Southbound on 2007-05-28
First a brief story of how I got this message:  I had a windows laptop with one big ntfs partition.  I created a small linux partition and a swap partition to give linux a try.  I installed linux and successfully used grub to dual boot.  THEN I tried to create a shared partition and the grub error 17 began being displayed.  I guess I'm unsure if the partition software made the partition successfully or caused any problems.

Running sudo fdisk -l gives me the following:

> Disk /dev/sda: 30.0 GB, 30005821440 bytes
240 heads, 63 sectors/track, 3876 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2003    15142648+   7  HPFS/NTFS
/dev/sda2            2710        3876     8819685    5  Extended
/dev/sda5            2710        3743     7807558+  83  Linux
/dev/sda6            3743        3876     1012063+  82  Linux swap / Solaris

Then entering the command: "sudo mkdir /media/Ubuntu && sudo mount -t ext3 /dev/sda5 /media/Ubuntu" gives me this:

> mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Altered Reality on 2007-05-28
omkarwagh, I tried to follow your instructions, but when I enter **fdisk -l** at the terminal, I get no list at all. It's like the command wasn't even executed! After I press return, all I get is **ubuntu@ubuntu:~$** and the blinking cursor.
However, the partitions are correctly seen by GParted. Here's what I see on GParted:

```

Partition        Filesystem  Size          Used          Unused        Flags
/dev/hda1        fat32        9.50 GiB      5.60 GiB      3.90 GiB     lba
/dev/hda2        ext3        65.76 GiB      2.98 GiB     62.78 GiB     boot
/dev/hda3        extended     1.07 GiB         --            --
   /dev/hda5     linux-swap   1.07 GiB         --            --

```

What next?

---

### Post by Borzo on 2007-05-28
according to what you have posted your linux parition is /dev/hda2, this is where grub should point in it's /boot/grub/menu.lst

p.s. to get a list from fdisk -l you need o type "sudo fdisk -l"

---

### Post by SoulinEther on 2007-05-28
The following passage is a story about some guy. After reading it, you may find your problems can be solvable by imitating his steps. (hehe, just wanted to sound like those standardized tests :))

I installed Ubuntu on my brother's PC... it already had two hard drives, each with one partition.

When I finished installing it the first time with the live CD, on the last step, when I clicked advanced, the installer said GRUB was going to be set up on hd0. That means the first hard drive on the system, I figured, and I was correct; lo and behold, after the install was finished, I could not boot up from the hard drive with Ubuntu but rather GRUB loaded onto the first win xp hard drive.

When I tried to boot into Ubuntu, I got an error 17.. I thought.. ok... that doesn't make sense. I pushed "e" to edit the boot command and then e again to edit "hd(2,0)". It would be a temp-only fix, as far as I know.

So... I edited that "hd(2,0)" entry. When I was in that GRUB command line style editing thing, it used a nice auto-completion system, so if you push tab at any point within your line of text it'll give you suggestions.

I backspaced to "hd(" and pushed tab. Gave me three choices: 0, 1, 2. I typed 2, knowing Ubuntu was my final drive.

"hd(2," gave me: 

0: Fat32, 1: ext3, 2: ext3, 3: swap

and I thought... ok, clearly the problem was that it was trying to boot into the fat32, empty partition I made for another windows install I would make on it later. I changed it to hd(2,1), where 1 was my / "root" ext3 partition. Tried booting, didn't work, but that's beyond the scope of what I'm trying to say.

I reinstalled Ubuntu and made sure that GRUB was installed ON THE PHYSICAL HARD DRIVE that I installed Ubuntu. Obviously this is not entirely necessary but it would make things a lot easier for me.

So... I try to boot again. It gave me another error 17. Wow that's junk. So I go back to edit the boot option for the Ubuntu kernel version blah.blah.blah.0blah and I see that the hard drive is... once again, wrong. It was ordering to boot off of hd(2,0) which according to the ubuntu installer was correct but in the perspective of the "ubuntu hard drive" was not. It needed to boot off of hd(0,0) (oh yeah, I didn't even make a fat32 partition this time). So I changed that setting, went back to the edit screen of GRUB and pushed b to boot. A success.

Then... when I loaded up, I decided to fix up GRUB's boot list.

Push alt-f2 and run gksudo gedit, or alternatively use a command line and run sudo gedit (hah, so much for vim or emacs), enter your password, go to Open, find /boot/grub/menu.lst. Find the

"## DO NOT UNCOMMENT THEM, Just edit them to your needs" line... go down a bit and find the "Default grub root device", where x and y are two numbers:

# groot=(hdx,y)

and change the #s accordingly to whatever you found you needed from the grub edit thing. And then go down and find every instance where you see Ubuntu, kernel 2.6.20-xx-whatever and where it says root (hdx,y) fix it to match your groot settings above.. from what I gather every time Ubuntu adds a new updated kernel to the launcher it takes the value of groot(x,y) above and applies it to the new launcher, but I'm not sure if it will automatically update any previously-made boot things.

On that matter maybe GRUB was saying stuff like (hd0,0) as opposed to hd(0,0). Oh well.

........

Uhm... I think my story helped... if it didn't, could someone with more than half a brain better explain what I'm trying to say? Thanks...

---

### Post by Borzo on 2007-05-29
allrighty... boot your  live CD or any live linux distibution, cd, pendrive whatever. at console type:

sudo mkdir /media/linux
sudo mount /dev/hda2 /media/linux
gedit  /media/linux/boot/grub/menu.lst

check your root enteries, yours should say:
root (hd0,1)
if they don't - correct, save, eject cd, reboot, observe if it works.

---

