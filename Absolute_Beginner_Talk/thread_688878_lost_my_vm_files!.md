---
title: "lost my vm files!?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-02-05
ok, i don't know how this happened, but i am in complete confusion here- i recently installed a new virtual machine on my Ubuntu 7.10 system with VMware Workstation 6.0.. the vm installed just fine and i have been using it for about a week now... all of a sudden my Ubuntu system froze up after i installed some new system updates that were available- i could still move the mouse but nothing else responded- so i rebooted the PC after awhile, which would have forced my vm to shut down improperly as well.  when i logged back into ubuntu after rebooting and went to load my vm- it is GONE!!  no files in the directory where i saved it to- nothing!!  am i missing something here?  can anyone suggest what might have happened here and how i might get my vm back please??

thanks.

---

### Post by talsemgeest on 2008-02-06
A cold reboot is not good for a linux box...

But even so, I doubt that it would cause all of those files to magically disappear.

Unfortunately, I have no Idea where they might have gone, but have a look in /etc/ "whatever looks like VMware" just to be sure.

Hope I've helped :)

---

### Post by Trail on 2008-02-06
You could try to undelete the files if you are using ext2/3. I do not remember the exact command, but should be easy to search for.

And of course, that doesn't mean that a recovered directory will surely be usable (might be corrupted), but give it a go.

---

### Post by Matt26 on 2008-02-06
thanks i will look into that... i am pretty sure that the machine was not rebooted since the vm was installed, so i don't know what bearing (if any) this would have on the situation.

would permissions or ownership to the volume be of any consideration here?  i'm just wondering if it would make any difference if the volume was owned by root for example.

---

### Post by Trail on 2008-02-06
Hmm I did some searching after noticing the other thread, and it seems that **recover** (sudo apt-get install recover) only works on ext2... ext3 appears to zero out some fields that recover uses. The only method at first glance of recovering a text file is through grep, but this is not a text file so it doesn't apply...

(Apparently I was insightful enough to pick ext2 but not to actually backup a particular .c file in the past...)

---

### Post by Trail on 2008-02-06
Maybe this:

[http://freshmeat.net/projects/giis](http://freshmeat.net/projects/giis)

---

### Post by Matt26 on 2008-02-06
i used photorec and i could see my files listed under the volume- so does this mean they are still retrievable?  how can i restore them back to the volume?

---

### Post by Matt26 on 2008-02-06
i used fsck on the volume and i was able to see my files again under the live cd.. when i logged back into ubuntu normally they were gone again- so i removed the volume from fstab, rebooted, manually mounted the volume and the file were available once again!  so i changed fstab back to auto-mount for the volume, rebooted, logged in, and once again the files were gone.  what could be causing this issue?

---

### Post by talsemgeest on 2008-02-07
Are they still listed under the command line?

---

### Post by Matt26 on 2008-02-07
well i finally figured out the issue here- and interestingly enough, i never lost my files at all and it appears there never was an issue with the volume... i recently added an entry to my fstab file to have the volume auto-mount when ubuntu loads- since then i have had to rename the folder that represents the mounting point for that volume, but i never changed the fstab file to reflect the changes- and i had not rebooted the PC since renaming the folder!  talking about missing the smallest things... anyways, it looks like all is well again- however i have noticed that my windows XP vm loaded extremely slow initially- could this be related the system freezing up recently?  since i had to do a hard reset on the PC, it would have forced the XP vm to shut down improperly.

---

