---
title: "External harddrive permission problems"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by GeneticFlea on 2007-11-26
hey everyone, i just bought a used Wiebe Tech  firewire 800 with 200gb hd, off ebay and im having some trouble getting write permissions for it. Heres what ive done so far:

The drive came to me not yet formatted, so i installed gparted through synaptic, ran the partition program under sys--admin, and reformatted the majority of the drive from hfs or whatver it was originally to Ext3. theres an odd 32 kb partition also that has an exclamation by it, but gparted wont let me format it, it just gives me an error.

anyway now that its formatted, it shows up under /media/disk .... however if i right click on it and try to create a folder its grayed out and im told i dont have the necessary permissions to do that action. Now im the only user on this computer, so it shouldnt be an issue. I read through other posts and tried  "chown Username:username /media/disk" in the terminal. That allowed me to change edit what was in the los tand found folder, and add files to the disk, just not create folders(i could create folders under lost and found but not on the main disk drive, i also couldnt delete anything. oddly enough the lost and found folder told me that its owner was geneticflea(my username) but the harddrives main area said it was owner of root. i then looked in my fstab( very new to this just following what others say) and saw no entry for sdb2(name of the harddrive in gparted) so i followed a direction to add it. Now the harddrive wouldnt even show up when i plugged it in. i tried deleting my entry, but now it still wont show up at all. 


im really clueless. its a harddrive in a Wiebetech enclosure, could that be the problem? some hardwired security i dont know about? i just tried to run the harddrive in windows, it plugged in ok, and windows said it was working properly, but its not showing up under my computer. any help would be appreciated!!!

---

### Post by jken146 on 2007-11-26
Hi there.  This should be completely fixable.

If you backed up your fstab before changing it, restore that.  If not, don't worry.  Have a look at this guide: [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

What you did wrong when setting the permissions was you didn't make the chown operation recursive (apply to all the files within the folder that represents the drive).  Use the option -R to do this (again, see that guide).

If you want to know more about permissions, see this: [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

If you want to mount the drive in Windows, you need an appropriate driver for the ext3 filesystem.  [http://www.fs-driver.org/](http://www.fs-driver.org/) is a site with such a driver.  Download the windows installer.

---

### Post by GeneticFlea on 2007-11-26
thanks man! that worked like a charm! hours of frustration today all solve din 5 minutes. thanks !!!

---

