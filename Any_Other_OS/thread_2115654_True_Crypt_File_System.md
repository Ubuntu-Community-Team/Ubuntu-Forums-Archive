---
title: "True Crypt File System"
date: 2013-02-13
forum: Any Other OS
---

### Post by coeball on 2013-02-13
I am running Linux Mint with Cinnamon. I can't access some files I recently backed up because the filesystem (no partitions are visible in file explorer) on my external HD no longer exists. The drive is also encrypted with True Crypt and I can still mount the drive but unable to access anything.

Any help would be greatly appreciated.

---

### Post by Perfect Storm on 2013-02-13
Moved to Other OS/Distro forum.

---

### Post by coeball on 2013-02-15
Thanks noob mistake by me apologies.

---

### Post by coeball on 2013-02-19
Bump.

---

### Post by coeball on 2013-02-25
I am somewhat desperate anybody able to help me with this problem?

---

### Post by Hodevah on 2013-02-25
I will try to help if I can. 
 You say that the file-system changed.
 Changed from what ***to*** what?

If _you_ changed the file system, inspite of having installed true crypt on that external HDD, your files are toast. The file-system needed to remain the same during the encryption process because true crypt makes a note of this and expects the file-system to remain the same when it wants to access the hidden drive again. 

Is this what happened? Sorry, I am trying to understand what happened, hence my question.

---

### Post by coeball on 2013-02-26
Thanks for the reply, I didn't do anything , the hardrive was working fine. The next time I tried to mount it the partition which my files are on had disappeared, and because there is no partition I can't mount the drive and retrieve my data.

---

### Post by Hodevah on 2013-02-26
Ok. I see what you are saying. 
The hard-drive on which truecrypt volume was mounted is now in-accessible, right?
Try *Testdisk*. It is in the repositories.>"Partition scanner and disk recovery tool (Testdisk)"
You mentioned that you can mount the Truecrypt file system; therefore, you might be able to access your files using the program. 

Found some information here:
[http://www.cgsecurity.org/wiki/Recover_a_TrueCrypt_Volume](http://www.cgsecurity.org/wiki/Recover_a_TrueCrypt_Volume)

Also, what operating system was used to create the volume?

I used search terms such as ' *truecrypt volume missing*" on Google.

---

### Post by coeball on 2013-03-01
Thanks for this intial scanning with test disk has not been successful, but I will keep trying the rest of the methods described in the wiki. The partition was created on an Windows 7 pc.

---

### Post by coeball on 2013-03-08
After some more scanning I got this message:


The harddisk (500 GB / 465 GiB) seems too small! (< 16304469 TB / 14828828 TiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors

Sorry for the incomplete message, but terminal wouldn't let my copy and paste the entire message. Any ideas on what I can try next would be welcome.

---

