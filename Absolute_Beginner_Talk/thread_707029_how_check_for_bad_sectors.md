---
title: "how check for bad sectors?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2008-02-25
i am using ubuntu 7.10 in a lenovo t60 laptop.

i did a clean installation of ubuntu 7.10 (after having some problem of crashing, after a year or so using ubuntu, firtst 7.04, and then 7.10), and now i want to check if there are any bad sector or physical error in the hard-disk?.

i was wondering if i should start with the live cd (or the one where i have the installation of ubuntu) and then run some 'tool' syntax??, do you know??

thanks in advance

---

### Post by jordanmthomas on 2008-02-25
Boot off the LiveCD and use badblocks.
```
sudo badblocks /dev/sda?
```
where /dev/sda? is the disk you'd like to check.

It's possible you'll need to install badblocks while on the CD
```
sudo apt-get install badblocks
```

---

### Post by cseljatib on 2008-02-25
Ok, i'll
but Does this badlocks 'bussiness'' erase the data that i have in that partition (or disk)?

---

### Post by jordanmthomas on 2008-02-25
No, it just prints out the blocks it finds that are bad.
It doesn't repair them or anything. 

There is a way you can pipe its output to e2fsck so it WILL repair them I think, but I haven't ever done it.

---

### Post by cseljatib on 2008-02-25
OK, i'll try. last quick question. 
The liveCD can be the ubuntu installation CD right?, then i put start or install ubuntu, and then go to the terminal and type
sudo badblocks /dev/sda?

am i right?

---

### Post by jordanmthomas on 2008-02-25
Yes, exactly.

If nothing gets output, that's a GOOD thing.
The more numbers come, the more bad blocks (not sectors, but bad blocks are essentially the same in terms of diagnosing hardware problems) you have.

---

### Post by cseljatib on 2008-02-25
i did it, but i did got a long list of numbers, but not so big, i think. Now, the question is how to fix bad blocks?

---

### Post by jordanmthomas on 2008-02-25
From e2fsck's man page ([http://linux.die.net/man/8/e2fsck](http://linux.die.net/man/8/e2fsck))
> -c
    This option causes e2fsck to use badblocks(8) program to do a read-only scan of the device in order to find any bad blocks. If any bad blocks are found, they are added to the bad block inode to prevent them from being allocated to a file or directory. If this option is specified twice, then the bad block scan will be done using a non-destructive read-write test. 
So, something like
```
sudo e2fsck -cc /dev/sda1
```
The second c makes it non-destructive, which sounds better than destructive.  To be perfectly honest, I'd wait for someone to verify this is what you want to do before you do it.  The only time I've used badblocks it was time for the drive to go away for good.
It will take a while since badblocks will need to run again.  If you happen to still have the list up, though, you can save them into a file and use the list you've already generated.

---

