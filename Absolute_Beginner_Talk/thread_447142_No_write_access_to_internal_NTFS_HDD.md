---
title: "No write access to internal NTFS HDD"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by matthaeus123 on 2007-05-17
Sorry if this is a repost. I couldn't find a solution for this anywhere in the forum.

Here's the problem: I just changed over from Windows and I have 2 hard drives, which were both formatted for windows and worked totally fine (reading and writing). Then, yesterday I switched to Ubuntu. I reformatted my primary hard drive to Linux, and didn't change a thing on my 2nd hard drive, because it has all of my files backed up on it. So, the 2nd hard drive is pretty much full, so I decided to "cut" and paste some of the files onto the primary hard drive. I noticed I couldn't because the 2nd hard drive was unable to write or delete data. It said I didn't have permission to do this or something like that. So, I went to properties and tried to change the permissions, but it said I didn't have the permission to do that. I'm stumped. Pease, help.

I tried the NTFS config tool, it did nothing for me.

---

### Post by k33bz on 2007-05-17
How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access

Warning: The software you will use is still in Beta. You should not enable it on production machines

    * Read #General Notes 

    * Enable universe. Read #How to apt-get the easy way (Synaptic) 

    * Applications -> Add/Remove -> search for 'NTFS', you should find NTFS Configuration Tool, install it. 

    * Applications -> System Tools -> NTFS Configuration Tool -> Enable Write Support (depending on your device internal/external) 

    * Further troubleshooting is listed at this comprehensive howto thread. 
[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by dxdemetriou on 2007-05-17
I think now it is on repos on Feisty, and it is not a beta now as it have reached the 1.0 release. I have read because of the optimization of the code it is not as fast as native, but even the half speed is ok with me
anyway, the only problem with that is when the ntfs disk don't umount properly, then must be start with windows (I don't know if can be do with Linux).
When I followed this howto on Edgy I hadn't any problem, except from that

---

