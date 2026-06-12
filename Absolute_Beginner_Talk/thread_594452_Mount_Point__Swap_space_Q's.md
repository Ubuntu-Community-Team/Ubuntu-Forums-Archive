---
title: "Mount Point // Swap space Q's"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by XNYE on 2007-10-28
I'm installing Gutsy on a notebook with 5 partitions.  This notebook has XP Pro already installed.  I'm dual booting.  When I select the partition I made for ubuntu it lets me select the formate type which I made ext3 and doesn't provide a mount point.  I previously installed this a week ago and I remember that it had something already set in the "mount point" area.  (Last time I didn't do manual)

What is the correct mount point?  Right now I have it as root but haven't completed the install process.  Waiting on replies to this thread.

Also, looking ahead it asks me if I want to make a swap space... Last time I had optioned not to because when I read it, I felt I had enough free HDD space but now I read it again and wonder if it's suppose to act like RAM?  I have an extra 5GB partition that I haven't used yet... should I use that?  What benefits does swap space give?

Thanks!

---

### Post by Six_Digits on 2007-10-28
You'll need 3 partitions in all. Swap, root, and boot. If you're so unsure, try [Wubi]("http://wubi-installer.org/"). The root partiton should be "/". Swap's partition doesn't have to be big, and I forget whether there is a boot table or not...

---

### Post by XNYE on 2007-10-28
I see... if I have to resort to wubi I will... but if I could get help otherwise, I'd prefer that.

So far, to my understanding, if I do the install manually.. and not allocating a certain amount of space on the Windows partition, I must create three seperate partitions(not just one?)  one mounted as "/", one as "/boot" and one as "/swap"?

My thoughts: I had thought I just needed one partition?  If I do it this way.. will I automatically be able to see the files on widows or no?? Does that just work if I install ubuntu using the first "option" on the ubuntu installer(allocating the space from the windows partition)?

---

### Post by sandysandy on 2007-10-28
> **XNYE said:**
> I see... if I have to resort to wubi I will... but if I could get help otherwise, I'd prefer that.

So far, to my understanding, if I do the install manually.. and not allocating a certain amount of space on the Windows partition, I must create three seperate partitions(not just one?)  one mounted as "/", one as "/boot" and one as "/swap"?

My thoughts: I had thought I just needed one partition?  If I do it this way.. will I automatically be able to see the files on widows or no?? Does that just work if I install ubuntu using the first "option" on the ubuntu installer(allocating the space from the windows partition)?

generally swap file should be twice ur RAM size.
eg if RAM is 1GB, SWAP could be made 2GB.
also u can create more partitions from existing partitions. Ubuntu disc allows u to do that. if u want your 5gb partition can be deleted and repartitioned to 2gb (swap) and 3gb.

regards

---

### Post by sneezymelon on 2007-10-28
Rather swap should be 1.5 times your RAM. That much suffices

---

### Post by XNYE on 2007-10-28
Thanks for those replies guys.


Now I need to know if I need to specifically set the mount points for each of them to make everything work.  Like... Do they have specific mount point dir. that need to be used.  ig... "/usr/swap"? 
/blah/boot"

How big does the boot partition need to be?

---

### Post by forestpixie on 2007-10-28
you don't actually need to set anything but / as a mount point, but if you want you could be setting /, /home and swap , I do that but only for if I want to reinstall or upgrade, just makes lefe a little easier

If you just go for / - the install will make swap space for you I believe

If you can get away with not using the 5Gb partition I'd leave it empty for the moment.

---

### Post by dcstar on 2007-10-28
> **sandysandy said:**
> generally swap file should be twice ur RAM size.
.........

I really wish people would stop repeating this old myth about Swap Space, it was out of date years ago and is still passed onto more people who then buy into the myth because "someone said so"....

If you want some realistic - and relevant - information:

[http://ubuntuforums.org/showpost.php?p=2528643&postcount=2](http://ubuntuforums.org/showpost.php?p=2528643&postcount=2)

---

