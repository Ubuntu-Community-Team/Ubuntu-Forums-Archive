---
title: "Checking external drives for errors"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by r76 on 2007-07-31
Every so often (I think every 20-30 times) when I start Ubuntu, it pauses during boot to check the hard drive for errors.  I've read a few posts where people have found this annoying and asked to disable it - but they are usually advised it is important and should let it proceed.

My question is how to check an external USB hard drive for errors, as this is not automatically done at boot?  I guess mine has never been checked :(

The drive is ext3 formatted so from what I can find I guess I should unmount it first, then run ext2fsck?  What are the commands I should use to do this?  If it helps, my drive appears as /media/seagate

Thanks! :)

---

### Post by FleetAdmiral74 on 2007-07-31
If you read the man page for fsck, it should be apparent, because I have done this myself. 

Don't remember the commands I am afraid, but run man fsck and you should see.

try fsck /media/seagate though and see where that gets ya

---

### Post by r76 on 2007-08-05
Thanks for the reply.  I read the manual pages for fsck and e2fsck but they were a bit technical!  Still, I used system rescue cd and booted using that to be safe and certain my external drive wasn't mounted.  Everytime I do this normally, and subsequently mount the drive to back up images of my system on the external drive, I get a warning about there being errors on that filesystem. I doubted that they are major problems, probably just an error with the journal but wanted to check anyway. Once booted but without mounting, I typed,
```
fsck.ext3 /dev/sda1
```
The output again didn't make much sense to me, just about 'checking inodes and blocks' - although there was no obvious error message.  The process took about 20 minutes for a 500GB drive with 400GB of data (not many files, most are over 2GB), and since doing it I haven't got any error message when mounting that drive using the rescue CD (I never got a message in Ubuntu) :)

Thank you!

---

