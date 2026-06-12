---
title: "Zero out free space for Virtual PC 7"
date: 2008-09-21
forum: Apple Hardware Users
---

### Post by johannes2510 on 2008-09-21
Hi!
First sorry for my english...
I have installed Ubuntu 7.10 on a G5 dual virtualized with Virtual PC 7 (and run well but slow). Now in the virtual HD I have some free space and according with the manual of VP I can recover that space, with a tool of VP, but I need first to "zero out" the free space. I have serch for but I have not find a solution.
Any ideas?
Thanks in advance.

---

### Post by johannes2510 on 2008-09-22
I have found this:
[http://www.linuxsecurity.com/content/view/117638/49/](http://www.linuxsecurity.com/content/view/117638/49/)
"To eliminate the traces of old removed files, one might want to wipe the empty space. The simple method is to use a standard Linux "dd" utility. To wipe the empty space on /home partition use:

dd if=/dev/zero of=/home/bigfile
sync
rm /home/bigfile
sync

I have no try... It's safe?

---

### Post by cyberdork33 on 2008-09-22
> **johannes2510 said:**
> I have found this:
[http://www.linuxsecurity.com/content/view/117638/49/](http://www.linuxsecurity.com/content/view/117638/49/)
"To eliminate the traces of old removed files, one might want to wipe the empty space. The simple method is to use a standard Linux "dd" utility. To wipe the empty space on /home partition use:

dd if=/dev/zero of=/home/bigfile
sync
rm /home/bigfile
sync

I have no try... It's safe?
it should be safe, but I am not sure if you will get any closer to your desired outcome. All that does is create a big file full of zeros on your virtual hard drive, then you delete it. 

What exactly are you trying to accomplish? I don't think I understand the problem...

---

### Post by johannes2510 on 2008-09-23
> **cyberdork33 said:**
> 
What exactly are you trying to accomplish? I don't think I understand the problem...
Thanks for answer!
I want shrink the Ubuntu virtual disk for recover free space from virtual machine to Mac HD with a tool of Virtual PC, but according with Virtual PC manual I need first zero out the free space and I don't know how do that.

---

### Post by tiresia on 2008-09-23
I think 'dd' should work quite good for you. You could use also 'shred'
I found a Link for you, just to get an idea how this utilities work
[http://www.gamedev.net/community/forums/topic.asp?topic_id=507595&whichpage=1&#3310055](http://www.gamedev.net/community/forums/topic.asp?topic_id=507595&whichpage=1&#3310055)
Anyway there is another one, that seems to be thought right for you purpose 'zerotools'
[http://koltsoff.com/pub/zerotools/](http://koltsoff.com/pub/zerotools/)
I never tried it!

Anyway you can try all of these. Just make a backup of your disk image. If it is in your 'Documents' make just a copy of it :) - Buona fortuna!

---

### Post by johannes2510 on 2008-09-23
> **tiresia said:**
> Anyway you can try all of these. Just make a backup of your disk image. If it is in your 'Documents' make just a copy of it :) - Buona fortuna!

Danke! :)
For the links but I will try with dd.
For backups I have duplicate the virtual hd so don't worry.
I will tell you the result....

Ok, report:
run dd seems fine. Virtual hd grow from 4 gig to 9....
run virtual pc shrink tool and the hd still at 9 gig.
Restore hd from backup.
Ideas?

---

### Post by cyberdork33 on 2008-09-23
> **johannes2510 said:**
> Danke! :)
For the links but I will try with dd.
For backups I have duplicate the virtual hd so don't worry.
I will tell you the result....

Ok, report:
run dd seems fine. Virtual hd grow from 4 gig to 9....
run virtual pc shrink tool and the hd still at 9 gig.
Restore hd from backup.
Ideas?
I think you should try the other posted tools. That dd command will create and file and that is not the same as zeroing the disk...

You also might check in the virtualization forum to see if there is something there that can help you.

---

### Post by johannes2510 on 2008-09-23
> **tiresia said:**
> 
[http://www.gamedev.net/community/forums/topic.asp?topic_id=507595&whichpage=1&#3310055](http://www.gamedev.net/community/forums/topic.asp?topic_id=507595&whichpage=1&#3310055)
Anyway there is another one, that seems to be thought right for you purpose 'zerotools'
[http://koltsoff.com/pub/zerotools/](http://koltsoff.com/pub/zerotools/)
I never tried it!



Seems too hard for me....

---

