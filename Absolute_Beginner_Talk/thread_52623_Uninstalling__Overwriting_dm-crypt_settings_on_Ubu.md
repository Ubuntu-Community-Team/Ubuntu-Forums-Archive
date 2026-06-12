---
title: "Uninstalling / Overwriting dm-crypt settings on Ubuntu?"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by fyrefly on 2005-07-28
Somedays I wonder why I just don't leave things alone when they are working just fine. 

 :roll: 

I had a DriveCrypt partition in on my windows drive, and since I couldn't find anything compatible for both windows and linux, and I spend more time in linux, I decided to create a new partition for linux that would be encrypted & move everything over. I followed the Ubuntu guide here:
[https://wiki.ubuntu.com/EncryptedFilesystemHowto?highlight=%28crypt%29](https://wiki.ubuntu.com/EncryptedFilesystemHowto?highlight=%28crypt%29)
[Using dm-crypt, #1-6]

The linux encryption, though I didn't like how it asked for the passphrase at boot up, at was working well... UNTIL I had the great idea to remove the drive crypt partition and free up space.

The Linux partition is at the end of the 80GB windows hard drive. Ubuntu is on it's own 40gb drive. 

I can still get into linux, but it's not recognizing the encrypted drive now and doesn't ask for the passphrase.  There is an error with the recognition on boot up and I need to  press ctrl + D to bypass it.

Finally :P

My question ...

Is my best option to remove the dm-crypt so I can reinstall / configure it new? And how?

Or can I run through the instructions in the guide above and it will overwrite the previous settings that no longer are working when I removed the drivecrypt partition?

I thought I could just delete from fstab there's lines ::

/dev/hda5       /media/crypt  vfat    iocharset=utf8,umask=000   0       0
/dev/mapper/crypt /crypt reiserfs defaults 0 1

But then I thought that might not help or make things worse. 

The partition tables look like this now :
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdb1     ext3     37G  3.5G   32G  10% /
tmpfs        tmpfs    126M     0  126M   0% /dev/shm
/dev/hda1     vfat     50G   33G   17G  67% /media/windows
/dev       unknown     37G  3.5G   32G  10% /.dev
none         tmpfs    5.0M  2.8M  2.3M  56% /dev

The 10gb encrypyed drive for Ubuntu isn't there - if I re-mount it, would that help?

---

