---
title: "Ubuntu into 1st Gen Macbook probs"
date: 2008-02-28
forum: Apple Intel Users
---

### Post by macn0ble on 2008-02-28
Hello everyone-new here soo-the situation-

Tried to install Ubuntu 7.10 into my Macbook 1.8/1Gt RAM. Bought a new 120G HD and installed OS X into 1 partition. Updated it, installed rEFIt and resized the the partition using DISKUTIL "diskutil resize volume disk0s2 90G Linux Ubuntu 0B" So far so good. Then synchronized the MBR table with rEFIt and booted into 7.10 live cd in safe craphics mode. Started installing Ubuntu, but suprise suprise-the installation cannot find the free space-in face the whole harddrive (checked with fdisk). Tried also with Debian Etch, same prob.

Maybe I fekked up something in partition? Has anyone any suggestions, hints or clues what to do. 
Cheers!

---

### Post by cyberdork33 on 2008-02-28
> **macn0ble said:**
> Updated it, installed rEFIt and resized the the partition using DISKUTIL "diskutil resize volume disk0s2 90G Linux Ubuntu 0B"You made your new partition 0 Bytes large...

In the ubuntu LiveCD, check what things look like in the Partition Editor... (System > Administration > Partition Editor).

---

### Post by macn0ble on 2008-02-28
Actully, if You take a look @ the Diskutil man, you'll find that that 0B means that it'll create a HFS x big and uses the rest for the new Linux partition..but thanks anyway.:)

---

### Post by cyberdork33 on 2008-02-28
> **macn0ble said:**
> Actully, if You take a look @ the Diskutil man, you'll find that that 0B means that it'll create a HFS x big and uses the rest for the new Linux partition..but thanks anyway.:)
Apologies... I would still check what is in gParted. If you created a partition, then it wouldn't be "free space"

---

### Post by macn0ble on 2008-02-28
Could it have something to do with the version of HFS? Checked the partition with Diskutility from boot disk  & Diskutil and everything was fine, excluding the fact that those programs described the partion as "windows space" or something.

---

### Post by cyberdork33 on 2008-02-28
> **macn0ble said:**
> Could it have something to do with the version of HFS? Checked the partition with Diskutility from boot disk  & Diskutil and everything was fine, excluding the fact that those programs described the partion as "windows space" or something.
Start the Ubuntu Live CD, start the Partition Editor.

Select the partition you created (whatever it happens to show up as, it should be after your EFI partition, and your OS X partition) and delete it. This will leave _free, empty_ space. Then you can Start the Ubuntu installer, and tell it to use the empty space on the disk.

---

### Post by macn0ble on 2008-02-28
That is the problem, when starting the partition prog, nothing shows up, it doesn't find any free space @ all. Interesting, isn't it?

---

### Post by cyberdork33 on 2008-02-28
> **macn0ble said:**
> That is the problem, when starting the partition prog, nothing shows up, it doesn't find any free space @ all. Interesting, isn't it?Well, I am trying to say that if you did what you said you did, there is no free space, if there is a partition made, you need to delete it to make free space. Post the output of 'sudo parted /dev/sda print'.

---

### Post by macn0ble on 2008-02-29
Okay, will try that. It's  just that in some wiki's it was the thing to do (a partition for linux). Will keep you posted..

---

### Post by cyberdork33 on 2008-02-29
> **macn0ble said:**
> It's  just that in some wiki's it was the thing to do (a partition for linux).
I understand. I do not know why those methods are not working, but more detailed information about the current state of your disk would be helpful in determining what to do next.

---

