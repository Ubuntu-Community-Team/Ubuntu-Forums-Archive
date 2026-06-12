---
title: "Triple Booting"
date: 2010-01-28
forum: Apple Hardware Users
---

### Post by Odin Overland on 2010-01-28
Hey everyone.  I am now successfully booting Mac OS 10.6.2, Ubuntu 9.10, and Windows XP on my MacBook 2,1.  I am doing so without rEFIt and did not use the Boot Camp Assistant either.  It was definitely trial and error, especially since every forum post I read on triple booting did not really work for me.

My hope was to write up a "How-To" post on the process.  But since it was a trial and error process, I wanted other people who are successfully triple booting Mac OS, Ubuntu, and Windows WITHOUT using rEFIt and Boot Camp Assistant to also throw in their experience.

---

### Post by Odin Overland on 2010-02-02
I really apologize for not posting my story here yet - but I realized two things:

1) I had a crazy-*** XP SP3 install CD that probably no one else out there will have

&

2) Any solution I post will not have rEFIt as part of the solution.  I successfully triple-booted twice; once without rEFIt and once with rEFIt where I am convinced I did not need it.

I am going to be spending all day tomorrow trying to refine the process and make notes so I can write up a clear "How-To" on how to triple boot without Boot Camp Assitant and rEFIt.

More to come - and other people please post your success stories too!

---

### Post by tonymartin on 2010-02-02
There seems to be alot of people who try to do this, and I am one of them.

I too finally succeeded, and I just posted my info on this thread: [http://ubuntuforums.org/showthread.php?t=995704&page=111](http://ubuntuforums.org/showthread.php?t=995704&page=111)[URL="http://ubuntuforums.org/showthread.php?t=995704&page=111"]

[/URL]  I probably didn't post it in the best place I guess, but there it is.

Enjoy!

---

### Post by CJN on 2010-02-03
I achieved this effect (OS X SL, Win 7, Karmic) by partitioning my drive into thirds (admittedly I used Bootcamp to shrink the original partition, then I used Windows 7's built in partition tool to shrink the second partition) OS X was obviously already installed, and for Windows 7 I just popped in the disc (x64 from a student ISO) and it installed without a hiccup (drivers from OS X cd and now Bootcamp update) all upgrades have worked fine, and as for Karmic I popped in a live cd and it didn't recognize that I had partitioned my windows 7 partition again, so I just guessed how much space to give it at the end of the disc and it installed again without hitch (put grub 2 in /), HOWEVER I had to follow the following instructions to get the boot tables synced (hybrids because OS X uses weird EFI):

Note these are not MY instructions, I didn't write them.

( In this example I assume your disk is /dev/sda , default for macbooks,  and your root partition is /dev/sda4 , adapt these if necessary! )  
1) Download an Ubuntu Live CD ( see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)  ) and burn the ISO to CD.
 2) Boot your macbook from the CD (hold option key at startup if you  don't have rEFIt)
 3) Open a terminal, mount your original root partition
 sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sda4 /mnt/root 
4) Find the correct package for your architecture on [http://packages.debian.org/sid/gptsync](http://packages.debian.org/sid/gptsync)  and download it to somewhere under /mnt/root/
 5) Set up /proc and /dev
 sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev 
6) Chroot into your original system, you're now in your own system.
 sudo chroot /mnt/root /bin/bash
7)  Install the package downloaded in step 4
 sudo dpkg --install gptsync*deb
8 ) Run gptsync on the affected disk
 sudo gptsync /dev/sda
9)  Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a copy  of rEFIt on CD if you're concerned)
 sudo grub-install /dev/sda
10)  reboot, the system should be able to boot again now

Note I had to install the alsa drivers/mixer to get sound and have to do so every kernel update, and I have to follow the above steps every time grub is upgraded.

I can now boot holding option and choose "windows" which loads grub, from which I can boot to win 7 or karmic, and if i boot with no flags it boots to OS X (admittedly a little slower than before I set all this up)

---

### Post by Odin Overland on 2010-02-03
Correct me if I am wrong, but it sounds like you did use rEFIt as part of your solution.

Also, when you divided your main partition into thirds, what format did you use for each of these partitions?  It sounds like your Windows 7 install did not just overtake both of the partitions, which my "crazy XP SP3" CD had a bad habit of doing.

---

### Post by Odin Overland on 2010-02-03
Took forever to get Mac OS installed onto a GPT and then clone it to a MBR computer.  Installing Windows 7 as the second OS now on the GPT iMac.  So far no problems.  Will report back later after Ubuntu install.  It probably will not be until tomorrow when I attempt to get all three OS on the MBR iMac.

---

### Post by ed12348 on 2010-02-03
I have macbook 5,2 triple boot win 7, OSX snow leopard, ubuntu 9.10 karmic and didn't use refit. I did it by doing a bootcamp install of windows 7 and then just installing ubuntu from the live cd using the install alongside in the partition stage, I noticed that this in the visual representation added itself to the end of windows, so I carried on with the install and it placed GRUB in the windows partition. So when I boot if I want linux or windows I hold down the option key, select windows, and am greeted with GRUB. Mac is listed in GRUB but I noticed that OSX wouldn't boot from it. But it all works well for me, had to do all the messing about to get stuff to work for mac, but am happily messing around on it now, in fact this is being posted from my mac in ubuntu without refit (which I decided not to to use when I discovered it voided the warranty from apple)

Hope this helps somebody :D

---

### Post by Odin Overland on 2010-02-03
> **ed12348 said:**
> So when I boot if I want linux or windows I hold down the option key, select windows, and am greeted with GRUB. 

This also happened when using rEFIt too... only two bootable partitions showed up... so why use rEFIt at all is my question.

---

### Post by ed12348 on 2010-02-03
Indeed I have seen rEFIt installed with all three systems listed, but I didn't see the point of messing around with the mac bootloader (by installing rEFIt) for the sake of a couple of extra keypresses.

---

### Post by Odin Overland on 2010-02-08
[FONT=Courier][SIZE=2]So it seems ridiculously easy to Triple Boot a Mac with Mac OS X, Windows, and Linux.  The only thing that made it hard for me my first time around was listening to the instructions of people who had no idea what they were talking about.  I now realize that the instructions I read on the Ubuntu Forums were impossible to carry out (some sadist must have posted the How-To just to watch people struggle).[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Anyway...[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Remember Rule #1 People - Backup your files before doing anything ever![/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]I have also Triple Booted on both GPT and MBR with the same results.  I would recommend most people stay with GPT, but I am still trying to figure out how to boot all three OS from GRUB - and I do not know if this will require the computer to be in MBR or not... so we'll see.  I believe Mac OS X will only do a fresh install to a GPT computer anyway.  Also you must be using an Intel-Based Apple computer (if anyone wants to debate this, feel free to explain to everyone).[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]The easiest thing to do is to start with your entire Mac running Mac OS X.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]So start with:[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]1st Partition: EFI (should be there by default)[/SIZE][/FONT]
 [FONT=Courier][SIZE=2]2nd Partition: Mac OS Journaled /hfs Plus format (With Mac OS X running)[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Next you will use the Mac Disk Utility to create two new partitions.  The first new partition should be formatted as FAT (this will be FAT 32, but Mac Disk Utility only shows it as FAT).  You do this by using the "+" button.  When you create this FAT partition, it should be the total size that you want your Windows, Linux, and Linux SWAP partitions to all add up to.  So for example if you have a 320 GB hard drive, and you want Mac OS to be 150 GB, Windows to be 100 GB, Linux to be around 65 GB, and the SWAP needs to be about 4 GB, you would make your new FAT partition around 170 GB.  You will choose the size you are aiming for, but the Disk Utility will not create everything to your exact specifications.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Once your new FAT partition is created, you will select FAT partition in the Disk Utility and then press the "+" button again to create another partition.  This will initially be another FAT partition, but I recommend changing it to another Mac OS Journaled partition so that if you happen to have a weird Windows install disk like I do, it won't recognize the partition as one it can install on.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]So once you have done all of this, your new partition scheme will be:[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]1st Partition: EFI[/SIZE][/FONT]
 [FONT=Courier][SIZE=2]2nd Partition: Mac OS Journaled (With Mac OS X running)[/SIZE][/FONT]
 [FONT=Courier][SIZE=2]3rd Partition: FAT 32 (Currently Empty)[/SIZE][/FONT]
 [FONT=Courier][SIZE=2]4th Partition: Mac OS Journaled (Currently Empty)[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Next step is to install Windows on your third Partition.  Insert your Windows install disk (anything from XP to 7 should work here).  Restart your computer holding down the "alt"/"option" key on your keyboard.  You should see an icon of a CD/DVD labeled Windows show up in the EFI next to the hard drive icon that you currently boot off of.  Use your keyboard to select the CD/DVD icon and hit enter.  You will then use the disk to format your 3rd Partition into NTFS and install Windows to the 3rd partition.  This experience will be different depending on your version of Windows and disc type obviously, but it should not be too difficult.  Your computer will restart, and unless you hold down the alt key again, it will boot to Mac OS X because you have not yet blessed the new Windows partition.  Either hold down the alt key to select the new Hard Drive icon labeled Windows, if you are booted up into Mac OS X you can go to system preferences and select the Hard Drive icon labeled Windows to restart into (if you use this route, your computer will now by default boot up into Windows... which will be easier for the rest of this process - and is completely reversible).[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Once you boot back into the Windows Hard Drive partition, the installation will continue or complete.  Another restart may be required in order to set up your Windows and load up the desktop environment.  Don't worry about using Windows update and installing Boot Camp just yet... you can do this later.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Now, insert your Linux install disc, and restart your computer again holding down the "alt"/"option" key on the keyboard.  The EFI will display your Linux install disc as CD/DVD icon again labeled Windows.  Use the keyboard to select the CD/DVD icon and hit enter.  You will now boot up from this install disc.  Again, depending on which version of Linux your are using, this will be different for you.  I am accustomed to using 9.10 Ubuntu derivatives, so that is what I will base these instructions off of - even though I have triple booted using other Linux builds.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Choose the install Ubuntu option.  Choose your language, time zone, keyboard etc, and then you will come to the partitioner.  Select the final option "Select Partitions Manually" and then hit forward.  You will select your fourth partition that is currently selected as hfs +.  You will then click the delete button to remove this formatting.  After a rescan, this partition will now show up just as free space.  Select the free space that follows your Windows partition, and then click the "add" button.  You will now create your SWAP partition.  Choose to add this to the end, and enter the size of the partition in MB (remember, this should be approximately twice the size of your computer's RAM).  Choose to use as a "swap area", and then hit okay.  You will then go back to the partitioner, and you will see the free space again, this time between your NTFS Windows partition, and your SWAP area.  Select the free space again, and again click the "add" button.  Again, choose to place this partition at the end. You can use the rest of the space that remains in this free space, so you do not need to resize it if you wish.  You will then use this as either an ext 3 or ext 4 file system (your needs may differ on what you need, I use ext 4 on my personal computers, but my work requires ext 3).  Then you will select the "/" as the mount point.  Click the "format the partition" box so that it is checked Click okay.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Now, back at the partitioner, click the ext file system you just created so that it is highlighted.  Now click the forward button, and finish the install.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]If all goes well, after you restart your computer you can hold down the "alt"/"option" key so that the EFI shows only two icons, a hard drive with your Mac OS X partition, and an icon that shows a partition labeled Windows.  Select the one labeled Windows.  Instead of your computer loading up the Windows OS, GRUB should load.  GRUB will then list all three OS: Mac OS, Windows, and Ubuntu.  You can use GRUB to boot to either Ubuntu or Windows.  If you try to boot to Mac OS from GRUB, your computer will simply restart - hence me trying to figure out how to boot Mac OS from GRUB 2 still.[/SIZE][/FONT]
 

 [FONT=Courier][SIZE=2]Anyway, that's it!  You can now boot your Intel Mac into all three operating systems.  Once you have done this one time successfully, it is truly a cakewalk.  I went into a lot of detail for anyone trying to attempt this the first time with no background like when I first attempted it.  Feel free to ask any questions or make any comments.[/SIZE][/FONT]

---

### Post by CJN on 2010-02-09
Sorry I haven't been around to reply, I know the instructions say to use refit, (I just copied and pasted them because they're not mine to edit) but you can safely (as I do) skip that.

---

### Post by Odin Overland on 2010-02-09
> **CJN said:**
> Sorry I haven't been around to reply, I know the instructions say to use refit, (I just copied and pasted them because they're not mine to edit) but you can safely (as I do) skip that.

No biggy.  rEFIt just doesn't seem to work like it is intended to for most people without some extra work, which in its current version makes it more of a hassle than a blessing in my opinion.  I am still racking my brain try to get GRUB2 to boot Mac OS X... then a cleaned up GRUB2 menu would be the only required boot loader... and exactly what I need for a triple-boot lab machine where I work.

---

### Post by Odin Overland on 2010-02-12
Still have not found an answer to booting Mac OS X from GRUB2 - but there is a bug filed here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/388135](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/388135)

I would encourage anyone else that wishes to boot Mac OS X from GRUB2 and cannot to log in and click the link that says this bug affects you too (which can also be done by click this: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/388135/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/388135/+affectsmetoo))

The importance of this bug has not yet been determined even though it has been filed for months.  If more users attach themselves to this bug maybe we can get some attention for it, especially with the Ubuntu Global Jam (especially the "Bug Jam") coming up.

Thanks

---

### Post by Unioniste on 2010-02-19
Hello ! I have a MacBook Pro 5,5 with MacOS X Snow Leopard and Ubuntu 9.10 Karmic.
I used BootCamp to install Ubuntu and installed rEFIt after. Now I want to install Windows 7 but when I put my DVD and begin to install, Windows ask me for the drivers, I think they are on MacOS X DVD, but it's impossible to eject Windows DVD. Do you have a solution for me please ??

[Sorry for my English, you know that French only know 1 language ;)]

Thank you,
Calixte.

---

### Post by Odin Overland on 2010-02-19
I don't know if Windows will let you install from where you are.  I have no idea about the drivers you are speaking of.  Boot Camp is only for after the Windows installation is complete, and that will be on your Mac OS X DVD.  I only know how to triple boot the way I posted, and it works just fine without rEFIt.  I ran into nothing but problems trying to put Windows on after-the-fact.

---

### Post by Unioniste on 2010-02-19
Thanks for your answer !
I search every where for the Windows 7 drivers on Macbook Pro on the web, but I find nothing... :( I read somewhere that the drivers where in BootCamp if you don't use it, or if the install is completed, so there aren't on my MacOS X, but maybe you have they and can send it to me ??

Thanks,
Calixte.

---

