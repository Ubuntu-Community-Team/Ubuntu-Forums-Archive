---
title: "PowerBook G4 12&quot; - CDRW no longer works."
date: 2007-09-09
forum: Apple PPC Users
---

### Post by akaSG on 2007-09-09
Hello,

the cdrw drive on my power book has stopped working. It draws the disc into the machine thinks for about 10 seconds then pushes it out. This is not ubuntu specific as it does the same when I boot into the OS X part of my box.

any ideas,  thanks.

akaSG

---

### Post by anemptygun on 2007-09-24
Is it the combo drive or the super drive?

---

### Post by stmiller on 2007-09-24
Drives do go bad after time. But it might just be a dirty lens. From radio shack you can buy a CD and DVD lens cleaner, which is a special CD with little brushes to clean the lens.

---

### Post by anemptygun on 2007-09-24
Dirty lens would be a cheap fix like stmiller said try it out.

---

### Post by anemptygun on 2007-09-24
If it's not the lens, then you might just have a broken drive.

[http://www.ifixit.com/PowerBook-Parts/G4-Aluminum-12-Inch-Combo-Drive/IF153-044](http://www.ifixit.com/PowerBook-Parts/G4-Aluminum-12-Inch-Combo-Drive/IF153-044)

---

### Post by guidop on 2007-09-25
If you are replacing the optical drive, you can also buy a new, non OEM, Super Drive for about the same amount of money from these guys:

[http://eshop.macsales.com/MyOWC/Upgrades.cfm?Model=188&Type=Internal+Optical+Drives&sort=a]("http://eshop.macsales.com/MyOWC/Upgrades.cfm?Model=188&Type=Internal+Optical+Drives&sort=a")

I did this fix on my 12" Powerbook when my OEM Superdrive failed.  The new drive works great, but its A LOT OF WORK to replace it on the 12" Powerbook.  To replace the Optical Drive, one has to remove:  Battery, Memory, Keyboard, Top Case, Hard Drive, Modem, Power Converter, Frame, Heatsink, and Unmount the MotherBoard before finally getting to the Optical Drive.  See attached photo.   

ifixit.com has instructions, and, usually a choice of new or used Combo and/or Super drives:

[http://www.ifixit.com/Guide/Mac/PowerBook-G4-Al-12-Inch/53]("http://www.ifixit.com/Guide/Mac/PowerBook-G4-Al-12-Inch/53")

If you use a non OEM drive, you'll also need to run Patchburn before you can use the Mac OS to burn disks with it:

[http://www.patchburn.de/]("http://www.patchburn.de/")

---

### Post by anemptygun on 2007-09-25
> **guidop said:**
>  To replace the Optical Drive, one has to remove:  Battery, Memory, Keyboard, Top Case, Hard Drive, Modem, Power Converter, Frame, Heatsink, and Unmount the MotherBoard before finally getting to the Optical Drive.  


Wow I never would have imagined it would take that much work.

---

### Post by akaSG on 2007-09-25
Thanks to all for your suggestions.

I've given it a blast of clean air. I'll try the disc cleaner.

If no luck with that I'm going to try an external firewire drive.

akaSG

---

### Post by anemptygun on 2007-09-25
I hope something works out for you :)

---

### Post by akaSG on 2007-11-23
To end this small story, today my LaCie DVD writer arrived. 

Thanks for everyones help.

akaSG

---

### Post by anemptygun on 2007-11-23
wow that took a long time...

---

### Post by akaSG on 2007-11-25
Another plea,

having spent the time whilst waiting for the drive to arrive reading various postings about booting from external cd/dvd drives, I've been unable to work it out, other than I may need to amend the yaboot.conf file to point at the drive. Any one know of the way to go?

I'm running 7.04 dual with OSX, on a G4. The new drive is the 2D laCie drive. Firewire and usb2.

Thanks 

akaSG

---

### Post by guidop on 2007-11-25
IIRC, this should work for you:*

With external CD drive and Powerbook off, connect them via the Firewire (not USB) cable and plug in the CD drive power adaptor.

Turn the drive on, the eject button on the drive should let you open it and insert the Ubuntu install CD.

Boot the Powerbook, holding down the option key until you see disk icons start to appear.

Once the drive scan process finishes, you should be able to select and boot from the Ubuntu CD.
(If it doesn't work the first time, boot into OSX, make sure you can see the install disk, and try restarting and holding down the option key when the machine restarts.)

The remainder of the install process should be the same as if you used the built-in CD drive.

I'll assume you know what you're doing regarding partitioning the hard drive.

You may wish to search the forums to see how to get your boot splash screen working using framebuffer mode with the nvidia graphics card.  I also use wicd for WPA wireless.


* I've done an OSX install this way.

---

### Post by Lindarose84 on 2007-11-25
I too have a Powerbook G4 12" (1Ghz) with a CDRW drive that doesn't work and I am successfully dual booting Tiger and Ubuntu 7.10. It took me a couple of days to figure everything out but now, knowing what I know- it shouldn't take more than a few hours to get everything up and running. 

First off, I botched everything from the getgo and pretty much wiped my system clean not by choice. So I used another mac with a CD drive, put that mac into target disk mode and held down the option key on bootup on my mac. This gave me the startup screen where I chose to boot from the CD drive on the other mac which had the mac os x install cd. First, I needed to partion my now clean hard drive. Using the install cd, I had the option to partion the drive. I made 3 partions- two were of about equal size (to hold Ubuntu and Mac) and the third was much smaller to hold the apple bootstrap partition. Once that was done, I installed Mac onto one of the partitions. 

Next, I wanted to install Ubuntu. For this, I decided to do a net install (so obviously you'll need a working internet connection). So I went into the Mac OS and put the four files for yaboot that I downloaded online (yaboot, yaboot.conf, vmlinux, initrd.gz) onto the root of my hard drive. Next, I booted onto the Mac Open Firmware screen which I got to by holding down option, command, O and F at boot. Once there, I entered "boot hd:, yaboot" and was taken to the black yaboot screen where there was a boot prompt. I typed in "install" and was taken to the net installation of Ubuntu 7.04. Once it came time for me to enter my partition options, I manually edited my partitions. Obviously, you don't touch the partition you installed Mac OS on. Just concentrate on the other two partitions you created. I went to the larger of the two remaining partitions and assigned that as my ext3 partition and used it has my root partition by designating it as "/" in the options. Then I went back and assigned the smaller partition as the "Apple_Bootstrap" partition and used it has "/boot". Now I needed "swap" space. Documentation suggests it should be at least 256mb, but I didn't think that to be hard and fast so I saw some "free space" on the partition menu in the amount of 134mb and then chose that to assign as my swap space. I continued with the installation with no problems. 

At boot, I got the yaboot menu to choose with OS to boot into. I ran into some graphics card problems which I resolved with the aid of following directions from this site. I don't remember the specifics but I know it had something to do with xorg.conf and changing my graphics card setting on the first screen to "nv" for nvidia. Once I got the graphics issue worked out, I went into Ubuntu and also resolved the airport wireless issue also with the aid of this site (you have to download a file starting with "bcm..." I dont' recall. 

To upgrade to 7.10, I simply went to the "system" menu and selected update manager and went through the upgrade process to Gutsy. It wasn't at all difficult- I just let the process run and rebooted back into 7.10. Simple. 

Now for Mac OS. I originally installed 10.3 and just yesterday, decided to upgrade to 10.4 since I had the CDs. But unfortunately, I no longer had access to another Mac. So this is where the external DVD drive comes in. I found an external USB DVD drive that actually allowed me to boot from the CD. I purchased the drive from Target and it worked beautifully ([http://www.target.com/External-DVD-RW-Drive/dp/B000HC7694/qid=1196027781/ref=br_1_10/602-6288521-4243056?ie=UTF8&node=366462011&frombrowse=1&rh=&page=1](http://www.target.com/External-DVD-RW-Drive/dp/B000HC7694/qid=1196027781/ref=br_1_10/602-6288521-4243056?ie=UTF8&node=366462011&frombrowse=1&rh=&page=1))
I simply plugged the usb cord in, and at boot up, I held the option key, and the mac os CD showed up and I simply booted from that into the Tiger installation. I installed it onto the partition previously holding 10.3. Once the install was done, I no longer saw the yaboot boot menu when I started the computer so I had to reboot, hold option and boot manually into Ubuntu. Once there, I went to terminal, and entered "sudo ybin -v" and the yaboot menu was restored. 

So that's it. Hopefully, this will help others that have this same problem and it's a relatively easy setup. Had I seen a post like this, I would've saved myself days of headache. To the OP, it IS possible to boot from an external DVD drive- one which is even USB instead of firewire. It could be that it's just an issue of finding the right external drive that works. The one from target should do the trick. good luck!

---

### Post by akaSG on 2007-11-26
Thank you both.

I only get sporadic internet access at the moment, so I'll go away and try your suggestions.

I'll post as to how it goes.

akaSG

---

### Post by akaSG on 2008-02-20
thanks to all the suggestions.

Finally got to boot from firewire Lacie external DVD drive.

I've lost who posted the post that suggested using :

comd-opt(alt)-O-F  , to get into open firmware

then : boot fw/node/sbp-2/disk:,\install\yaboot

Thanks again.

akaSG

---

