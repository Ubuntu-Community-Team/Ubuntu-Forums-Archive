---
title: "How exactly to install Ubuntu on External HD?"
date: 2010-10-21
forum: Apple Hardware Users
---

### Post by northerlywind on 2010-10-21
Sorry if this has been asked before; I checked the documentations and topics but it doesn't seem to be explicitly stated. So how, exactly, could I go about installing on an External HD? I run Mac 10.5.8 (Leopard), 3rd generation Macbook. Help? Thanks!

---

### Post by Nwwmac on 2010-10-22
I don't think booting Ubuntu from an external disk is possible. OSX and Ubuntu / Windows use different boot processes and you need to use either boot camp or rEFIt to get them to boot off the same internal disk. Neither boot camp or rEFIt supports booting from an external disk. 

It would be great if they did, wouldn't it? :)

---

### Post by scienceandcake on 2011-03-12
So, the forum I was following is like 3 years old, so I can't post my solution there, so here it is! I'll post some pics in my album of my handwritten instructions. It's wordy. It's for beginners. I'm a beginner. My Ubuntu isn't even 3 hours old, but it works.

The old forum I read was [http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030) 
I'd say it's still a useful read.

I use a Late 2008 Aluminum body Macbook. Core 2 Duo. 10.6.6.

- back up your stuff
- have an ethernet connection ready
- have an ubuntu live CD (I'm using 10.10, 32bit)
- grab some tools to pull out your internal hard drive 

[LIST=1]
[*]Assuming you already have the external, turn on your mac, attach the hard drive, go into spotlight. Type in disk utility and select it to open.


[*]On the left you should see your external listed. Go ahead and click on the drive. Click on the erase tab. Where it asks you the format, choose MS-DOS (FAT). Go ahead and erase the drive and have it formatted for this.  This is probably the most important and most key step in the whole process.

Some people like to partition the drive - I did in my first attempt, which didn't work for a multitude of reasons, but here is how you do it if you want: 


[LIST]
[*]Go to the partition tab in disk utility, where says "current scheme" click that dropdown menu and choose 1 partition. On the right you can name it if you like. There is then an advance option. CLICK THIS. Select Master Boot Record for the partition table type. Now, go ahead and partition your drive. 


[*]The reason I say this doesn't matter to partition, is because I used the Ubuntu install disk to do this task.
[/LIST]

So now your Live CD is in your optical drive, and your external is ready to have an install put on.


[*]Shut down your mac. Don't bother trying to boot the live CD with the internal HD still in there...it can be done, but eh. For now just play it safe and pull out the drive. Personally, after a failed attempt, I got tired of pulling out my HDD and putting it back in, so I did it through a crappy Dell, but it's the same.


[*]If you're using a laptop, pull out the power adapter. Take out the battery. Unscrew the mounting plate thing from the hard drive. Gently pull the drive from the SATA cable. Gently remove. Put the battery back in. Attach the power. Attach the external.


[*]Start up your mac and as soon as you hear the sound, or see the screen light up, hold down the OPTION key. Keep holding it. You'll see a picture of a CD. Mine said 'Windows' but whatever. It's your live CD. Click that. You are now booting from CD.


[*]Click install Ubuntu.


[*]When it asks you to choose a partition, select to do this manually. You can try to let it just erase and write. I didn't try this as I was very particular my second time around. Go for it if you want. You can skip the next 5 paragraphs if that works.

Some key information here is that Ubuntu requires 2 partitions to run - one that is sort of a startup, asking you which OS you want to run called the Swap, and the other with the OS itself. Also, until you click install, nothing is formatted, rewritten, everything is preserved.


[LIST]
[*]So in the manual section, asking you about partitions, click on your hard drive. The names are weird, so choose it by the size. Click on the main hard drive, not the subgroups listed. Click on NEW PARTITION TABLE... click continue. You should now have a partition that says 'free space' if i remember correctly. 


[*]Now click on the hard drive again, and click add (Or it's click on the free space and click change). What you should see is a CREATE A PARTITION window. You need to create that bootable partition, known as the Swap. This needs to be double your amount of RAM. I went with 5GB to be on the safe side (5000MB).


[*]So in this window, select PRIMARY. When asked about the use, press SWAP. I don't think you can set the mount with swap selected, but if you can it's "/" in the dropdown menu. Okay. save this. You should be back to the listed drives.


[*]Click Add/Change again. Designate the remainder of the free space for Ubuntu. Select PRIMARY. When it asks for format, choose 'EXT4'. Mount is "/". Save this. You should be back to the listed drives.


[*]At the bottom of that window, it asks where to install the bootloader. SELECT THE EXTERNAL! It should also be the only one there if you removed your internal. Okay... now... check...aaand
[/LIST]


[*]INSTALL! Answer questions, wait for it, be sure you've got internet connected. Will it work on your Mac now!? 

NO. Your mac still won't read it. It will try to restart. I got errors. I pressed enter, it tried to restart, stuff didn't boot. Shut down the computer. Detach the hard drive. Reassemble your mac. Pull out the power supplies, and reattach the hard drive. Plug them back in. Restart your computer. If you attach your external it will say it can't read it when you connect the hard drive, and will also not do anything but start OS X when you hold option. One last process.


[*]You need to make it so your computer sees this as a bootable drive. So go online and download rEFIt. It's not under warrantee, but it works. Download the disk image. Run the installer .mpkg. 

[http://refit.sourceforge.net/](http://refit.sourceforge.net/) 

Okay! Attach your external! Restart your computer! Hold down option! and you should see an Apple and a Penguin and some other stuff. select the Penguin. Press enter. The next thing you'll see is GRUB which lists Ubuntu versions... it will load the one you want by default, but you can select it and Voila! Linux on a mac.
[/LIST]

I hope that helps. 

Mine is running beautifully, no lag, but I still need to figure out how to get iSight, Multi-touch trackpad and number of other things up and running, but on a base level, it works great.

---

### Post by dubmartian on 2011-03-12
good info. i would stress any alum macbookpros made after 2008 might have problems booting linux from any usb device.

---

### Post by scienceandcake on 2011-03-13
> **dubmartian said:**
> good info. i would stress any alum macbookpros made after 2008 might have problems booting linux from any usb device.

aww boo. how come?

---

### Post by C.S.Cameron on 2011-03-13
Following step by step for Full install of 10.10 to external USB drive, partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "NTFS file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

