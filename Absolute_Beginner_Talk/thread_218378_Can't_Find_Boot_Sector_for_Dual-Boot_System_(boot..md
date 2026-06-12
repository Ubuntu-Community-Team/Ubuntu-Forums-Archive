---
title: "Can't Find Boot Sector for Dual-Boot System (boot.ini -&gt; GRUB method)"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Astravian on 2006-07-18
So after wracking my brain on this problem, I believe I've found a solution, but I'm missing one step. I'm going with the XP / Dapper 2 hard drive dual-boot system and my current method for getting into Linux is a bit indirect.

Right now, no matter how I have the jumpers or cables set up on my drives, Windows bullies the BIOS into booting first :mad: , even though I switched the Linux drive to cable-select master when I installed it. The only way I can bring Linux up is by either unplugging the Windows drive, at which point the BIOS will freak out but eventually find Linux and boot, or I can tell the BIOS each time to boot the master (Linux) drive by F12ing. There is no option for this in the BIOS menu's boot sequence. I can only select to boot from the C:\ drive (which somehow means which ever drive is Windows) and the CD-ROM drive.

Now, when Linux boots, GRUB comes up and works just fine. It even has an option for Windows and will boot XP if I so desire. This leads me to believe that GRUB was not written to the MBR, but I can't remember what I did. I can tell you that I created three partitions on the Linux drive and left the Windows drive alone. hda1 is ext3 for the Linux install, hda2 is linux-swap and hda3 is fat32 for Windows to Linux file sharing.

After searching the forums and internet, I'm pretty sure I should go with the method outlined [here]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html"). This is the "Edit boot.ini to add a file that contains the boot sector for linux, have it default to linux so it brings up GRUB and use that instead" method. 

So I ran this command, where "/bridge" is the name of my fat32 partition: 

```
sudo dd if=/dev/hda1 of=/bridge/linux.bin bs=512 count=1
```

I moved the file to the C:\ drive in Windows and then added this line to boot.ini.

```
c:\linux.bin="Ubuntu Linux"
```

But all that was put in the file were 0s! The above mentioned link suggests making a /boot partition in hda1, but I had not done this. So now it's time for my actual question!

**How do I figure out where the bootable sector is??**

Everything else seemed to work, but with the linux.bin file being all 0s, it just booted to nothing. I appreciate any help with getting this to work properly. Hopefully, one day I'll understand Linux enough to drop Windows forever.

---

### Post by hanexar on 2006-07-18
I can't anwser directly to your question, but it seems to me that you have a problem with your grub installation, since it should start first even if your BIOS point to a Windows HDD.  You should check for tread to enable grub over windows.

---

### Post by confused57 on 2006-07-18
I've never booted Linux with Windows boot.ini file, so I can't help you there.  
Here's how I have my system setup, maybe there's something that'll help:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Astravian on 2006-07-18
Thanks for the replies.

I'm not quite sure if there really is a problem with the GRUB install. It works fine once I force the BIOS to boot from the Linux drive.

> ...it should start first even if your BIOS point to a Windows HDD

If the BIOS points to the Windows drive, then why should it start first? It's booting in the order listed in the boot sequence. Unfortunately, the boot sequence does not have a choice for IDE Master or Slave, just C:\ or CD-ROM.

Confused57, I looked at your thread, but that was the procedure I initially followed. As soon as I plug the Windows drive back in, it immediately wants to boot Windows again. And doesn't care about Linux anymore. I'm on a Dell Dimension 4600 and I believe it has something to do with the Dell BIOS being in cahoots with Microsoft.

Does anyone else have any thoughts on finding the boot sector Ubuntu is using without a /boot partition?

---

### Post by confused57 on 2006-07-18
Sorry the method I outlined didn't work for you.
I have a Dell Dimension 4550, I had to update the bios from A02 to A08 in order to install SP2...probably not your problem, but you may want to check Dell for a possible bios update.  My bios boots to hd0 automatically, evidently the 4600 bios is setup differently.

If you don't mind grub being installed to your Windows mbr, you could connect the Windows drive as master(hda) and Ubuntu as slave(hdb) and reinstall Ubuntu(to hdb), selecting to install grub to the mbr(Windows).

At least I bumped your thread...good luck.  Maybe someone who's experienced your problem can offer you a solution.

---

### Post by Jax Kovak on 2006-07-19
Not really an answer but a workaround that I use myself. Mount a floppy disk, and change:

```
sudo dd if=/dev/hda1 of=/bridge/linux.bin bs=512 count=1
```

to...

```
sudo dd if=/dev/hda1 of=/media/floppy/linux.bin bs=512 count=1
```

If your floppy mount is not /media/floppy/ then just change that bit to suit. Once you have the file on the floppy disk you can boot into windows and copy it across.

---

### Post by falcon15500 on 2006-07-19
Your method sounds fine to me.  The only way I have ever gotten dual boot to work is with the method you describe (using NTLDR to boot into GRUB).  The command you are entering (DD) seems fine, as the first 512 (less actually, but 512 will do) should contain the boot sector.  I have no idea why it is reading zeroes?  Sorry!

falc

Edit: Oh, I don't have a seperate /boot partition either. Have you tried the dd command with just /dev/hda rather than /dev/hda1 ?  Not at my linux boxen at present, so I can't check...

---

### Post by Astravian on 2006-07-19
Well, unfortunately, I don't have a floppy drive. Didn't think I would need one. :???: 

I actually did try using the "dd" command with hda instead of hda1 and the file it created did have something other than 0s in it. But that something was in hex and I had no idea if it was right. But I still tried adding it to the Windows boot.ini file and this time when I tried to boot to Linux with the Windows boot loader it just said "GRUB" at the top with a blinking underscore. 

Who knows, maybe this is a promising. Would it hurt to try pulling more than 512 bytes? I don't know, any more thoughts?

Thanks for the replies.

And BTW, I did update the BIOS. Dell is up to version A12. :D

---

### Post by falcon15500 on 2006-07-19
This is more promising... What it means is that NTLDR is correctly loading the first stage (or stage and a half?) of GRUB, hence the display.  It doesn't appear to be getting all the way, however.  Maybe some research on GRUB will help you?

And no, I wouldn't grab more than 512.  Probably wouldn't do anything - but it isn't needed.  What you need is in less than 512 (472 or something or other).

falc

---

### Post by cptInsane0 on 2007-07-24
I am having the same exact problem, except I know where the boot folder that contains grub is.  I use the exact same code, and create it.  Right now I'm not getting anything at all.  Earlier, I installed it to /dev/hda1 instead of (hd0), which is the same thing, but not to grub.  Doing that, however, made GRUB appear and sit there.  Now that I installed grub to (hd0), when I view ubuntu.bin it is blank.  Of course, this makes nothing but a blinking cursor appear.  There has to be an easier way to do this.  Is there just some file I could copy?  I see all the visible files inside the boot/grub folder.

---

