---
title: "Have XP &amp; Vista - how to add Ubuntu"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by kasvi on 2007-03-04
Okay. Im going nuts. I tried several times installing Ubuntu, XP & Vista.. For a reason or another Ubuntu stopped starting telling cannot mount device error 17. I tried fixing the GRUB but it didnt do a thing. 

So I installed XP and Vista and have a working dual boot. 

Is it possible to add Ubuntu now without enormous hazzle? I don´t feel like giving up. I wanna make it work. :D

I once had Vista.. installed Ubuntu and the GRUB worked nicely. I could choose the operating system. XP & Vista boot is working now.. will the GRUB work as it did before? Or does the existing dual boot make it more difficult?

---

### Post by hoagie on 2007-03-04
If windows (Xp & Vista) are installed a clear install of Ubuntu will configure Grub, to give you the option to boot to Ubutnu (default) and then Windows XP, Windows Vista.

---

### Post by unisol on 2007-03-04
you could try this:This HowTo was inspired by molly_001's dual boot tutorial.

GOAL: To allow a PC to boot into three operating systems from one hard drive: Ubuntu, Vista, and XP. 

NOTE: THIS METHOD DELETES ALL DATA ON YOUR HARD DRIVE. If you wish to try Vista without losing your data, I recommend this tutorial by Loffe_.

Requirements: -Ubuntu 6.06 Desktop CD (or DVD)
-Windows Vista Beta 2 DVD
-Windows XP Install CD
-A lot of free time
(You do not necessarily need an ethernet connection for this howto, but it is highly recommended)


PART 1: PARTITION YOUR HARD DRIVE
1. Back up all data you wish to save. You will be completely deleting everything on your hard drive in this part of the tutorial.
2. Insert the Ubuntu desktop CD into your CD drive and restart your computer . At the Ubuntu menu, choose "Start or Install Ubuntu" to boot into the live Gnome desktop.
3. Go to System -> Administration -> Gnome Partition Editor. Your current hard drive partitions will appear as colored boxes. Select each box and press the delete button. If you have a swap partition, you will have to right-click it and choose "deactivate" before you can delete it.

In the next step, you will need to create 4 partitions. The minimum amount of space each partition needs is given below. (1GB is more than adequate swap space for the average user.) You should end up filling your entire hard drive with these four partitions:
1.) NTFS (or FAT32) for Windows XP: at least 4GB
2.) NTFS for Windows Vista: at least 10GB
3.) Ext3 for Ubuntu: at least 3GB
4.) Swap for Ubuntu: ~1GB

4. Click "New" to create each partition as a primary partition in the preceding order. Make sure you choose the correct file system before clicking "Add." It's also a good idea to write down the details of your partition to help keep them straight. For example, this is what I wrote down when I partitioned my 60GB hard drive:
Partition 1: 15360MB, NTFS, Vista
Partition 2: 20480MB, NTFS, XP
Partition 3: 20368MB, EXT3, Ubuntu
Partition 4: 1024MB, Swap

5. Click "Apply" to permanently erase all data on your hard drive and repartition it for a triple-boot installation.


PART 2: INSTALL WINDOWS XP
1. Close GParted and restart your computer. When your CD drive opens automatically, replace the Ubuntu CD with your Windows XP CD and hit enter.
2. You should boot up into the Windows XP Installer. Choose "Setup Windows XP Now" to begin the installation. Refer to your notes to choose the appropriate partition on which to install Windows XP. If given the option, I recommend reformating the partition using NTFS, but you can choose any formatting procedure that you wish.
3. From here on out the XP installation is self-explanatory. I leave it to you.
4. OPTIONAL. Once you have successfully booted into Windows XP, I recommend that you get online and go to update.microsoft.com to update your Windows software. Reboot as necessary until it shows no more available updates. (Just for the record, I had to reboot nine times!  ) 


PART 3: INSTALL WINDOWS VISTA
1. Insert the Vista DVD into your drive and restart your computer. DO NOT install Vista from within XP. Let your computer boot up from the DVD, choose your desired settings, click "Install Now," enter your serial number and accept the license.
2. When you are given the choice, click "Custom (advanced)" for the installation type. Selec the appropriate partition. NOTE: The Vista partition should be the only choice where the number in the "Total Size" column is equal to the number in the "Amount of Free Space" column. Click "Next."
3. From here on out, the Vista installation is surprisingly simple. I trust you can handle it alone. When it's finished, you will have a dual-booting system between Vista and XP.

If your OS installations have been correct so far, you'll notice that when you restart your computer, it brings up the Windows Boot Manager, which lets you choose between "Microsoft Windows" (Vista) and "Earlier version of Windows" (XP). We'll use the Windows Boot Manager to our advantage when installing Ubuntu later on.

4. OPTIONAL: ENABLE AERO INTERFACE. It's no secret that many of us want to try Vista mostly for the Aero Glass interface. Here's how to activate it. Make sure you are connected to the internet, and go to the Windows Welcome Center (the Welcome Center is the window that pops up automatically when you start Vista). Click "More Details." Click the yellow box under "Windows Activation" and hit "continue" in the resulting permissions popup. Proceed to activate your copy of Vista. When done, run Windows Update. If Windows Update did not successfully find a driver for your video card, go online to find and install Vista drivers. Then go to the Control Panel and find your Windows System Performance Rating. Click "Refresh my rating now" and proceed with the ratings diagnostic. When it is finished, you should have Aero enabled. You may need to restart your computer. **Note: Please don't litter this thread with Vista help requests. There are plenty of other forums where you can do this.


PART 4: INSTALL UBUNTU 6.06
1. Insert the Ubuntu Desktop CD into your computer and boot up into the live GNOME desktop. Double-click "Install" to begin the install process.
2. Choose your desired language, user name, etc... When you get to the "Prepare disk space" step of the installation, choose "Manually edit partition table," and click "Forward." Since we already partitioned the disk in Part 1, click "Forward" again to skip this step.
3. You should now be at the "Prepare mount points" step of the installation. Choose the EXT3 partition as the mount point "/" and the swap partition as "swap." you can reformat these two partitions if you desire.
4. Click "Forward" and then "Install" to continue with the Ubuntu installation. You can play a game in Applications -> Games while it is installing. I prefer Mines.  . After a while, the installer will reboot your computer.

You'll probably notice that the GRUB menu only lists Ubuntu and Windows XP. DON'T PANIC! This is perfectly normal. If you choose Windows XP at the GRUB menu, it actually loads the Windows Boot Manager, where you can choose between Vista and XP.

5. OPTIONAL: CHANGE GRUB MENU CHOICES. As far as I know, it's not possible to bypass the Windows Boot Manager. However, you can change the menu options.

Code:
sudo gedit /boot/grub/menu.lstAt the bottom of the file, you'll find something like this:

Code:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1You can change the "title" line (but not the others) to whatever you like. Here's mine:

Code:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Boot Manager
root		(hd0,0)
savedefault
makeactive
chainloader	+1
That's it! Congratulations, you are now triple-booting!
    

testube_babies 
View Public Profile 
Send a private message to testube_babies 
Send email to testube_babies 
Find all posts by testube_babies 
Add testube_babies to Your Buddy List 

Reply 


« Previous Thread | Next Thread » 

 vBulletin Message  
  
Cancel Changes 
  #3    2 Hours Ago  
BongoBob  
5 Cups of Ubuntu
   Join Date: Jan 2006
Beans: 33 

 
 Re: Dual booting Ubuntu 6.06.1 and Vista RC1 

--------------------------------------------------------------------------------

I'm also dual booting dapper and Vista RC1. How did you fix your GRUB?

Thanks in advance.
  

BongoBob 
View Public Profile 
Send a private message to BongoBob 
Find all posts by BongoBob 

  #4    38 Minutes Ago  
kalpik  
First Cup of Ubuntu
   Join Date: Jul 2006
Beans: 5 

 
 Re: Dual booting Ubuntu 6.06.1 and Vista RC1 

--------------------------------------------------------------------------------

1. Boot from Live CD

2. Open a Terminal. "Type sudo grub"

3. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

4. Type "root (hd0,3)".

5. Type "setup (hd0)". (That's a zero)

7. Type "quit".

8. Restart the system.

---

