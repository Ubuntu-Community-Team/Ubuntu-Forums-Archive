---
title: "Copy from Mac hard drive"
date: 2014-03-25
forum: Apple Hardware Users
---

### Post by elizabeth5 on 2014-03-25
Hello, 

I am posting this out of desperation :p

Right, i have a Macbook; there has been an issue with the hard drive, which i've rectified by replacing the old HD with a new one. I did not have backups of my data, i tried to recover these via disk utility, however that did not work. I also placed the hard drive into one of those sata enclosure thingy, but the hard drive does not appear on my desktop. I do see it in disk utility, but i am unable to mount it :(

Now, onto ubunto, 

I have the 11.04 version. I've followed the directions from this video to gain access to my files, however i am doing something wrong, somewhere.
[https://www.youtube.com/watch?v=eMyREL8qOPE&list=FLRdkQLuKnMyEpzJwn9beLSQ&index=2](https://www.youtube.com/watch?v=eMyREL8qOPE&list=FLRdkQLuKnMyEpzJwn9beLSQ&index=2)

When i open terminal, i get the following message 'To run command administrator (user "root"), use "sudo <command>". See main sudo_root" for details. ????? What command should i use? I type gksudo nautilus, then click onto mackintosh HD, users, Elizabeth, then permissions. Owner 503 - user 503, click root, message appears ' Sorry, could not change the owner: Read only file system'. What am i doing wrong? I cannot drag the folder onto desktop either, as it is 'read only'. Help, this is so frustrating, i can see the contents of my folders, but i unable to save onto my external HD :( 

Hope all that makes sense xD :)

Edit: The HD is in a external enclosure, i boot from windows into ubunto.

Thanks in advance,

Elizabeth

---

### Post by steeldriver on 2014-03-25
Hello and welcome to the forums

What is your end goal here? it shouldn't be necessary to change the permissions on the mac drive in order to copy your files off it

It sounds like the drive *has* been mounted, but mounted read-only ('ro') - possibly because the system thinks it's damaged, but more likely simply because it's a mac filesystem (hfs/hfs+), which is mounted read-only by default

Can you post the results of the following command so we can see what we're dealing with please?

```

mount | grep ^/dev

```

---

### Post by phidia on 2014-03-25
You can also check out the 4th post at [this thread]("http://ubuntuforums.org/showthread.php?t=2197874&highlight=mount+hfs%2B") which should help getting hfs+ mounting working.

---

