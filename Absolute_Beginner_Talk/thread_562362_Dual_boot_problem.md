---
title: "Dual boot problem"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Arkasai on 2007-09-28
So I installed PCLinuxOS to get a feel for popular KDE distro (other than Kubuntu) and am having trouble dual booting.  I'm fairly sure I configured PCLOS to install with its own partitions, but when I boot I just get a PCLOS splash screen and no Ubuntu option.  This is very odd, as before when I still had Windows on the disk, it would prompt me to choose an operating system.  My original partitions are seemingly intact.  Any help?

---

### Post by benerivo on 2007-09-28
Something similar happened to me last year. I think Ubuntu is still on your system, it's just that it is not listed in  /boot/grub/menu.lst in your PCLinuxOS installation - which is now the file that your boot options come from when you switch the pc on.

If i remember right, I fixed it by copying the lines for Ubuntu from Ubuntu's /boot/grub/menu.lst and pasting them in to PClinuxOS's menu.lst (you should be able to access the Ubuntu partition from PCLinuxOS).

---

### Post by nb123 on 2007-09-28
Hi, it's probably not recognizing your ubuntu partition. You need to edit it to make sure it does. You installed a grub bootloader? Edit the menu.lst file to get it to recognize Ubuntu again.

I'm running PCLinuxOS alongside Ubuntu as well (both on my external USB hard disk) but I did not install a bootloader with PCLinuxOS. I just installed the Operating System and pressed cancel at the part where it prompts me to install a bootloader. Then I edited my menu.lst file in my existing grub installed by ubuntu to launch PCLinuxOS. I find this much easier than dealing with the headache of my existing grub being overwritten. 

That said, although I've never installed PCLinuxOs exactly the way you did it, I might be able to help you. Could you post the contents of your menu.lst file? It'll most probably be at /boot/grub/menu.lst in PClinuxOS filesystem.

Also please post the output of: --- 

```

fdisk -l

```

What is the partition that your ubuntu is on? (e.g. /dev/hda2)

---

### Post by nb123 on 2007-09-28
Please do as benerivo says and copy your ubuntu entries in /boot/grub/menu.lst in your ubuntu filesystem to the /boot/grub/menu.lst in your PCLinuxOS filesystem.

---

### Post by ajgreeny on 2007-09-28
Most linux distros other than ubuntu don't seem to detect an existing linux and therefore don't add them to the menu.lst file when it is installed.  Assuming you know the partition name on which you have ubuntu, eg. hda2 or sda2 or whatever, just mount that partition in pclos with ```
mount /dev/hda2 /mnt/ubuntu -t ext3
``` having first made the /mnt/ubuntu folder with ```
mkdir /mnt/ubuntu
```  You will have to do both these commands in a root terminal, but I can't remember how you do that in pclos.

You will now be able to copy the entry for the ubuntu install in the ubuntu menu.lst file  and add it to the pclos menu.lst file.  Now when you boot up you should have both linux distros showing.  I know this works because I have done it myself, also with pclos, which I didn't like as much as (k)ubuntu, so got rid of it and am now trying linux mint instead, which is a very attractive version of ubuntu with all codecs installed by default, together with several plugins for firefox which have to be added in ubuntu, not difficult I agree, but for new linux users mint has distinct advantages, and it also finds other existing linux installations.

---

### Post by Arkasai on 2007-09-28
This is my /boot/grub/menu.lst for PCLOS, I'm not sure how to access that file on my Ubuntu partition from PCLOS though.```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,7)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title linux
kernel (hd0,7)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda8  acpi=on resume=/dev/sda6 splash=silent vga=788
initrd (hd0,7)/boot/initrd.img

title linux-nonfb
kernel (hd0,7)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda8  acpi=on resume=/dev/sda6
initrd (hd0,7)/boot/initrd.img

title failsafe
kernel (hd0,7)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda8  failsafe acpi=on resume=/dev/sda6
initrd (hd0,7)/boot/initrd.img

```

Is there an easy way of checking which partition Ubuntu is installed on from PCLOS?  I looked at the partitions earlier on my Ubuntu liveCD using Gparted, but didn't take note of which one Ubuntu was on.

---

### Post by Arkasai on 2007-09-28
Ubuntu is on partition sda6, but when I enter:```
mount /dev/sda6 /mnt/ubuntu -t ext3
```konsole tells me "mount: /dev/sda6 already mounted or /mnt/ubuntu busy"

---

### Post by benerivo on 2007-09-28
> Is there an easy way of checking which partition Ubuntu is installed on from PCLOS

You could install GParted from PCLinuxOS, or have a guess at the partition using either of these commands in a terminal ```
sudo fdisk -l
blkid
```

Then try to mount it in PCLinuxOS.

BUT FIRST -  i would run ```
sudo konqueror
```, then in the address bar, type ```
media:/
```then right click on any partitions visible and mount them if the option is available.

---

### Post by benerivo on 2007-09-28
> **Arkasai said:**
> Ubuntu is on partition sda6, but when I enter:```
mount /dev/sda6 /mnt/ubuntu -t ext3
```konsole tells me "mount: /dev/sda6 already mounted or /mnt/ubuntu busy"

It sounds as if it is already mounted. Check your /mnt and /media folders to see if it there.

---

### Post by Arkasai on 2007-09-28
> **benerivo said:**
> It sounds as if it is already mounted. Check your /mnt and /media folders to see if it there.My mnt file lists ubuntu and cdrom, and the media file in that same partition shows nothing.

---

### Post by benerivo on 2007-09-28
What does it show when you type media:/ in to a konqeror window?

---

### Post by Arkasai on 2007-09-28
> **benerivo said:**
> What does it show when you type media:/ in to a konqeror window?Currently showing two partitions, both mounted.

---

### Post by benerivo on 2007-09-28
And neither of these are Ubuntu? Are you sure Ubuntu is on hda6? If you are then you can add an entry to your /etc/fstab file so that it mounts automatically when you boot. In konsole run ```
blkid
```and get the UUIID number for hda6. Then put this line in to your fstab file (using your own UUID number) ```
UUID=FETC212FDC7156D2 /mnt/ubuntu ext3 gid=500 0 0
```and reboot.

PS - This assumes that your Group ID is 500. I think it will be in PCLinuxOS, but you can double check in the account management section if it isn't.

---

### Post by ajgreeny on 2007-09-29
> **Arkasai said:**
> Ubuntu is on partition sda6, but when I enter:```
mount /dev/sda6 /mnt/ubuntu -t ext3
```konsole tells me "mount: /dev/sda6 already mounted or /mnt/ubuntu busy"

OK Arkasai, your ubuntu is already mounted in PCLos by the looks of it.
So in konqueror or nautilus, whichever file manager is in PCLos, go to /mnt/ubuntu or /mnt/sda6, navigate to /boot/grub/menu.lst and open that file.  Copy the entries at the end of the file, starting with one that will look like this, but may be slightly different:-

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=962b3956-3aa3-4c1d-88fa-4f0ee2568dee ro splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

You can copy the rest of the entries if you like, but it is not really needed.  Now open your PCLos menu.lst file as root and add the entries you just copied at the bottom of that.  Save this and you should get the option to boot ubuntu next time you start.

---

### Post by Arkasai on 2007-09-29
Well I'm snagged in a few places here.  PCLOS doesn't recognize the directory /mnt/sda6 (even though I can see this partition)  so I cant navigate to the ubuntu  /boot/grub/menu.lst file on that partition (unless I've been doing something wrong.) I've tried from both the konsole and konqueror.   Also, even as root, my menu.lst file doesn't allow me  to edit it.  I can copy entries, but can make no changes.

---

### Post by ajgreeny on 2007-09-30
It might be easier to download a puppy linux iso, burn the image to a CD, boot from that and then find your ubuntu partition from its file manager.  Puppy will mount hard disks easier than ubuntu liveCD, so may make the task in hand more straightforward for you.  Having found the ubuntu partition, find the menu.lst file (you'll know if it is the right one as it will list ubuntu at the top of the OS list at the bottom of the file).  Copy this onto a usb flash drive, or just make a careful hard copy, then boot into PCLos and add the ubuntu entries to you PCLos menu.lst file as before.

An alternative method is to copy the entries for PCLos from its own menu.lst file to a usb drive as I said above, then boot into a live CD and reinstall your ubuntu grub, instead of the PCLos grub.  You can do this as follows:-

oot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install, use the one that you want the grub to run from. Here is where you will have to decide which is your PCLos and which your ubuntu partition.  Replace the question marks in the following command with the output of the this last command that corresponds to the ubuntu partition :
    root (hd?,?)
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working ubuntu grub bootloader.

Now when you restart into ubuntu you will be able to add the PCLos entry into the ubuntu menu.lst, and away you go.

Trust me, it may sound very complicated, but once you've done it a few times as I have with various second disk linux distro installations it almost becomes second nature and very easy.

---

