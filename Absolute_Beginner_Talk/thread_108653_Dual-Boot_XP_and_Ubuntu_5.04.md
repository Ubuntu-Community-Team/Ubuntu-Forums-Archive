---
title: "Dual-Boot XP and Ubuntu 5.04"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by decoomzaLP on 2005-12-26
First of all I'd like to say Hi to all at Ubuntu. Being umuntu myself and exhibiting the spirit o ubuntu and all.

I  have a not so moer se problem here, but am stumped, . . . obviously. 

I have two Hard Drives on my PC. The Primary is loaded with Win XP Pro with Office XP Pro and lots of data files.

On the second, the slave, I have installed Ubuntu 5.04, and i used the onscreen directions. Went through the GRUB setting and then had to reboot.

When rebooting the Message appears"

"GRUB Loading Stage 1.5.

GRUB Loading, please wait . . . 
Error 21"
and the infamous blinking cursor.

How do i sort the dual boot problem? I want to install Open Office and other OSS wares to run on Ubuntu, and now am dead on me tracks.

---

### Post by Sokraates on 2005-12-26
As an immediate "solutiton", should you need to fix the problem urgently, you can alway use the recovery-console on your WinXP-CD. Typing "fixmbr" will rewrite the Master Boot Record and you will be able to start XP. Of course, GRUB and Ubuntu will be ignored.

For any real solutions (i.e. fixing GRUB) you will need access to your linux-partition. For this best use a live-CD.

According to the [GRUB Manual](http://www.gnu.org/software/grub/manual/grub.html), your error means

[HTML]Selected disk does not exist
    This error is returned if the device part of a device- or full file name 
    refers to a disk or BIOS device that is not present or not recognized
    by the BIOS in the system.[/HTML]

Usually you have this sort of problem with external HDs or RAID-devices. If I read your post correctly, neither is present in your case.

The devices loaded by GRUB are found in /boot/grub/menu.lst. Please post the content of this file together with more info on your system (IDE- or SCSI-drives, number of partitions etc).

**Edit:** Just found [this](http://lists.debian.org/debian-user/2005/02/msg00415.html). Please take a look at your BIOS and tell us, whether both HDs are corrctly recognized.

---

### Post by jimrz on 2005-12-26
Welcome

[**[COLOR="Sienna"]Here[/COLOR]**]("http://users.bigpond.net.au/hermanzone/") is an excellent guide for setting up dual boot. It is based on a 5.04 intall but also works properly for 5.10. which, if you can get before you start in again, would be better to go with than 5.04.

A couple of weeks ago I did my first ever linux install (XP/ubuntu). First time I installed I tried to put both on my master drive and got similar errors. What I did was [1] booted again from the install disc [2] deleted all of the ubuntu partitions that I had just made ***MAKE SURE THAT YOU SELECT THE LINUX DRIVE AND NOT YOUR WINDOWS***[3] booted from the "live" cd to check that the partitions were indeed gone [4]booted again from the install cd and installed, following the above mentioned guide, ubuntu 5.10 to my slave drive. This time everything went perfectly and still is operating perfectly. 

Good luck  -  jim

---

### Post by Landice on 2005-12-26
LoL.. too bad i din read this post earlier... I've encountered the same error last nite, what i did is i just use the windows recovery console to fix the MBR and then re-installed my linux.. :(

---

### Post by decoomzaLP on 2005-12-27
Hi Thanks for the assistance.

The GRUB issue has been sorted out. I used CMOS settings abd its now running GRUB OK. Only to Hit a second snag.
Ubunty 5.04 First Boot Failure (Dual Boot with XP Pro) - 30 Minutes Ago 
GRUB worked, and I chose the Ubuntu option. Initially it runs and then it halts after:

"Pivot root: No such file or directory
/sbin/init: 428: Cannot open dev/console: No such file
Kernel Panic - not syncing: Attempting to kill Init"
(and the blinking cursor)

 How do I sort this one out?

The PC is an old AMD K6 333MhZ with 256MB RAM and running XP Pro on the first HD. So am Dual-booting XP and Ubuntu.

---

### Post by az on 2005-12-27
Grub error 21 means there is a discrepancy between what grub thinks is the hard drive where the latter stages of grub are stored and where the linux kernel thinks they are.

Often, you solve the problem by editing the /boot/grub/device.map file.

You seem to have solved this problem with your bios settings.  However, now your linux kernel cannot find itself or the filesystem.

What did you do to your BIOS (CMOS) and what are your hard drive partitions like?

---

### Post by az on 2005-12-27
I forgot.

To edit a file on a partition you cannot boot, boot the installer and let it set up your keyboard and such,

CTRL-ALT-F2 will get you into a console

mkdir tmp
mount /dev/hda3 /tmp
nano /tmp/boot/grub/device.map

---

### Post by decoomzaLP on 2005-12-27
You wrote: However, now your linux kernel cannot find itself or the filesystem.

What did you do to your BIOS (CMOS) and what are your hard drive partitions like?

Ans.
How does one editthe /boot/grub/device.map file?
At the blinking cursor, I am stumped as to what commands to activate, being a Linux "blind man".

What I did?
I noticed that the 2nd HDD was reflected as 0MB and the CD_ROM set as rimary slave. So I changed the setting to TYpe: to USER, and also changed the cable select (basically swapped the CD-Rom and the HDD). In this case the Slave HDD, was correctly set as 10GB, and Ubuntu read the correct drive details.

However, when starting up Ubuntu (XP works super), it display the error:
"Pivot root: No such file or directory
/sbin/init: 428: Cannot open dev/console: No such file
Kernel Panic - not syncing: Attempting to kill Init"
(and the blinking cursor)

Ironically though, it now fails to boot from CD rom. 'd tried the live CD, Win XP as well as the 1.44" stiffy. zilch boot from them. I am now stumped. Its been ages since I fiddled on a PC, and i'd forgot many a setting commands.

I am tempted to complete format the slave, but I am unable to fix MBR first, so it points only to Win, . . . 'cause cant boot from CD.

I am on ISM (lucky@mailbox.co.za) and the PC is not the PC am using, am on notebook with GPRS-Bluetooth net connection through cell.

---

