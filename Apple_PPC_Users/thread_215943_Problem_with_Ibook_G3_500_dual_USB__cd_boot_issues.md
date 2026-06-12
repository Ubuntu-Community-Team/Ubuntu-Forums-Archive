---
title: "Problem with Ibook G3 500 dual USB / cd boot issues  / solved - Dapper"
date: 2006-07-14
forum: Apple PPC Users
---

### Post by alipsius on 2006-07-14
Like the post title says, I dloaded the ubuntu-6.06-desktop-powerpc.iso
from:

[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-powerpc.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-powerpc.iso)

and it would not boot in the ibook G3 500. When I booted the ibook back into panther, it would not even recognized the cd when inserted. The md5 sum checks out, the cd is readable and bootable in both my ibook G4 12" 1.2 and in my G5 tower. I could not figure out for anything why.

I reset the open firmware by booting with cmd-opt-O-F and did

reset-nvram
reset-all

and when it rebooted holding down the C key, it boots off the hard drive like it does not see the cd. Disk Utility sees the cd in the drive but wont mount it.

I also zapped the PRAM. I searched the forums here for like the past 3 hours and found lots of other info but nothing specific to solve this issue, also google either turned up nada or thousands of 'not really the answer to my problem'.....

I read in the forums here about using the 'alternate' installer ISO, and I began dloading that thinking I would try it if nothing else worked.

So I tried the following:

Put the cd in the combo drive of the ibook G4 and booted that machine in firewire target disk mode by holding down the T key after power on. And then reboot the ibook G3 into panther just to see if it was something funky with the burned cd and the cdrom drive on the ibook G3.

Result: Nada.

Then I booted from a Hoary livecd (I could not locate the Breezy livecd at the moment), and it booted no problem. It took better than 5 minutes to get to the desktop but it booted. No firewire devices showing tho. Not sure if they would. I did not have another firewire cable to test, but I had just used this same cable to make a backup image of the panther config from the ibook G3 (in target disk mode) onto my G5 using disk utility.

While I was waiting forever for the Hoary live cd to load, I located the  Breezy live cd. 

I rebooted the ibook G3 into panther and inserted the Breezy cd, and it mounted on the desktop, so I figured I might try something, and it worked.

What I did was, shutdown the ibook G3, power it on, and then immediately hold down the option key. When I saw the icons for the hard drive and cd rom drive I knew it saw the disc partition on the cd. I then repeated this procedure with the Dapper cd, and it did not show. So, I again repeated with the Breezy cd. The Breezy cd showed up.

There must be something different about the boot loader or format of the Dapper cd that OpenFirmware does not like.

So I am thinking for a minute, and knowing that  OpenFirmware now has accepted the cd disc as a boot device, I ejected the Breezy cd (I had to use a toothpick into the eject pinhole on the drive) and then inserted the Dapper CD. and selected it as the boot device, and clicked the right-pointing arrow, and held my breath.

And....(drum roll please) TADA. Boot process began. Total time delta to desktop was about 45 seconds.

SO, what it seems is that this machine is not totally compatible with the Dapper cd boot sector. The Breezy CD and Hoary CD are both the same brand media from the same box, so I dont think it is media, although we all know about the quality control myths on blank CD's.

I was so excited at seeing this work, that I came right here to tell everyone, just in case someone else is struggling with the same issue.

Also I dont have the airport card installed, but I do have a D-Link DWL-g120 usb wifi adapter that I picked up at KMart on clearance for like $12 that I am going to try to use with this machine in Dapper. I hope it works.

Right after I send this note, I am going to click on the installer and see what happens, I'll post a followup here either way.


If you have any other ideas please let me know.

Adam :>

---

