---
title: "Edgy to Feisty= caa caa"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by memyselfnie on 2007-12-04
Hyyas, noticed this morning update manager had a couple, so I went ahead with it, no problems.
Then, with my 2nd cup of coffee in hand, I decided to take the plunge, and go for the big button,
7.04... left it unattended for over an hour... came back to an apparently normal desktop, upgraded??? ... reboot... froze.   MY BAD, wasn't broke, shouldn'a tried to fix it.  Worked great for @year, oh well, opened case, unplugged dual boot xp/edgy drive plugged in backup 6.06lts backup 
drive, back in Ubizness!   (always, always pack a backup drive!!!!)  
To the point:  How best to retrieve the files that are not backed up?  I have no problem wiping the 
fubared upgrade,  (should) be easy... but I'd hate to lose something important.  
Machine is networked to other Ubuntu machines,  but I am not certain how to safely mount the drive, without screwing it up, particularly the xp part.

---

### Post by ajgreeny on 2007-12-04
With an external usb drive attached and using the ubuntu live CD (you have one I presume?), you can mount the old 7.04/7.10 and copy the data you need to the usb drive easily without any danger of corrupting the data files.  Simply mounting drives does nothing to the files on that drive other than make them available and copyable, so don't worry.  If you have no external usb drive it is a bit more difficult as you can't burn a CD or DVD unless you have two CD/DVD drives available on your machine.

Alternatively you could try adding the old 7.04/7.10 drive to another ubuntu machine, mounting it and then copying the files you need to the working ubuntu on that machine.  You'll probably need to find the device name for the mount command using ```
sudo fdisk -l
``` but then I think it should work OK, unless, that is, I've forgotten something basic.

---

### Post by memyselfnie on 2007-12-04
Thanks, the machine does have 2 cd drives, and i do have a couple of usb sticks, but I think the other alternative sounds good.  If I just rejumper the 2 drives, making the xp/edgy drive a slave, and the dapper drive master, I should be able to access the edgy drive ok, without disturbing the xp partition?  I can live with what I have,  just as long as I don't mess up anything else.  
The machine is currently downloading 7.10,  I'm gonna give that a whirl  (after I backup the xp partition)  but if my limited experience is correct, that will not "fix" the original install's problem.  
I have mounted network drives, but never mounted another drive with dual o/s partitions on it.  
That's my main concern, not so worried about the edgy partition, I'm afraid of improperly accessing
the drive and somehow screwing up XP.  
I would rather not ever do another windows install, if I can avoid it.

---

### Post by ajgreeny on 2007-12-04
If you can get the data off the original 7.04/7.10 drive that you need you should then be able to simply do a clean install of gutsy in place of your borked ubuntu tou have at present.  Not sure about "rejumpering" as you call it as that may upset the booting completely and grub may not be found as it will probably now be on the slave drive not the master.  Try it but don't be surprised if it won't boot.

---

### Post by memyselfnie on 2007-12-04
Sorry, I guess I''ve been confusing.  The "backup" drive is in the machine, but is normally not 
connected physically.  It has my first installation of 6.06, with it's own grub.  I occasionally connect it, and boot to it,to transfer files to, from the network.  I then pull the power plug, and ribbon cable  for safekeeping.   
 The dual boot drive, XP/ EDGY 6.10, (normally the only drive connected)  could be connected as a 2nd drive, with the "backup" drive as the boot drive.  Shouldn't require any change to grub, to mount it as a 2nd drive, and allow me to remove the data.  Basically doing as you suggest, it's just the same computer.   Only thing I'm not sure of, is how 6.06 will affect the xp partition, if at all.

---

### Post by ajgreeny on 2007-12-05
Shouldn't affect it at all.  Good luck.

---

