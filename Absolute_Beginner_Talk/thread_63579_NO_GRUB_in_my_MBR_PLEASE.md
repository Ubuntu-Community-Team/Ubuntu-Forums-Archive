---
title: "NO GRUB in my MBR PLEASE"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by ahayes on 2005-09-08
I'm looking to install Ubuntu but last time the installation failed and because the installer put GRUB in my MBR I wasn't able to recover and I had to reinstall Windows to get it out.  Is it possible to make sure that next time the installer instead installs GRUB in the root partition so that if I have problems I can simply activate the windows partition?

---

### Post by tonysathre on 2005-09-08
u should have been asked if u want to install grub on the MBR or somewhere else, when it asks just say no and it should ask u where u want to install it.  if it messes up your windows install again u can reinstall NTLDR in the MBR with the fixboot command from the emergency console after booting with the install cd.  what is the error you get when the linux install fails?

---

### Post by JimmyBEng on 2005-09-08
[QUOTE=ahayes]I'm looking to install Ubuntu but last time the installation failed and because the installer put GRUB in my MBR I wasn't able to recover and I had to reinstall Windows to get it out.  Is it possible to make sure that next time the installer instead installs GRUB in the root partition so that if I have problems I can simply activate the windows partition?[/QUOTE]
 umm... maybe a silly question but why not install GRUB to the MBR?  When I installed Ubuntu the installer did a good job of recognizing my windows partition and putting that option into GRUB automatically.  Then you will be able to boot into either Ubuntu or windows.

---

### Post by menawollas on 2005-09-08
If you find a handy Win98 Floppy (  :-# ) with fdisk on it, then boot from that and type fdisk /mbr and your MBR will get reset. 

In my case, I used Gdisk, which comes with Norton Ghost, and which is a lot more flexible, but does the same thing. As I had Windows in hda2 and ubuntu in hda7 it didn't reset hda2 as the active partition, so I had to use gdsik to do that for a straight non boot managed boot to Windows.

---

### Post by Lux Perpetua on 2005-09-08
There are reasons to avoid overwriting your existing MBR (paranoia, mistrust, advance knowledge that GRUB will not be able to boot one of your pre-existing partitions (it happens!), etc.). The way I did it was pretty much exactly steps 10-18 [here](http://www.linux-laptop.net/hosted/thinkpad-a31p-rhel.html). (Caveat: if you do decide to use the bootpart solution, for some reason, Windows does not like it if your "bootsect.lnx" is not precisely in the directory C:. Not even a subdirectory of C:; it wouldn't work for me until I put it directly in C:.)

---

### Post by ahayes on 2005-09-08
[QUOTE=tonysathre]u should have been asked if u want to install grub on the MBR or somewhere else, when it asks just say no and it should ask u where u want to install it.  if it messes up your windows install again u can reinstall NTLDR in the MBR with the fixboot command from the emergency console after booting with the install cd.  what is the error you get when the linux install fails?[/QUOTE]

No message, I have a LCD and the screen looked like what a CRT looks like if you assign a resolution or colour depth that it too high.  That's what happened when I tried to boot, and it completely ignored my Windows partition.

If it helps i have a laptop with:
1.8 ghz AMD a64
256 MB ram
80 gb ide hdd
nVidia GeForce Go 440 w/64MB ram
USB 2 and Firewire 400, 100Mbit Ethernet
a USB mouse and keyboard
a FW HDD
dlink DWL-630 wireless card

When I did this I was attempting to install the AMD64 version.

---

### Post by GreyFox503 on 2005-09-09
If you are just looking to try out Ubuntu and keep the Windows bootloader, I believe that during the install you can instruct it to install GRUB to a floppy disc.  That way, your MBR stays the same, and whenever you want to use Ubuntu, you boot from that floppy.

---

### Post by quandary on 2007-10-15
Hi there!

You don't have to reinstall Windows. Just kick Grub out of the MBR (Master Boot Record).

To do so, do the following:
When your PC starts, make sure the primary boot device is the CD/DVD drive.
(On my PC: Press F2 on startup to enter the BIOS. Select Boot Order. Press Enter. Set the CD Drive as No. 1, the Hard Disk as No 2, Press ESC, select "Save settings and exit". DO NOT ALTER ANY OTHER SETTINGS THAN THE BOOT ORDER, OR YOU might SCREW-UP YOUR COMPUTER!!)

Now you can boot up using your WinXP/Vista install CD. When it says: press any key to boot from CD, DON'T press any key. Windows should then start using the boot image from the CD, and the rest from your Hard Drive.

---
If you are not sure that this works, download a boot image CD from the internet (there are quite many out there). Burn the image to CD AND TEST WHETHER IT WORKS. If it works, you can install Linux without fear.
---

If GRUB screws your MBR, just boot windows from CD using either way i described.
Download MbrFix.exe from [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)
Install it/Unpack it.

On your Explorer Bar, click on Start --> Run
type 'CMD' (without the ') , press enter

change to the folder you copied MbrFix to. In case you put it on the desktop in the folder MbrFix, do this:
type 'cd "c:\Documents and Settings\YOUR_USER_NAME\Desktop\MbrFix" '

Now type (this is optional, but a GOOD idea):
'MbrFix /drive 0 savembr Backup_MBR_0.bin'
this creates a backup Copy of your current MBR

If you run WindowsXP/2000 type:
MbrFix /drive 0 fixmbr /yes

else If you run Windows Vista, like me, type:
MbrFix /drive 0 fixmbr /vista /yes

The MBR of your Windows is now restored. (This did not delete any of the data that was on your drive, it just put back the Windows BootLoader to where it belongs).

Now remove any CD from the CD-Rom drive and restart. Windows should now start up normally.

Should anything go wrong, you can boot up windows again (from CD) and type:
MbrFix /drive 0 restorembr Backup_MBR_0.bin
The program will ask: 'You are about to Restore MBR, are you sure (Y/N)?'
Type 'Y'
With that, you put the GRUB-s**t back to your MBR.
-----------------------------------------------------------------------------

To solve your GRUB problems:
GRUB sometimes mixes up the boot drive numbers. You have to manually edit the grub config to correct this. But as you can't start Linux, you have to do this from Windows.

So start WinXP (from CD, with GRUB in the screwed up MBR), download Ext2IFS_1_10c.exe from [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)
Install it. Go to the 'Control Panel'. Double Click on IFS Drives (don't know the name anymore, something with IFS in it's name, it will be then only thing with IFS in the name).

Select your Linux partition, select a drive name (z:\ for example). Now go to MyComputer, select z:\boot\grub\menu.lst

Open it with MS-WordPad (if you open it using notepad, you will not have any new lines...)

Somewhere it will probably look something like this:

----------------------------------------------------------------------------------------------
title		Ubuntu, kernel 2.6.20-15-generic

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b78f8799-d1eb-4ab6-9281-9b754eaea4a3 ro quiet splash

initrd		/boot/initrd.img-2.6.20-15-generic

quiet

savedefault



title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b78f8799-d1eb-4ab6-9281-9b754eaea4a3 ro single

initrd		/boot/initrd.img-2.6.20-15-generic



title		Ubuntu, memtest86+

root		(hd0,0)

kernel		/boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Windows Vista/Longhorn (loader)

root		(hd1,0)

savedefault

chainloader	+1
----------------------------------
Now i have installed Vista on my Laptop's internal hard drive, and Ubuntu on a external USB hard drive. It copied grub in the MBR, and it worked fine, except that i couldn't start anything, including windows, if i had not plugged in the USB drive. So i needed to get grub out the MBR as described above with MbrFix, and then see what was wrong.

I found out that all (hd0,0) and all  (hd1,0) had been mixed up. So the only thing i had to do, is to rename all (hd0,0) to (hd1,0), and all  (hd1,0) to (hd0,0) in the menu.lst file. 
Afterwards everything went fine, i could start Windows without having GRUB anywhere on my internal HD, and if i plugged in the external USB HD, it started GRUB, and i could select between Ubuntu Linux-Kernel Version and Windows Vista to boot, and everything, even Vista, worked well :guitar:.

Now you problem probably is something similar, that is to say that you have multiple partitions on hd0, which got mixed up. So you will have to exchange all (hd0,0) with (hd0,1), and all  (hd0,1) with (hd0,0).

Maybe the number after the comma is different, in windows use: 
'MbrFix /drive 0 listpartitions'
To see the partition's numbers. 
(You have to subtract 1, because Windows numbering starts at 1, Linux numbering at 0...)

------
You should see something like:
MbrFix /drive 0 listpartitions
# Boot Size (MB) Type
1  Yes     151001    6  DOS 3.31+ 16-bit FAT (over 32M)
2          1623   12  WIN95 OSR2 32-bit FAT, LBA-mapped
3             0    0  None
4             0    0  None
------
with 1,2,3,4 being the partition's numbers (remember as i said, subtract 1 to get the Linux number)



So far, give it a try, and see whether it works. Maybe it's a good idea to make a backup copy of menu.lst in case what i wrote doesn't work, or you have screwed it up...

However, with my tip you should always be able to remove Grub from your MBR, and get Windows starting again, without having to reinstall it each time :lolflag:...

---

