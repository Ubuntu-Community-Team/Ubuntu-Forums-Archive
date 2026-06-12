---
title: "Macbook boot broken after installing 11.04"
date: 2011-09-12
forum: Apple Hardware Users
---

### Post by antiigrav on 2011-09-12
Hi everyone.

Can I please have some help to fix the EFI boot on my Macbook Pro? Its seriously broken after installing Ubuntu 11.04

Here is the sequence of events and my attempts to fix the problem:

1. OSX on partition 1.

2. rEFIt installed and set to appear on every boot - everything still working fine.

3. Installed Ubuntu 11.04 on partition 2 - at the end it said Grub was installing on the hard-drive.

4. Macbook, after shutdown, makes a long tone and has a blank, BLACK, unlit screen (ie with no Apple logo). Does not boot or do anything. Does not respond to Option key. After many power cycles, the Macbook finally boots to rEFIt menu. 

5. Synced partition table with rEFIt and shutdown.

6. Same as step 4, after many reboots I can load rEFIt then OSX or Ubuntu.

7. I ran rEFIt enable-always.sh script to bless it again - result same as 4.

8. I used OSX's Startup Disk utility to select OSX hard-drive - result same as 4.

9. I then used OSX install-DVD to totally format hard-drive and re-installed OSX - result same as 4.

10. Many more attempts of steps 5 to 9 - result same as 4.

11. Finally, after poking around in the USB port with a screwdriver, a hologram of a female projected out the side of the Macbook and said "Help me Obi-Wan Kenobi. You&#8217;re my only hope".


Thank-you for any help or advice.


  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro5,4
  Processor Name:	Intel Core 2 Duo
  Boot ROM Version:	MBP53.00AC.B03
  SMC Version (system):	1.49f2

---

### Post by devitol on 2011-10-07
Did you find a solution to this?  I am in the same situation?  Can't even POST on any reboots to try to flash EFI.

Please let me know.

---

### Post by johnmurrayvi on 2011-10-08
> **antiigrav said:**
> Hi everyone.

Can I please have some help to fix the EFI boot on my Macbook Pro? Its seriously broken after installing Ubuntu 11.04

Here is the sequence of events and my attempts to fix the problem:

1. OSX on partition 1.

2. rEFIt installed and set to appear on every boot - everything still working fine.

3. Installed Ubuntu 11.04 on partition 2 - at the end it said Grub was installing on the hard-drive.

4. Macbook, after shutdown, makes a long tone and has a blank, BLACK, unlit screen (ie with no Apple logo). Does not boot or do anything. Does not respond to Option key. After many power cycles, the Macbook finally boots to rEFIt menu. 

5. Synced partition table with rEFIt and shutdown.

6. Same as step 4, after many reboots I can load rEFIt then OSX or Ubuntu.

7. I ran rEFIt enable-always.sh script to bless it again - result same as 4.

8. I used OSX's Startup Disk utility to select OSX hard-drive - result same as 4.

9. I then used OSX install-DVD to totally format hard-drive and re-installed OSX - result same as 4.

10. Many more attempts of steps 5 to 9 - result same as 4.

11. Finally, after poking around in the USB port with a screwdriver, a hologram of a female projected out the side of the Macbook and said "Help me Obi-Wan Kenobi. You’re my only hope".


Thank-you for any help or advice.


  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro5,4
  Processor Name:	Intel Core 2 Duo
  Boot ROM Version:	MBP53.00AC.B03
  SMC Version (system):	1.49f2


Which version of the install disk did you use? Did you try to install Ubuntu as a single boot system?

---

### Post by devitol on 2011-10-08
I used 11.04 and tried to install alongside OSX.  After the booting issue I deleted Ubuntu through the EFI prompt and now all I get is a black screen, but the on the 5 boot the SuperDrive kicks in.  The next boot after that, I get the blinking sleep light and the long dreadful beep...

---

