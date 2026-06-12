---
title: "Mounting NTFS External Hard Drive."
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by cmotdibbler13 on 2008-02-21
Hi,

Hopefully someone far cleverer than I can help me with a small problem I have.

As the title suggests I am trying to get my external hard drive to mount, it is formatted in NTFS,is USB and I am using Fiesty Fawn with KDE (although I have Gnome as well), I have ntfs-3g and ntfsfix installed and after reading other threads tried the solutions there.

When I try to mount it with right click on the desktop, it gives me this error message in kio_media_mounthelper:

**hal-storage-removable-mount-all-options refused uid 1000**

So I then read that force mounting works, so I went to the terminal and did this :

 [B]sudo mount -t ntfs-3g /dev/sdb5 /media/disk -o force
[/B]
which gave me this message:

[B]fuse: failed to access mountpoint /media/disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb5 (spare)[/B]

I read on another web site to go into Windows and autofix problems then unmount properly, which I have done. 

So can anyone tell me what I have missed please?

Since I know very little about command lines or using terminal properly, if any suggestions are made using these, could you write exactely what I need to put inot terminal. 

Thanks for your time.

Jon

---

### Post by FrozenFox on 2008-02-21
Are you sure you're on feisty? I've only seen that error on gutsy..

hal-storage-removable-mount-all-options refused uid 1000  is a problem related, from what I understand, to debian-based distros like ubuntu not having implemented policykit yet among other problems, such as incorrect assignment of the ID for the hard drive. But read your error more closely and you'll realize your mistake is pretty simple..

fuse: failed to access mountpoint /media/disk: No such file or directory

Fuse says you can't mount to /media/disk because that folder doesn't exist. You need to make the folder /media/disk before you can mount to it.

sudo mkdir /media/disk

then try again. For a more permanent solution, you might try:

1) sudo cp /etc/fstab /etc/fstab.backup
2) sudo gedit /etc/fstab  (replace gedit with kwrite if on kde)
3) Find the line for your hard drive you're trying to mount (make sure you have the right one.. removing the wrong partition would kind of suck)
4) Remove the line related to your hard drive (if it's there). It may be under a big long UID instead of /dev/sdb5 -- which is just the problem, many times, as it's not done correctly. But note that your good partitions that are picked up correctly also are likely to be so.
5) sudo apt-get install ntfs-config
6) sudo ntfs-config
7) Enable your external drive.
8) Reboot and try clicking it to get in again. If you have no luck, you may need to try editing fstab again with different stuff. I'd give you such info, but I'm using hardy and don't have that issue anymore, and such stuff isn't in my fstab.

If you run into problems, just restore your old fstab via sudo cp /etc/fstab.backup /etc/fstab

---

### Post by cmotdibbler13 on 2008-02-21
Yes thanks, I was totally wrong in my ubuntu distor's, it was gutsy sorry, I told you I was a bit of a thicky.

That worked fine.

I will now try to edit fstab (gulp)

Thank you for a quick and easy solution.

this is what kwrite says:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=abc68720-df6c-4c0b-b348-7f62d45c0480 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
[B]UUID=d51735fd-aea6-4a70-be32-819e54f9122a none swap sw 0 0
[/B]/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

If i read your reply right, I need to delete the bold entry and then save the file.

Then carry on with your instructions.

---

### Post by FrozenFox on 2008-02-21
I suppose you could wait until you have the "good" solution working, but edit your original post to relay the new question (fstab) if it doesn't work immediately. I've found that people outside of those asking a question in general tend not to read replies in these forums and answer something multiple times in the same way.

---

### Post by FrozenFox on 2008-02-21
**_Woa, hold on there!_**

I don't think you are looking at the correct partition. Notice it says 'swap'? That seems to me that sda5 is a linux swap memory partition.. which would definitely be bad to delete!

That is /dev/sda5, not /dev/sdb5.

# Entry for /dev/sda1 :
UUID=abc68720-df6c-4c0b-b348-7f62d45c0480 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=d51735fd-aea6-4a70-be32-819e54f9122a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

the first entry is your root ubuntu setup (obviously working correctly), the 2nd entry is your swap memory setup (clearly working correctly.. that is your spare memory partition though. do not remove it!), and the last is your cd drive setup or something. Notice the entry in question says sd-A-5, not sd-B-5. In general, devices are set up logically as follows..

device type_of_device device_"number" partition_number

where device = /dev/
type_of_device is hd for IDE hard drive, or sd for SATA hard drive
device_"number"  the letter corresponds to which hard drive you are looking at. A is drive 1, B is drive 2, etc.
partition_number the last thing corresponds to what number the partition is that you are looking at.

Ie /dev/sdc12 is device: SATA hard drive #3, partition #12.


In short: your entry does not appear to be in fstab at all. Just skip that part of my instructions and go on with ntfs-config. After you do that stuff and reboot, if you open fstab again the entry should indeed be there.

To continue, just FYI, the setup of entries in fstab is as follows.. i'll use your example. sections of the entry will be put in parenthesis to show you where they correspond to in the line:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
(cdrom device 0) (mount it to the folder /media/cdrom0) (it is supposed to be in the format of or the filesystem matching udf,iso9660) (the options to be included are that it shouldn't be automatically mounted, it should give permissions to the user, and i forgot what exec means, execution priveleges? ;p) (i forgot what the special options 0 0 are)

---

