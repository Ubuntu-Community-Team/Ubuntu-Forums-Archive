---
title: "Unallocated space on my hard disk (Gnome Partition Editor)"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-02
Hi all, got a problem...

I've taken the plunge and have just deleted my Windows NTFS partition - about half of my disk space is now unallocated (please see attachment).

What I want to do now is to "combine" this unallocated space with the existing ext3 partition - but the option to 'resize/move' my current ext3 partition is greyed out! Any idea why this is?

Also, my old NTFS partition was named 'hda1' - as you can see from the attachment, the ext3 partition and the swap partition are named hda2 and hda3 respectivily - is it possible to change these to hda1 and hda2 as well?

Thanks in advance.

---

### Post by professor_chaos on 2006-08-03
It probably greyed out because you cant move a mounted system and also your running programs needed to do the partitioning, that are on the partition you want to move. You should try to boot of the live cd or other and try moving/resizing. You will have to update or reinstall your bootloader, so it knows where your new OS is if you change the device name. 
I haven't tried this, so the bootloader part I'm not sure about. Lets see what others have to say.

---

### Post by cheway on 2006-08-03
> It probably greyed out because you cant move a mounted system and also your running programs needed to do the partitioning, that are on the partition you want to move.

I see what you're saying there, that makes sense.

I clicked on 'unmount' for the ext3 partition, but it didn't seem to do anything - I'm not even sure what 'unmount' means... I wouldn't have tried it unless everything was backed up, although it would be really nice if I didn't lose it all and could simply resize the partition to fill the unallocated space, AND make it the 'boot' partition forever and ever. I'm done and dusted with Windows.

---

### Post by professor_chaos on 2006-08-03
Yeah, you can't unmount the system you are using. However, if this partition was a non-system part, you could unmount it on the fly and partition it. Something to think about, since your at the crossroads, is perhaps making your home partition seperate from the OS. I know a lot of people prefer to devide there system this way. That way you can wipe your OS and still have all of your documents/files in home. 
Basically, make a new partition and then copy all your files over from old home and then mount your new home. 
Just a thought.

There are some guides on this forum.. try this [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by kerry_s on 2006-08-03
Have you rebooted so it can see that something has changed? When you change it the system will have the wrong settings in fstab, so after you reboot you should be able to resize, then reboot again so your fstab can be updated.

---

