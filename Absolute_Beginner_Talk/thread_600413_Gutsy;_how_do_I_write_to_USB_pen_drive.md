---
title: "Gutsy; how do I write to USB pen drive?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by kojakk00 on 2007-11-02
I am new to linux so forgive me if I am missing something fundamental. After the upgrade to Gutsy  I cannot write to my USB stick any more. The permissions are fixed at read only and I and when I try to change them the system says it's a read-only device. Does anyone have the same problem?

---

### Post by philinux on 2007-11-02
Just use the sudo chown command

---

### Post by ajmorris on 2007-11-02
This is most likely a permissions problem. so, you could chown the flash disk like philinus said, or, you could edit /etc/fstab, and in the options sections add 'users' . This will allow all users, not just root, to mount the flash disk, and thus, also write capabilities.

---

### Post by kojakk00 on 2007-11-02
Many thanks for responding but, no, chown doesn't work.  
When I type:
sudo chown -R kojakk00 '/media/LEXAR MEDIA' 
I get the error message:
chown: changing ownership of `/media/LEXAR MEDIA/test.txt': Read-only file system

and the permissions don't change. The problem seems to be more profound.

---

### Post by kojakk00 on 2007-11-02
> **ajmorris said:**
> This is most likely a permissions problem. so, you could chown the flash disk like philinus said, or, you could edit /etc/fstab, and in the options sections add 'users' . This will allow all users, not just root, to mount the flash disk, and thus, also write capabilities.

But mounting does not seem to be the problem. The disk is mounted, (and I have already responded to philinus, that chown does not allow me to change permissions). My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=92c1b903-d48f-4549-9c07-bd4219158046 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=aba9357c-3946-4651-9a5f-08c4f4e50c57 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks again for taking the trouble to respond but I am still on square one.

---

### Post by philinux on 2007-11-02
I've just put my pen drive in and it mounts as /media/disk

Attached is a screenshot of the permissions tab.

What does yours look like.

---

### Post by kojakk00 on 2007-11-02
I have also tried pmount, but to no avail. To do that, I first unmounted the USB pen drive and  then typed:
pmount -w /dev/sdc1

It mounted ok but as read-only.  Any attempt to change permissions results in the error 'read-only file system'. So I still can't write to it.

---

### Post by philinux on 2007-11-02
When you put the pen drive in it should automagically appear on your desktop.

Right click and select properties and let us know what it says there.

---

### Post by kojakk00 on 2007-11-02
> **philinux said:**
> I've just put my pen drive in and it mounts as /media/disk

Attached is a screenshot of the permissions tab.

What does yours look like.

Hi, Phil,
After using pmount, my permissions tab also shows,  'create and delete files' for 'Owner' but not group or others. For group and others the Folder access is 'none' and nb, attempts to change that fail with the error 'it's a read-only disk'  The funny thing is that I, as Owner, can neither create nor delete files despite what the permissions tab says.

---

### Post by philinux on 2007-11-02
Can you click on group find your user and select it?

Not sure why you need pmount though mine appears on desktop as mounted.

---

### Post by kojakk00 on 2007-11-02
> **philinux said:**
> Can you click on group find your user and select it?

Not sure why you need pmount though mine appears on desktop as mounted.

I don't really need pmount, I was just trying it because I ran out of ideas. My USB stick also appears as mounted when I just plug it in.  So I am now not using pmount and have reverted to automount. The owner permissions also show 'create and delete'. I clicked on root as you suggested and tried to select my user but got this error message: "/dev/sdc1 is read-only". Oh, I have seen this message so many times now:mad:

---

### Post by philinux on 2007-11-02
sudo chown -R youruser /dev/sdc1

Keep going .

---

### Post by paul.matthijsse on 2007-11-02
Suggestion: has your usb stick perhaps a switch that prevents writing to it? My SD photo card has such a (very very little) thingy...

---

### Post by philinux on 2007-11-02
a switch eh thats a bit crafty and it must be damn small. :lolflag:

---

### Post by kojakk00 on 2007-11-02
> **philinux said:**
> sudo chown -R youruser /dev/sdc1

Keep going .

Phil,
Sorry for repeating myself but chown doesn't allow me to change the owner the because it thinks it's a 'read-only file system',  Nb, yes, I have checked  this little plastic switch and  as I explained in my first post, have used a Windows machine to write to this USB flash without a problem.

---

### Post by philinux on 2007-11-02
Is there anything important on it.

You could format it.

---

### Post by philinux on 2007-11-02
Another idea - boot up the live cd and use sudo chown from there.

---

### Post by kojakk00 on 2007-11-02
So, I decided to invest money in a brand new 2GB USB pen drive. Guess what. The new one works fine! I can write to it no problem. So the old trusty 128MB flash (with FAT16 on it) goes in the bin. Now I am in love with Gutsy again, even though I have to say, I did not expect Gutsy to fail me on something Windows had no problem with,

Thanks for all your help, good people.

---

### Post by philinux on 2007-11-02
If its fat16 reformat it to fat32.

---

### Post by kojakk00 on 2007-11-02
> **philinux said:**
> If its fat16 reformat it to fat32.

Well, I did as you suggest and now I can write to that old USB flash too!  So was FAT16 the cause of all this? It would never occur to me. Does this look like a bug in Gutsy or is Gutsy meant not to be able to write to FAT16? 
Cheers
Kojakk00

---

### Post by philinux on 2007-11-02
I thought linux could write to fat16. I just think it got corrupted somehow and formatting did the trick. Save you having to throw it away. :)

---

### Post by kojakk00 on 2007-11-02
> **philinux said:**
> I thought linux could write to fat16. I just think it got corrupted somehow and formatting did the trick. Save you having to throw it away. :)

Well I was using that USB flash for a long time mainly to move files between my windows desktop and ubuntu feisty on my laptop. The problem started when I upgraded from Feisty to Gutsy. I think it's unlikely that the flash got corrupted exactly at the same time. Especially as Windows could still read and write. It looks to me that perhaps Gutsy has a problem with FAT16. Thanks for all your help  I am not throwing the old flash away now :)
Cheers

---

