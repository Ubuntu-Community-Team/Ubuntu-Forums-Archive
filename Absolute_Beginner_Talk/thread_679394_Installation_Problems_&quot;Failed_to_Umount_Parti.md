---
title: "Installation Problems: &quot;Failed to Umount Partitions&quot;"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Hitam269 on 2008-01-26
I was just given an Ubuntu installation disk from a neighbor, and the live boot worked fine, but I've had a few problems when trying to install it.  First of all, I would like to install it, ideally, on a partition of my computer's main C:/ hard drive (SCSl1 / sda1, I think).  But this didn't work out because the smallest partition it will let me select is around 30 GB, and I only have about 20GB free on that drive.  But if that is difficult to solve, I can also install it on an external USB hard drive.  Again, ideally, this would be installed on a partition of this drive around 20 GB in size.  The first few times I ran the installer, it allowed me to select this drive and select a portion of it for installation.  Since then, though, for some reason, it will not allow me to partition the drive; I can only install Ubuntu on the full (120GB) drive.  (The resize SCSl3 (my external HD) option was replaced by an option to resize SCSl1 (my internal HD))  Although this isn't ideal, it's not really too big of a problem; I could install it on the full 120GB external HD.  When I try to do this though, I go through all of the steps of the installation, except for the 7th step, where the installation / partition stops around 15% and tells me:

Failed to Unmount Partitions

The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/WD\040Passport

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

Go Back | Continue

Whichever option I select, the installer takes me back to step 4 of the installation.  I tried doing a umount command in the terminal, but I was told that either that "/media/WD\040Passport" had already been unmounted or was not mounted.  It is possible that I typed in the command wrong, but I have not tried again because I'm not sure unmounting the HD through the terminal is something I should be doing at that point in the installation.  If anyone has any suggestions, I would really appreciate them.  What is most important to me is just getting Ubuntu to install without erasing the current contents of my internal hard drive (the external hard drive's current contents don't really matter, and it doesn't matter too much where ubuntu is installed).  Thank you in advance.

- Ethan

---

### Post by drowner on 2008-01-26
You should definitely be able to select a partition smaller than 30 gig.

And, something is open that is not allowing you to unmount your Western Digital USB drive.

Which would you rather install it on.... the hard drive, or the USB? The HD will be easier, unless the USB is permanently attached to your computer. Both are possible, which would you prefer.

---

### Post by Hitam269 on 2008-01-26
I thought it had to be something related to the USB drive being open or still in RAM or something, but I have restarted Ubuntu and gone straight to the installation, and I still get this same problem.

Even after defragmenting it, the internal hard drive is still somewhat fragmented, so I think the USB drive would be better. And it will not be permanently attached to the computer, but the vast majority of the time it will be.  And for the time it is not attached, I plan to just run Windows from the internal hard drive.

---

### Post by drowner on 2008-01-26
It can be a tricky little install, putting it onto an external USB drive.

The reason is that you need to install grub to the hard drive, but make sure it has all its files with it, otherwise it will look for them on your USB and not work.

Alternatively, if your BIOS can boot from USB then you can install the GRub to the USB, but it is complicated!

Do a search on that particular topic

---

### Post by Hitam269 on 2008-01-26
Searching through these forums just now, I found someone who had an issue similar to mine.  That thread is at [http://ubuntuforums.org/showthread.php?t=475354](http://ubuntuforums.org/showthread.php?t=475354) and jmo8795 gave some advice which may be applicable to my problem, but I'm not sure.  Anyway, here is what he said:

> Hi guys,

Daniel,

I can't help with the Wubi issues, however, I may be able to help you get your CD-ROM drive detected which would allow you to perform a standard install.

I also installed Feisty recently on a Dell Latitude X200 and ran into the same issue with the CD drive not being detected (the drive is in a media base that the laptop connects to).

I was able to get it to recognize the CD drive by manually specifying the drive location during the install process as /dev/scd0.

Steps I followed are outlined below:

1. I burned an alternate install .iso and started the install in text mode.
2. After the installer loads and you partition your HD, select a keyboard layout, etc...the installer tries to detect a CD drive and fails. It then asks if you want to install a driver from a disc.
3. Select the "No" option. After doing so, the installer asks you if you want to manually specify a drive location.
4. Select "Yes" and select "None" when prompted to enable additional services/drivers. You will then see a prompt that will allow you to input a specific drive location.
5. Input /dev/scd0 and the installer should then be able to detect the drive.

This worked for me with the CD R/W in the media base. I'd think this would also work for an external firewire or USB drive.

Those steps are from memory, so if they are slightly inaccurate or out of order I apologize.

Hope this helps. Sorry I can't give any insight on Wubi but I've never configured that before.

Good luck.

I am not installing with Wubi and my problem is with my USB drive, not my CD drive, but does anyone know if this solution or some similar solution could be used in my case?  I don't know much at all about Linux, so I'm afraid to go beyond the standard installation procedure without knowing that it won't cause any harm.  And I am trying to install on a Dell computer if that is at all relevant. Thanks.

---

### Post by Hitam269 on 2008-01-26
Thanks.

I'll check on that and let you know what happens.

---

### Post by drowner on 2008-01-27
That isn't what you are looking for. In that situation somebody is trying to install, but during the install process their drive is not being recognised.

Your drive is being recognised, its just currently in use.

And also, if you want to install to a USB drive, you really should have a good read about it first. It is not easy, although it can be done. The first thing you will need to know is if your computer can boot from USB drives, or not. (Not an ubuntu issue)

---

### Post by Hitam269 on 2008-01-27
drowner, thanks again for your help.

I figured out that the cause of my particular problem was that the Ubuntu disk was set to mount my external HD when it recognized it, and for whatever reason the installer could then not unmount the drive.  I solved this by changing the settings for the drives not to mount drives automatically.  After that the installation worked fine.  I had another problem with grub (Error 21) but I may have found a solution to that, and I posted that in another thread.

---

### Post by puna11 on 2008-04-04
Hi,
I am facing the same issue. However I am a completely newbie to ubuntu and am trying hard to install it and start using it.

I thus still have not figured out a way to install ubuntu on my external HDD even though I am able to partition it as i please and at 15% it gives me the Failed to unmount errors.

Please help!!!

Thanks,
Puna11

---

