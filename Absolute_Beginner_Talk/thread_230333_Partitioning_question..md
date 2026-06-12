---
title: "Partitioning question."
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-05
Hi Folks

My Seagate USB HD (250 GB) has one primary partition and one extended partition which contains three logical partitions. All are presently ntfs and all four "usable" partitions are roughly 60 GB in size.
The partitioning was done with the Seagate Diskwizard.
In addition to the above, there is 900 MB of unallocated space which resulted from an oversight (OK, it was an error) while partitioning.

I tried today to use GPartEd to extend one of my logicals to encompass the unallocated space. However, this option was not available.
Indeed, the only option presented to me was to create a primary partition of a maximum size of 900 MB.

Is there anything I can do to include this presently unallocated space into one of my partitions?

Thanks
Paul

---

### Post by cheway on 2006-08-05
Were you using GParted Live (runs off the CD) or the one that's within Ubuntu?

---

### Post by PaulFXH on 2006-08-05
Sorry, I should have said that I was using the Live CD version of GPartEd

Paul

---

### Post by cheway on 2006-08-05
Now I have to apologise - I was going to suggest that you use the Live CD to see if that makes any difference.

---

### Post by catlett on 2006-08-05
Where is the 900mb of space? Is it inside of the extended partition? If it isn't inside the extended partition then you can't add it to a logical partition.The logical partition cannot reside outside the extended partition and the 900mb of unallocated is outside the extended partition.
Also if it is on one side of the extended partition and the primary partition is on the other, then the 900mb can't be added to that.
If this is the scenario (900mb of unallocated space at the end of the drive after the extended partition) then the only option is to make it a primary partition. 
If you really wanted to add the space to one of your logical partitions, you would have to delete the extended partiotion with all of it's logical partition. Then make a new extended partition that encompassed all the unallocated space i.e. the deleted extended partition and the unallocated 900mb. Then you can make your logical partitons again and one of them can be 900mb bigger.
Obviously if those partitions have data that is alot of backing up and restoring just for 900mb, I would just make it  a primary partition.

---

### Post by PaulFXH on 2006-08-06
Hi catlett
Looks like I'm out of luck because the unallocated space is OUTSIDE of the extended partition AND it's at the other end of the disk to the primary partition.
Oh well, it's only 900 MB!
Thanks for your explanation.

Paul

---

### Post by richbarna on 2006-08-06
Why not allocate it as your swap partition? Also, do you have a linux distro in there? You say that they are ALL ntfs? You could have it like this :-
Primary|Extended (with 3 logicals inside)|SWAP (900Mb)|

---

### Post by PaulFXH on 2006-08-06
Thanks for the reply.
Right now there are no Linux distros on that drive but I am going to try to boot (indirectly) to Linux (something or other) from there based on this link:

[https://help.ubuntu.com/community/BootFromUSB?highlight=%28hd%29%7C%28boot%29%7C%28from%29%7C%28usb%29](https://help.ubuntu.com/community/BootFromUSB?highlight=%28hd%29%7C%28boot%29%7C%28from%29%7C%28usb%29)

Yes, I could use this small space as a swap partition even though it is just a little smaller than my RAM (1GB).

Paul

---

