---
title: "how to edit fstab file during boot cycle"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-04-09
Hi:

I believe I need to edit my fstab file bc my comp gives errors of 

<code>
Checking filesystem
fsck.ext3: No such file or directory while trying to open /dev/hdf1
</code>

Which, in essence, means my comp is not "seeing" the hard drive or drives attached via a PCI RAID card (which previously had been recognized, formatted, written to, etc.).

Tried other PCI slots, same error.

Entered root password and tried to edit /etc/fstab file with "vim" editor but fstab is "read only" at this point and I get a message that says the file can be edited with 

fstab-sync

and to check the "man" pages which I've done and found . . . nothing.

So, any helpful hints on how to edit the fstab file? I just need to comment out that line so my comp will boot all the way. Yes, I have tried live version boots which get me nowhere.

GM


[and then a message about being dropped to a shell and how the system will reboot if I do not type in root password for maintenance]

---

### Post by dcstar on 2006-04-09
[QUOTE=GMachine_24]Hi:

I believe I need to edit my fstab file bc my comp gives errors of 

<code>
Checking filesystem
fsck.ext3: No such file or directory while trying to open /dev/hdf1
</code>

Which, in essence, means my comp is not "seeing" the hard drive or drives attached via a PCI RAID card (which previously had been recognized, formatted, written to, etc.).

Tried other PCI slots, same error.

Entered root password and tried to edit /etc/fstab file with "vim" editor but fstab is "read only" at this point and I get a message that says the file can be edited with 

fstab-sync

and to check the "man" pages which I've done and found . . . nothing.

So, any helpful hints on how to edit the fstab file? I just need to comment out that line so my comp will boot all the way. Yes, I have tried live version boots which get me nowhere.

GM


[and then a message about being dropped to a shell and how the system will reboot if I do not type in root password for maintenance][/QUOTE]
Your system is booting up in Read Only mode because of the errors, that is why you cannot edit anything.

A boot of the install disk should allow you to exit to a shell, then mount and edit your hard disk - do a forum search for detailed instructions on this procedure.

---

### Post by GMachine_24 on 2006-04-10
Well, as I pointed out in my first post, I had tried live version boots in attempt to solve the problem - but, as I mentioned, these attempts did not work. And I spent several hours attempting to do this.

Which is why I ended up back in the forum asking about a way to edit the fstab file without using a live boot disk. Either it's impossible or there is a way to do it because people obviously had problems with fstab files before live boot disks became so popular. I attempted to figure out how to edit the file using a Unix editing program but, as I said, to no avail.

Eventually, I concluded the problem was either a blown hard drive, corrupted files or some combination. I replaced the drive, reinstalled the OS and now everything runs fine again.

I guess what I'm trying to say is, sure, some people come here without looking through previous forum posts but most of us make an honest, and often lengthy, attempt to resolve issues on our own.

GM

---

### Post by dcstar on 2006-04-10
[QUOTE=GMachine_24]Well, as I pointed out in my first post, I had tried live version boots in attempt to solve the problem - but, as I mentioned, these attempts did not work. And I spent several hours attempting to do this.
......
I guess what I'm trying to say is, sure, some people come here without looking through previous forum posts but most of us make an honest, and often lengthy, attempt to resolve issues on our own.

GM[/QUOTE]
And as I said, you can use the **Install** disk, not the **Live** disk to do these sort of thing, and there are numerous step-by-step instructions in the forum on how to do such things.

---

### Post by taurus on 2006-04-10
Just wonder if you can boot your system to recovery mode from GRUB.  Then edit your /etc/fstab...

---

### Post by GMachine_24 on 2006-04-12
Ugh. My mistake.

I am building another Ubuntu comp to use for testing-learning and I will give a try to editing the fstab file with the install disk.

Thanks.

GM

---

