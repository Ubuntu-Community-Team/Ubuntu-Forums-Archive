---
title: "GRUB : Dual Booting"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by TC_UK on 2007-12-22
I use a Samsung laptop X50 with XP OS and i wanted to install Ubuntu on my external firewire drive. The plan was to dual boot.  I managed to boot using the DVD with the Ubuntu OS 7.10 released and it installs on the external hard drive via the firewire and it works fine, i selected the installation to use the entire external hard disk.  
At the end of the installation I reboot without the dvd with the OS and i can see the sequence where i can read the display text GRUB and the error 12.  Can you help me, I really need my xp os and contents intact, is there a way i can get Grub to give me the option to select the os i wanted to boot, can you help.  I suspect that the grub error 12 means it was unable to see the external drive using firewire is that right?  Love to hear from some one who can help me resolve this, I am unable to get to my system disks for the backups. I am a virgin in the linux system.

---

### Post by meierfra on 2007-12-22
Just to make sure: It sounds like you  can boot  neither   Ubuntu nor Windows. If  this is the case I recommend that you  restore your MBR. (Click on FixMBR in my signature) This should allowed you to boot into Windows. (If you are on the LiveCD while reading this try the third method first)

I'm not sure whether you will be able to boot ubuntu from your firewire drive.  But we can try. Boot from the LiveCD, open a terminal (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```

---

### Post by TC_UK on 2007-12-23
thank you, will try that and let you know.

---

### Post by TC_UK on 2007-12-23
Does the third option on LIVE CD require the use of the XP boot cd?  

I tried the sudo fdisk -l which tells me the partition of the two hard drives. Was wondering if i can find the txt file which grub uses to boot and use to boot my XP from the main hard drive.

thks

---

### Post by meierfra on 2007-12-23
> Does the third option on LIVE CD require the use of the XP boot cd? 

No.


> Was wondering if i can find the txt file which grub uses to boot and use to boot my XP from the main hard drive.

In theory yes. But that file (/boot/grub/menu.lst)  is located on the ubuntu partition on the external drive, and it seems that you are currently not able the access the external drive during boot up. Or do you get to the Grub  menu at boot up? (You might have the press "Esc" during the countdown for the Grub menu to appear)


If you post the output of  "sudo fdisk -l"  I can tell exactly how to find "menu.lst" and how to edit it.

---

### Post by TC_UK on 2007-12-23
I should explain a bit more: I swapped out the laptop HDD drive with Windows (WHDD) and install the ubuntu to the new drive (UHDD).
I did swap back my WHDD and checked.  You are right, the Grub needs the information that i think is on the firewire external drive (FHDD) which it does not see.  Booting off the Live Ubuntu DVD works and it see the fhdd.  This mean boot sequence does not have the ability to see FHDD, I agree with you I dont see how this could be fix as the boot sequence assumes that any HDD the system.  I suppose this also rules out booting from a external USB drive as well.  If i can boot off a usb drive, I can get a usb enclosure for it and use usb connection to boot the FHDD. 

when I have the WHDD installed I have not access to the internet, I use wireless connection and i think i can swing the connection but i can not sure if the save the setup in network connections will corrupt the WHDD.  If in there is no hard done I can get the internet connection and give you a copy of the sudo fdisk -l information but if my guess/deduction is correct I not sure if that information will be helpful.

I did look for the menu list and could not find it on the WHDD.

I am away from home no windows boot disk might ask a neighbour to help out with the loan of XP professional cd.

thanks for helping out looking forward to your advice. :)

---

### Post by meierfra on 2007-12-23
It seems your bios do not  support  booting from an FireWire (but I'm not  sure)

You can still try   any of  the following:

1) Install ubuntu on the internal drive and use the FireWire drive for storage.

2) Put ubuntu onto the FireWire, but make a separate boot partition on the internal drive.

3) Yes, if your  bios support booting from an  USB drive, you might get an USB enclosure. But I have seen various case where people had problems booting from a USB enclosure. So I would not recommend this, (But this opinion doesn't  count  much since I don't know anything about USB enclosures)

---

### Post by TC_UK on 2007-12-23
hehe good new, thanks to your comment, about the BIOS support for firewire booting, I went to check the BIOS and found the firewire boot support disabled.  When i enabled it and reboot GRUB now sees the firewire.

This is very good news indeed and I even booted up my XP OS as well.  I must admit I am very impressed with Ubuntu and especially the support to resolve my silly naivety thanks to you.

I was wondering if you can help me more.  At the moment i can boot with the firewire hdd (FHDD) connected.  Was wondering what I really like is to be able to boot even without the FHDD connected and to be given the option to boot xp without the FHDD.  Can you help?  I suspect some where on th einternal drive there is a file I can intercept and modify to make this work.  The idea I can travel about with the FHDD and when i want I can boot unbuntu to use the os to teach myself more on Linux.

I really like Linux to be the user friendlier to the joe public  so thet will move to Linux instead of Vista.  If you can point me in the right direction I help out, I have done programming years back so have a steep learning curve to catch, let me know.  

Hope this is posting helps as well to others. :)

---

### Post by TC_UK on 2007-12-23
Sorry bad typing about travelling, I mean travel about without the FHDD device.  Might look into a larger hdd and have both OS on the laptop. :)

---

### Post by meierfra on 2007-12-23
> I was wondering if you can help me more. At the moment i can boot with the firewire hdd (FHDD) connected. Was wondering what I really like is to be able to boot even without the FHDD connected and to be given the option to boot xp without the FHDD. Can you help?


Actually just a couple of days ago I wrote up a tutorial how to do that.I haven't posted it yet, so this is the perfect opportunity for me to try it out. I'll put it in the next post.

---

### Post by meierfra on 2007-12-23
This howto  addresses the following issue: You successfully installed Ubuntu onto an external hard drive. With the external drive plugged in, you can boot into Windows and Ubuntu from the Grub menu. But if the external drive is unplugged you get a Grub error during boot up. 
To fix the problem you will have to edit the file "menu.lst",  install grub to the external hard drive,  restore the MBR of the internal hard drive and change the boot order in  the Bios. Here are the details:

Step 1 Edit menu.lst

Open a terminal (Applications->Accessories->Terminal) and type

```
cd /boot/grub
sudo cp menu.lst menu.lst.backup
gksudo gedit menu.lst
```

This backups the file "menu.lst" and  opens it in a new window.
Look for the line 

#groot (hdx,y)

Here x and y are some numbers. Typically this would be "#groot (hd1,0)"

Change it to 

#groot (hd0,y)

So for example "#groot (hd1,0)" needs to be changed to "#groot (hd0,0)"

Next look for the Windows title. It should look something  like

title Some Version of Windows
root (hds,t)
savedefault
makeactive
chainloader +1

Here  s and t are some numbers. Change it to 

title Some  Version of Windows
root (hd1,t)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

So for example 

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

needs to be changed to 

title Windows XP
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1 

Save and close the file.

To complete Step 1, go back to the terminal and type
```
sudo update-grub 
```

Step 2:  Install Grub to the MBR of the external drive:

In the terminal type:
```
 sudo grub 
```

and at the "grub>" prompt

```
root (hdx,y)

setup (hdx)

quit
```

Here x and y are the same numbers as above (the orignal  numbers from "#groot (hdx,y)" in menu.lst)  So  for example if  menu.lst originally contained "#groot (hd1,0)", you need to do

```
sudo grub
root (hd1,0)
setup (hd1)
quit 
```

Step 3 Restore the MBR of the internal drive (You need to have a working Internet  connection for this step. For other options how to fix the MBR  see FixMBR in my signature):

If you do not  have the "universe" repositories enabled:
Go to Systems-> Administration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)
Click on Close (twice)

Next in a terminal type:

```

sudo apt-get update

sudo apt-get install ms-sys

sudo ms-sys -m /dev/sda 
```

Here /dev/sda needs to be replace by the actual   name for the hard drive containing your Windows partition. Typically it will be /dev/sda or /dev/hda. If you do not know  the correct  name, type "sudo fdisk -l" in a terminal (not at the grub prompt). Looking at the output you should be able to figure out the correct name.

Step 4  Change your boot order.

Reboot. At boot -up enter the Bio's Setup. (For example on a Dell you will have to press the "F2" key  immediately after the computer restarts.) 
 Set the boot order such that the external hard drive containing Ubuntu is first,  and the internal drive containing Windows is second.

That's it. Now if you boot with the external drive plugged in you should get the
grub menu. If the external drive is  unplugged you should boot directly into windows.

If you  run into problems or you have a question,  post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

---

### Post by TC_UK on 2007-12-23
Great, if that works i was wondering if it can be a option of the boot Livecd and built in code to check the bios being enabled to check for external hdds be it usb or firewired.  I suspect that with the large capacity like 64GB solid state devices coming on line, that become requirements.  I do love the idea of getting people to dual boot get used to linux and switch over completely once they feel very comfortable with using ubuntu. :-)

---

### Post by meierfra on 2007-12-23
This is the very first version of this howto, so don't hesitiate  to ask questions, if something does not make sense to you.

---

### Post by meierfra on 2007-12-23
> built in code to check the bios being enabled to check for external hdds be it usb or firewired. 

I don't think that is possible, but I do not know. It seems to me that the operating systems does not know about the status of the bios. For example Ubuntu sometimes messes up the install onto an external drive, since it does not know the order of the hard drives in the bios.

---

### Post by meierfra on 2007-12-23
I just fixed a typo in my tutorial. I left out a "gedit" in the first code.

---

### Post by TC_UK on 2007-12-23
when is the next posting. hehe

---

### Post by meierfra on 2007-12-23
> when is the next posting. hehe
??????

---

### Post by meierfra on 2007-12-23
Did you see post 11?

---

### Post by TC_UK on 2007-12-23
sorry, it was in the new page, i thought it was continous pageless one.  I will try it out soon perhaps I should save a copy in case i made a mess of it.

---

### Post by meierfra on 2007-12-23
You can backup menu.lst via

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

---

### Post by TC_UK on 2007-12-23
I am ready to make the change you suggested.  Have a problem getting to the root directory, the boot sequence makes the deafult directory to the user directory.  So i need to use the terminal to get down to the boot directory.  I have use su and change to root and cd to root  done the first sequence.  Here is the menu.lst :-)



# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ad778d0e-1130-4c3d-b9b7-6784503e8dc2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ad778d0e-1130-4c3d-b9b7-6784503e8dc2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ad778d0e-1130-4c3d-b9b7-6784503e8dc2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

cannot find #groot (hdx,y) :-)

here is the fdisk information :-)

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa299a299

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       16384   12  Compaq diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           4        9733    78156225    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x937bb523

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11784    94654948+  83  Linux
/dev/sdb2           11785       12161     3028252+   5  Extended
/dev/sdb5           11785       12161     3028221   82  Linux swap / Solaris

---

### Post by TC_UK on 2007-12-23
I took the plunge and made the modifications which sems to work well.  There is one slight issue, the bios enables the booting via firewire but does not allow the firewire hd to be the primary drive as you suggested.  Probably my lack of understanding, there is external atapi, the cdrom, then the external ide etc.  tried to use the different options and no success.

I remember a long time ago where people use the boot.ini as the menu to allow multiple os to be selected at  the user discretion, perhaps that is a better way.  Was wondering if you or the other ubuntu advisors can add to this or help me to select dual boot on firewire or usb.

Thanks so far fro the help, manage to boot my xp os and lost the ability boot ubuntu from external firewire drive.
:-)

---

### Post by meierfra on 2007-12-23
> cannot find #groot (hdx,y)


It is in the middle of the file:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)


> remember a long time ago where people use the boot.ini as the menu to allow multiple os to be selected at the user discretion, perhaps that is a better way. Was wondering if you or the other ubuntu advisors can add to this or help me to select dual boot on firewire or usb.

This might be possible and I have done it to boot Ubuntu when  Ubuntu and Windows are on the same drive. I'm not quite sure whether  and how it works when Ubuntu and Windows are on different drives. I'll do some testing and let you know.

---

### Post by TC_UK on 2007-12-23
I think I done that before on different internal drives but not on different type of transfer protocols, i.e. usb or firewire.  Those the old days with redhat or suse but never not far with using them on laptops back in 1999.  mLook forward to hearing from you or you can send me the scripts to try it out.

---

### Post by meierfra on 2007-12-23
I figured out how to  do it, but it is a little bit of a hack.  Maybe you want to use a different bootloader instead (for example [:WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html"))

Anyway, this should work:

Boot from the Ubuntu Live CD.  We will temporarily installl grub to the boot sector of sda1. But we will first  backup  the boot sector

```
sudo dd if=/dev/sda1 of=sda1 bs=512 count=1
sudo grub
root (hd1,0)
setup(hd0,0)
quit

```

Next we mount the Windows partition, copy the boot sector of sda1 to a file on the windows partition and restore the boot  sector of sda1:

```
sudo mkdir /windows
sudo mount -t ntfs /dev/sda2 /windows
sudo dd if=/dev/sda1 of=/windows/ubuntu.dos bs=512 count=1 
sudo dd of=/dev/sda1 if=sda1 bs=512 count=1

``` 
(Note that "if" and"of" are swapped in the last line)

Finally you need to edit "boot.ini"

```
gksudo gedit /windows/boot.ini
```

Add the following line to the end (in the line immediately after the last line, don't leave a blank line)

C:\ubuntu.dos="Ubuntu"

Save the file. Reboot and hope for the best.


You need to follow the instruction very carefully. The best thing is to  the copy and paste line by line. (I tripple checked for typos)
"dd" is  dangerous command, which can wipe your hard drive)

---

### Post by TC_UK on 2007-12-24
Thanks for the help, was wondering, the hack as you says seems challenging.  I just woke up, will consider doing the hack later, the good news is that Ubuntu seems more use friendly on the terminal and networking front, should not be problem i think.  Will let you know.  I have to run the live cd again, setup the wireless lan and safe the file before it can work was wondering if it will affect my main windows drive if i save the dns and stastic address.  The Wrouter has DHCP off.

---

### Post by TC_UK on 2007-12-24
WinGrub dont know that, which is easier and less risker.

---

### Post by TC_UK on 2007-12-24
I had a looked on wingrub and think yours is cooler.  Lets say its neater.  I am wondering if the commands you gave me if it can be be run automatically.  The earlier scripts as well, I was think if i have to undate ubuntu or replace the firewire hdd whether that i can boot off the livecd again and get the whole thing automated using fdisk -l to provide the information with search for the information and puting them to registers and then run it automatically.  Sounds fun.

---

### Post by meierfra on 2007-12-24
Automatic script probably would not work (For example I have six operating systems on just one hard drive) But an interactive script should be possible. Never wrote any scripts myself, but if you have some experience writing scripts and would like to do it, I am  willing to help.

---

### Post by meierfra on 2007-12-24
I forget to mention that you should NOT change the "groot"-line  in menu.lst  before you try my second script.  Since you will be booting from the internal drive, the second script only works with original   "groot"-line.


> WinGrub dont know that, which is easier and less risker.

I guess my script is easier. The only risky part in my script is the "dd".  But as long  as you get the "bs=512 count =1"  parts  correct, it won't do any damage.

---

### Post by TC_UK on 2007-12-25
I been trying to make a backup plan just in case it did not work and I found the BIOS boot function can allow to me to select the sequence  like to boot firewire drive first and then the internal drive.  It works great too.  Still to have what we talked about to make it easier for later installaments.  Still thanks for your help.

---

### Post by meierfra on 2007-12-25
> It works great too.

So are you able to boot into ubuntu now?  How did you do it?  Did you change #groot in menu.lst? Are you using a different bootloader?

---

