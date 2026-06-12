---
title: "e2fsck/scandisk a ext3 harddrive in windows?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by omgwtf on 2006-09-07
Hello :)

I think I accidentally added a corrupt file (virus?) to my already dying hard drive. Now, Ubuntu won't boot up anymore. It stops right after "mounting drives ... ok." In recovery mode it says something about I/O error (possibly caused by the corrupted file) and then "**kernel panic: Attempted to kill init!**" and then 'freezes up.'
Last time this happened, I simply formatted the drive and reinstalled. This time I was wondering if there might be a more, hm, sophisticated way in fixing Ubuntu?
Perhaps just running a type of scandisk in windows or command line (is there such a thing in Ubuntu?) and it'll fix/delete whatever file is causing this.

Thanks for any tips


edit: I can read the drive in windows by using Ext2Fsd and some other software.

---

### Post by TwoWordz on 2006-09-07
Hello,

This looks to me like your drive is dead.

You should try to find the maker of your drive and download the bootable diagnostic disk from them.

If everything is fine, you can then perform some filesystem checks.

TW

---

### Post by omgwtf on 2006-09-08
Thank you!
But the strange thing is that I can still access the drive without any problems on windows.

How would I go about doing a filesystem check?

Does it help that I have a Knoppix DVD lying around?

---

