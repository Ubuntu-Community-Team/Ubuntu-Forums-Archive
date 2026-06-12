---
title: "Copying/deleting data"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by danwosere2007 on 2007-10-06
Hi everyone. Basically my Microsoft Windows operating system fell foul to some sort of virus/difficulty ("unmountable boot volume" whatever the heck that is) so i decided to use the Ubuntu live cd in order to try and 1) Back-up the files from the internal harddrive onto an external one and then ultimately 2) Partition Hard-drive and 3)Install Ubuntu and totally have shot of Windows. and finally 4) Reinstall/Copy the files from the external onto Ubuntu Operating system. Upon trying to do this which i thought would be a fairly easy click and drag affair, i soon realised for some bizarre reason that i cannot copy any of the files, i cannot move any of the files and i cannot delete any of the files. "Pumalite" has suggested running Truemage and copying an image of the harddrive onto said external. Although i appreciate his way of resolving the problem,i would much rather be able to simply click and drag the relevant files from interal to external, as i can then delete as i go (so i know what i have copied and what is yet pending) also my external harddrive is only running at usb 1.0 as opposed to 2.0 so any copying is taking a considerable amount of time. If someone could suggest a way to do this, im sure it has to be possible as i cannot even move files on the internal harddrive or delete them let alone move them from internal to external. Basically it seems as though i have no rights on my own computer which is ludicrous. How am i supposed to manage the harddrive space left on my computer when i cant delete anything? It's just gonna fill up and fill up until eventually it has a fit and gives in. Any suggestyiond would be appreciated. I've allready tried changing to login as "root" but to no avail. Thanks - Dan Jackson

---

### Post by nick_h on 2007-10-06
If your Windows partition is NTFS then Ubuntu only supports read-only access by default.  If you need write access you need to install the ntfs-3g and ntfs-config packages.

Are you able to mount your windows drive in Ubuntu? (can you see the files in it?)

---

### Post by Linux_Man on 2007-10-06
If you have firewire ports, they are much faster then USB 1.0 if your externel hard drive has them.

---

### Post by danwosere2007 on 2007-10-08
Hi Nick. Before i could see the files in the drive and as you say they were read only though, but today i loaded ubuntu, and the whole drive had dissapeared from off my desktop as if it doesn't exist anymore...the drive is plugged in and seems to be functioning nominally. *shrugs any suggestions? - Dan

---

### Post by nick_h on 2007-10-08
When you say "some sort of virus/difficulty" could it be that the drive is failing?

If you have a failing drive then copying the data off as a disk image using Trueimage or even the unix dd command is a good suggestion.  It would be worth doing this before attempting to use the drive any more.

If you have a virus then using an antivirus program from a boot CD may be an idea.

Using a linux live CD as a recovery tool is not a bad idea.  You could try to mount a partition manually using the mount command.

You could always test the drive using a diagnostic from the drive manufacturer.  Some of these tools are included in the [Ultimate Boot CD](http://www.ultimatebootcd.com/) which may also be worth a try.

---

