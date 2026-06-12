---
title: "How do I get to boot setup on a Mac Mini"
date: 2008-06-05
forum: Apple Hardware Users
---

### Post by SouthernPott on 2008-06-05
I picked up a Mini at a garage sale last weekend because it supposedly wouldn't boot.  No OS X disc.  It seems to boot up fine but I can only get to the user screen which has three users showing and I don't know the passwords.

I am wanting to put on Ubuntu.  I inserted the disk, restarted the computer, held down the C key, and it still loads OS X.  I tried restarting and tapping the C key.  Same thing.  Tried several other keys and combinations.  Nothing so far.

Any help or thoughts?  Also I am using my Ubuntu 8.04 disk that I made from the desktop i386 link.  Is this the correct version?

Thank you.

Malcolm

---

### Post by ditsch on 2008-06-05
> **SouthernPott said:**
> Is this the correct version?

That depends. if it is an old mini it has a G4 PowerPC processor. For these minis the PPC version is needed: [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

Only newer minis have an Intel processor.

---

### Post by SouthernPott on 2008-06-05
Thank you.  Evidently my eyes don't read fine print very well.  I see where it says it is a 1.42G4 on the bottom edge.  Thanks for the link.

---

### Post by cyberdork33 on 2008-06-05
just FYI, you can start in Single User Mode to get root permissions. Then you should be able to change the root password, and login as root at the login screen.

To boot into single user mode, you hold cmd+s during bootup. (If you do not have an apple keyboard, try alt)

---

### Post by SouthernPott on 2008-06-05
Unfortunately, it did not come with an Apple keyboard.  Tried the Alt button with c and s but neither worked.

---

### Post by cyberdork33 on 2008-06-05
OK sorry, the Windows key acts as the command key. I just tried it!

---

### Post by SouthernPott on 2008-06-05
I set it all aside for now.  It came with a smaller keyboard that had a Fn key in the lower left.  Tried that with no luck.  Will plug in this keyboard and try the Windows key later.

Thanks for the help.

---

### Post by SouthernPott on 2008-06-06
Purchased a new Apple keyboard today while I was picking up some other items.  Pressed Command + s button and it booted into this screen:

standard timeslicing quantum is 10000us
vm_page_bootstrap: 125639 free pages
mig_table_max_displ = 70
81 prelinked modules
Copyright (c) 1982, 1986, 1989, 1991, 1993
      The Regents of the University of California. All rights reserved.

using 1310 buffer headers and 1310 cluster IO buffer headers
USB caused wake event (EHCI)
Firewire (OHCI)Apple ID 31 built-in now active, GUID 001451ff fe166d0; max speed s400.
CSRHIDTransitionDriver: :probe: -s
CSRHIDTransitionDriver: :probe booting in single user .. do not match
Security auditing service present
BSM auditing present
disabled
rooting via boot-uuid from /chosen: C89D190c-8108-38A1-9406-B488336B7091
Waiting on <dict ID="0"><key>IOProviderClass</key><string ID="1">IOResources</string><key>IOResourceMatch</key><string ID="2">boot-uuid-media</string></dict>
Got boot device = IOService:/MacRISC2PE/pci@f4000000/AppleMacRiscPCI/ata-6@D/AppleKauaiATA/ATADevice
Nub@0/IOATABlockStorageDriver/IOATABlockStorageDevice/IOBlockStorageDriver/ST9808211A Media/IOApplePartitionScheme/Untitled@3
BSD root: disk0s3, major 14, minor 2
Singleuser boot -- fsck not done
Root device is mounted read-only

If you want to make modifications to files:
    /sbin/fsck -fy
    /sbin/mount -uw /

If you wish to boot the system, but stay in single user mode:

   sh /etc/rc
localhost:/ root#


I am in over my head as usual.  What next?  Also, because I put my copy of i386 Ubuntu cd in the drive, I need to get it out.  How do I accomplish this?

Thanks again for the help.

---

### Post by SouthernPott on 2008-06-06
The smiley faces are incorrect of course, nice as they are.  Should have been a colon followed immediately by a p so it reads colon probe.

---

### Post by cyberdork33 on 2008-06-06
as you can see at the end, you are at a root prompt. You can pretty much literally do anything from here. 

I suggest using the 'passwd' command to change your root user's password. (You might have to mount the root filesystem first. How to do that is shown on the screen (modifying files...).

after you have set a root password, you can reboot normally, and at the login, you can login as root. As root, you can create / delete users. Don't use the root user as your normal user though, that is quite dangerous. If you really need help with the Mac stuff, you can go to any local Apple Store and they will usually be glad to help.

P.S. There is an eject button on your apple keyboard to eject the cd.

---

### Post by SouthernPott on 2008-06-06
Thank you again. I will work from your directions and then look things up as I go.  Just needed a starting point.

Yesterday I was trying to switch back and forth with the keyboard and mouse from this computer and it was mostly a losing effort.  Now I have them set up side by side with separate mice and keyboards.  I really like the slim lines of the Apple keyboard even though I wasn't keen on buying on.

---

### Post by SouthernPott on 2008-06-06
Found the eject button.  Excellent.

---

