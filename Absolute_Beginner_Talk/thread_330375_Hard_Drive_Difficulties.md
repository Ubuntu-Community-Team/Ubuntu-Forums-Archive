---
title: "Hard Drive Difficulties"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by jas992 on 2007-01-03
Hi,

I am just starting out and have a few questions to ask :) Firstly, I have two internal HDD's connected but neither show up in the System->Computer window. I can however access my master drive through the 'Filesystem' shortcut. My question is, how do I make my master HDD appear in the 'Computer' window.

Secondly, my slave drive currently is formatted using the NTFS filesystem as it was previously used under Windows XP. I really don't want to format this drive as it holds data I value. Can Ubuntu recognise NTFS and if so how do I access this drive?

Any information would be greatly appreciated,

Yours truly,
jas992.

---

### Post by aberry5555 on 2007-01-03
Firstly I suggest that you read up on how Hard drives are represented in Linux. In windows they are show as completely seperate drives in the "my computer" section. In linux however, the drives are read as folders. For instance say you had two HDs, one with one partition on, the other with two and you set up your first HD with the linux distro. The very top folder for that HD would be "  /  ". Usually linux names the hard-drives in their order on the IDE controller, i.e IDE0 will be "hda", IDE1 will be "hdb" and so on. Any partitions on these disks are named using first the drive they are on and secondly the number of the partition, so the first partition on your first IDE drive is usually "hda1".

so if you wanted to add a partition from one of the other hard drives you would have to "mount" it somewhere within " / " (usually in /mnt/*drive-name*). e.g. if you wanted to add the first partition on the second drive to the "mnt" folder so that you could view it's contents you would open up a terminal window and type something like"sudo mount /dev/hdb1 /mnt/win_c (or whatever name you want it to be called, just make sure the folder is there before you run the command). Any drive you want to see can be mounted this way, using the mount command, the drive's location (/dev/*Hard-drive-name*) followed by desired location within " / ".

With NTFS it depends on whether you want it to be a read-only drive or whether you want to read and write. Ubuntu can read NTFS natively but it cannot write to it. For that you need a piece of software called "NTFS 3g" ([http://www.ntfs-3g.org/)](http://www.ntfs-3g.org/)). This works in a very similar way to the mount command but has it's own commands which are listed on the site. Because it isn't a built in command, rather a standalone script, you will need to include it somewhere in your startup scripts if you want it to be there every time you turn on the pc.

---

### Post by benthegreat on 2007-01-05
I'm also trying to mount an old ntfs drive and i want to get the data off it, but i have tried many times and a can't get it to work. It mentions something about fstab. Could you please give a detailed accurate run through of exactly what I have to do. it would help me greatly.

---

### Post by jvc26 on 2007-01-05
An extremely useful post on fstab:
[http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab](http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab)
This is where I learnt most of my fstab stuff from and the links from that guide.

NTFS may cause you a headache - mine worked fine and I had no problems, but other people have had. The NTFS read-write drivers are talked about here:
[http://ubuntuforums.org/showthread.php?&t=217009](http://ubuntuforums.org/showthread.php?&t=217009)

aberry5555 has explained the fact that linux uses a different method of filesystem than windows (not surprisingly) So your drives will be mounted under / (the filesystem) and in separate folders for other mounts. take a peek at the fstab post its pretty helpful if you have a moment to do some reading :)

Il

---

### Post by livingtarget on 2007-01-05
Actually if you can read the harddrive inside 'Filesystem' and you want to add it to the sidebar, it's quite simple. Go in the filebrowser, browse to the drive. Then in the menu called 'Bookmarks' -> 'Add bookmark'.

If the other links above don't satify you already, ubuntuguide.org to the rescue!

If you only need to read:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)
If you want read and write:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

It should mount it correctly next time you start up the pc.

---

