---
title: "NDAS-Admin removal"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by stueyboy on 2007-02-11
Folks, hoping you can help a bit here. I've got an NDAS network disk which I was keen to get working with Ubuntu 6.10 and reading on the Ximeta site the guidance was vague but kind of looked like it might work.

I followed the instructions to install the driver and the admin package but the latter failed to install properly so now I get an error about my package manager which would like to reinstall the program but it can't find an archive for it.

Does anyone have any general help or advice on how I can either remove the package properly or get it to work. Tried looking on the forums but not much of direct relevance. I can post some details if it is going to help.

Ta
 
From package manager

> E: The package ndas-admin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


---

### Post by stueyboy on 2007-02-11
OK, I found how to get the package manager error sorted so that is OK now and the software is removed. I'd still be interested to hear if anyone ever managed to get an NDAS device working properly. It looks like the package from Ximeta is flawed in some way from reading the tickets on their website.

---

### Post by gsanse on 2007-02-15
Can you describe how did you manage to solve the minstalled package problem. I am suffering with the same problem.

Thank you.

---

### Post by gsanse on 2007-02-15
Following the instructions in this thread I was able to remove ndas-admin. 

[http://ubuntuforums.org/showthread.php?t=160331](http://ubuntuforums.org/showthread.php?t=160331)

---

### Post by gsanse on 2007-02-24
The Ximeta site has been updated and the drivers now work with Ubuntu 6.10. Check it at:

[http://code.ximeta.com/trac-ndas/wiki](http://code.ximeta.com/trac-ndas/wiki)

---

### Post by stueyboy on 2007-02-26
That's smashing as it now works pretty well.

I have a problem though when trying to automount the drive as fdisk -l gives me an error as it can't read the partitions properly so I can't get the correct code to mount it in fstab but it will mount manually.

---

### Post by gsanse on 2007-03-06
Can we post the lines you added in fstab for the device?

---

### Post by stueyboy on 2007-03-06
I used the guide [HERE]("http://code.ximeta.com/trac-ndas/wiki/Usage") but like I said, I had trouble getting the system to recognise the partition table on the NDAS disk and there is too much data on it to start from scratch again

I ought to add that I am using a freecom device, not ximeta it just so happens that the freecom drivers are not as good as the ximeta ones (like the freecom ones used to blue screen my xp laptop when I connected)

---

### Post by ooops on 2007-04-28
Have trouble of getting NDAS working on Ubuntu 7.04

NDAS kernel installed OK, but ndas-admin gets an error.

Anybody has it working on Ubuntu 7.04?

Thanks
in advance

---

### Post by eentonig on 2007-05-22
following this thread.

---

