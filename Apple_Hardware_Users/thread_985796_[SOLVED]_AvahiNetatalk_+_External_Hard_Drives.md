---
title: "[SOLVED] Avahi/Netatalk + External Hard Drives"
date: 2008-11-18
forum: Apple Hardware Users
---

### Post by rshnike on 2008-11-18
Hi everyone.
New user of Ubuntu. Installed the latest version for AMD64 Desktop. I've set up a file share, scan share and print share but been having some trouble with my external hard drives.
I have 2 external hard drives mounted, one is a 2.5" 80GB used for media and the other is a 40GB 3.5" that is used for Time Machine for my mac laptop. I plugged both into my Ubuntu box to see if I could serve them over my network and not have to plug them directly into the mac.

Both are formatted as HFS+. I've tried to write to the drives from the ubuntu box but it seems I can't, even though I've chown -R root and chgrp -R root.

I followed all the directions here:
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#avahi2](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#avahi2)

and installed avahi and netatalk. I can login from my laptop with the username and password as well as access $u (the /home/<user> folder) without problem. However when I try to access either of the two external drives I get an error that they cannot be accessed because the original cannot be found. I see that a couple of other people seem to have this problem but from what I've come up with in a search nothing has worked yet.

Originally the time drive wasn't even showing up on the mac, but when I renamed it to all lowercase with no spaces now it shows up.

Both drives are listed in my AppleVolumes file.

Obviously I'm assuming to fix it one would need to see some sort of log or to view my configuration file so if anyone would be so kind as to let me know what you would need (and how I would be able to get that information) I would post that.

Thanks a lot for your time.

---

### Post by cyberdork33 on 2008-11-18
Linux cannot write to a journaled HFS+ volume. You will need to disable journaling first in order to write to the mounted external hard drives.

Secondly, if you are planning to permanently leave the hard drives attached to your fileserver, then I would HIGHLY recommend the use of a Linux-native filesystem such as ext3. This will eliminate several issues when working with HFS+ (support for HFS+ is not that great in Linux) and probably make the drive access time a bit faster.

Having your Time Machine Backup on the network is not that great of an option either. There are issues with getting Time Machine to work with a networked volume, and it is very difficult to restore anything should the need to reinstall OSX arise. I would leave it hardwired to your Mac when you want to backup / restore files and not worry about setting it up with your file server.

---

### Post by rshnike on 2008-11-18
Thanks a lot for the response I appreciate it.

I don't much care that the linux box itself won't write to the drive as long as the mac can. I'm not quite sure of the underlying principle at work here with netatalk. When I try to write to the drive from a mac does the mac do the drive write or it tells the linux box to? i.e. If I choose not to turn journaling off (the benefits of which I haven't even looked into yet though I'm sure I wouldn't need whatever they are) would I be able to write to the drive from the mac laptop or that wouldn't work either?

The reason why I'm reluctant to convert to ext3 is because the 80gb drive I take with me when I go out of the house, I only wanted to plug it in when I get home so that I could serve the media files that were on there. The majority of the use of this drive though would be on a mac, which I assume likes HFS+ better...

The Time Drive I wanted to permanently leave plugged in to the linux box so that when I got home the laptop would automatically start backing up to the time machine drive without having to go upstairs to plug the cable directly into the laptop and leave it plugged in while it backs up.

Cheers.

---

### Post by cyberdork33 on 2008-11-18
> **rshnike said:**
> I don't much care that the linux box itself won't write to the drive as long as the mac can. I'm not quite sure of the underlying principle at work here with netatalk. When I try to write to the drive from a mac does the mac do the drive write or it tells the linux box to? i.e. If I choose not to turn journaling off (the benefits of which I haven't even looked into yet though I'm sure I wouldn't need whatever they are) would I be able to write to the drive from the mac laptop or that wouldn't work either? You mac does not see the actual hardware over a network share... essentially, the "filesystem" used by the remote machine is the sharing format (samba, netatalk, or whatever), the server application running on the linux box trnslates this information into the files it actually stores on the drive. I have never used netatalk specifically myself, but for other fileservers I have used, it does not matter as long as the server hardware can access the filesystem.

and yes, you would like to have journaling enabled. It will definitely help protect your data. Any modern linux filesystem also uses journaling (I think that ext2 is only thing that is used sporatically today that does not)

> **rshnike said:**
> The reason why I'm reluctant to convert to ext3 is because the 80gb drive I take with me when I go out of the house, I only wanted to plug it in when I get home so that I could serve the media files that were on there. The majority of the use of this drive though would be on a mac, which I assume likes HFS+ better...

That situation makes things a bit more difficult then. FAT32 would be the most compatible filesystem between them all, but it has it's limitations (specifically a 4gb filesize limitation). NTFS can be used between them both, but requires drivers in OS X. ext3 and other native linux filesystems are pretty much out of the question.

> **rshnike said:**
> The Time Drive I wanted to permanently leave plugged in to the linux box so that when I got home the laptop would automatically start backing up to the time machine drive without having to go upstairs to plug the cable directly into the laptop and leave it plugged in while it backs up.This sounds nice in theory, I know. I used to have mine setup similarly, but it makes things a bit difficult if you had to reinstall OSX and restore files from the Time Machine Drive over the network. Plus, unless you startup from a Mac that is turned off, you would likely have to connect to the share manually everytime you wanted to backup anyway. This might be completely different on the Time Capsule that Apple mackes because, well, they have the priviledge of creating things to work correctly together...

---

### Post by rshnike on 2008-11-19
> **cyberdork33 said:**
> 
This sounds nice in theory, I know. I used to have mine setup similarly, but it makes things a bit difficult if you had to reinstall OSX and restore files from the Time Machine Drive over the network. Plus, unless you startup from a Mac that is turned off, you would likely have to connect to the share manually everytime you wanted to backup anyway. This might be completely different on the Time Capsule that Apple mackes because, well, they have the priviledge of creating things to work correctly together...

I guess I'll try out NTFS then for the portable drive. As for the Time Drive it would seem I'm out of luck. Bit jealous of your cross-platform knowledge, heh. Thanks a lot for your help.

---

### Post by samden on 2008-12-10
Post removed by author

---

### Post by ElectricBlue on 2008-12-19
> **cyberdork33 said:**
> Linux cannot write to a journaled HFS+ volume. You will need to disable journaling first in order to write to the mounted external hard drives.

Secondly, if you are planning to permanently leave the hard drives attached to your fileserver, then I would HIGHLY recommend the use of a Linux-native filesystem such as ext3. This will eliminate several issues when working with HFS+ (support for HFS+ is not that great in Linux) and probably make the drive access time a bit faster.


I have a similar issue. First, is there a safe way to disable journaling on the HFS+ volume (I have access to OS X if that's required)?

If that's too diffucult/risky is there a good way to reformat without losing my data?

I'm new to this cross platform file system business.

---

### Post by cyberdork33 on 2008-12-19
> **ElectricBlue said:**
> I have a similar issue. First, is there a safe way to disable journaling on the HFS+ volume (I have access to OS X if that's required)?

If that's too diffucult/risky is there a good way to reformat without losing my data?

I'm new to this cross platform file system business.

yes, you can disable journaling on HFS+ volumes ONLY in OSX:

```
sudo diskutil enableJournal /dev/disk0
```
Replacing "/dev/disk0" with the disk you want. Bear in mind that the above is not a typo, it is supposed to read "enableJournal" even though we are trying to disable Journaling, this is due to a bug that labelled the Volume as Journaled when it wasn't.

 After you have run the above run:
```
sudo diskutil disableJournal /dev/disk0
```
verify that it says Journaling has been disabled.

---

### Post by ElectricBlue on 2008-12-21
Worked famously. thanks

---

