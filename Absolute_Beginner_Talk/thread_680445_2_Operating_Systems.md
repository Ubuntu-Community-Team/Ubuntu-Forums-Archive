---
title: "2 Operating Systems?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by kittykatmeowmeow on 2008-01-27
Is it possible to install ubuntu on my PC that has Vista and still work from both OS?  I'm liking what I see from the LIVE CD, but I can't do much without installing it onto the hard drive.

---

### Post by emarkd on 2008-01-27
You can install Ubuntu next to Vista and dual boot.  When you run the Ubuntu installer from the CD, make sure you tell it to resize the partitions and only use the free space.  I think that comes up in step #4

---

### Post by horry on 2008-01-27
of course, you can! just double click 'install' icon after LIVE CD startup. follow its information you can simply install ubuntu in your PC which has been installed VISTA.
my PC is installed like that. both of them work fine.

---

### Post by JoshuaRL on 2008-01-27
Yep, but please make sure you defrag the drive before you do.  Whenever there's been problems with files being overwritten it's almost always been because the person didn't defrag.  If you do that, you eliminate 98% of the chance of having issues.

---

### Post by jipke on 2008-01-29
You could also consider installing Virtualbox or Wubi and run Ubuntu from there. That way you can launch Ubuntu as if it is an application inside Windows. 

I don't know about Wubi, but Virtualbox even gives you the option to share directories between host (windows) and the virtual machine (Ubuntu in your setup).

---

### Post by Smelly Avocado on 2008-01-29
theres a nice guide i used to dual boot my vista and ubuntu
[http://acpmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://acpmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")
It worked like a charm.

---

### Post by bumanie on 2008-01-29
One word of caution when you are dual booting with vista is that the linux partitioners don't work well with vista. The suggested way around this is to use vista's in-built partitioner to reduce the size of your vista partition and leave the space as unallocated. Then ubuntu should insttall OK. Personally I would choose manual when up to the partitionstage, but that is up to you. To get to vista's partion manager right click my computer --> Disk managment --> Partition manager.

---

### Post by agim on 2008-01-29
I would also strongly suggest you use vista's partitioner as mentioned above.

Then, during the Ubuntu install (using the livecd of course), make sure you select install in the largest free space.

---

### Post by FuturePilot on 2008-01-29
I didn't have to use the Vista Partitioner. Everything went perfectly for me. Just selected resize the current partition and everything went fine.:confused:

---

### Post by ugm6hr on 2008-01-29
This might help:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

I would also recommend resizing the Vista partition in Vista to create "empty space" / "unallocated" at the end of the drive (about 15GB minimum is reasonable).  Then use the "Guided - largest contnuous free space" installation option in Ubuntu.

---

### Post by kittykatmeowmeow on 2008-02-16
Thank you thank you to everyone who has given me suggestions!!  I really look forward to this amazing change.  I'm sure I will be back with more questions after I do this.

Thanks!!:guitar::KS:KS:KS

---

