---
title: "HELP!! Accidently deleted file from Local Disk! How to Recover!!!!!!!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-10-25
I accidently deleted a file in my local disk! How can i recover it back?? I pressed shift delete and it didn't ask for comfirmation! It just disappeared!

---

### Post by RomeReactor on 2007-10-25
Hi. Did you enable the Trash bypass in Nautilus? If you did, then that file is most likely gone. Was it a hidden file (did it have a dot before the name, e.g. **.file.txt**)? If it was a hidden file, open the trash can and press CTRL+H to see if it's still there.

---

### Post by evilregis on 2007-10-25
You must've changed the default behaviour because I get asked for confirmation when I SHIFT+Delete a file.

Did you check the Trash just to make sure?

If so and it isn't there, then I think you are out of luck.  Un-deleting in the ext3 filesystem is not like un-deleting NTFS.

From [ext3 FAQS]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html"):

**Q: How can I recover (undelete) deleted files from my ext3 partition?**

[I]Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.[/I]

---

### Post by az on 2007-10-25
Power off your computer right now.

(well, keep reading this for a second)

Obtain ubuntu-rescue-remix ([http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org))
and boot it.

You will need another drive onto which you will dump an image of all you unallocated disk space.  You will create this image by using dls (which is part of the sleuth kit).  This image can be quite large (think all of your disk's free space)

You can actually do this using the Ubuntu live cd and installing the sleuth kit package.

sudo dls /dev/sda1 > outputimage

Then data carve the files out of the output image using foremost or photorec, again by either using the Rescue-remix or by installing it from within the live session.  You will need to store the output from this on the external disk, since it may not all fit on the ramdisk the live cd runs from.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by kinngg on 2007-10-25
i deleted a file in my ntfs drive is it still possible for me to undo delete or something

---

### Post by evilregis on 2007-10-25
I'd suggest booting into Windows, install NTFS Undelete: [http://ntfsundelete.com/downloads/](http://ntfsundelete.com/downloads/)

Run it, search for the file you deleted and see if you can restore it.

---

### Post by az on 2007-10-25
> **kinngg said:**
> i deleted a file in my ntfs drive is it still possible for me to undo delete or something

Ntfsprogs is in Ubuntu.  

sudo apt-get install ntfsprogs.


Ntfsundelete can recover deleted files from an NTFS filesystem

From the manpage:

EXAMPLES

       Look for deleted files on /dev/hda1.

              ntfsundelete /dev/hda1

       Look for deleted documents on /dev/hda1.

              ntfsundelete /dev/hda1 -s -m '*.doc'

       Look for deleted files between 5000 and 6000000 bytes,  with  at  least
       90% of the data recoverable, on /dev/hda1.

              ntfsundelete /dev/hda1 -S 5k-6m -p 90

       Look for deleted files altered in the last two days

              ntfsundelete /dev/hda1 -t 2d

       Undelete inodes 2, 5 and 100 to 131 of device /dev/sda1

              ntfsundelete /dev/sda1 -u 2,5,100-131

       Undelete  inode number 3689, call the file 'work.doc' and put it in the
       user's home directory.

              ntfsundelete /dev/hda1 -u 3689 -o work.doc -d ~

       Save MFT Records 3689 to 3690 to a file 'debug'

              ntfsundelete /dev/hda1 -c 3689-3690 -o debug

---

