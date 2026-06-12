---
title: "Vista not working after ubuntu install"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ndinadis on 2007-07-06
I know there has been a thread on this in the past but, their solution did not work for me (did it twice) 
I have set it up as a dual boot with vista with an extra "media" drive to share between the two OS"s
After installing and confirming the ubuntu installation I went to check vista, it goes to start up then stops and restarts at the progress bar. I have some outputs that may help you determine what is happening, (vista is the 60 gig partition) 

Disk /dev/sda: 234441647s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         133806419s  133806357s  primary   ntfs         boot 
 2      133808128s  195248127s  61440000s   primary   ntfs              
 3      195254010s  232717589s  37463580s   primary   ext3              
 4      232717590s  234436544s  1718955s    extended                    
 5      232717653s  234436544s  1718892s    logical   linux-swap  

Hopefully someone else has had this problem and will be able to help me.
Nick

---

### Post by MoxJet on 2007-07-06
Do you use ntfs-3g?

---

### Post by ndinadis on 2007-07-06
> **MoxJet said:**
> Do you use ntfs-3g?

I am not sure what that means. Is that the other ntfs partition?

---

### Post by Old Pink on 2007-07-06
> **ndinadis said:**
> **Vista not working after ubuntu install**

Result!

Enjoy your new setup. :)

---

### Post by ndinadis on 2007-07-06
> **Old Pink said:**
> Result!

Enjoy your new setup. :)

ha ha ha
Yeah I was expecting that, or someone to say its an upgrade 
unfortunately I need it to work again.
I have used ubuntu for about a year and a half on and off and am a big believer in linux and open source being the future (at least part of mine).

---

### Post by ndinadis on 2007-07-06
someone must know the answer to this????

---

### Post by sab0403 on 2007-07-06
Well, the partition table seems fine, perhaps Vista "senses" that the partition changed, and does something about it?

What's the other thread on the subject that didn't work?

---

### Post by ndinadis on 2007-07-06
This is the other thread with a similar problem which did not resolve my issue
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)
Yeah the partitions are all right its really odd, I am thinking it might be because the boot has been changed and there is now a boot loader

---

### Post by lbelloq on 2007-07-06
Dunno exactly how you can solve the problem, but 2 options:

- Use the Vista CD-DVD (or the recovery discs of your computer) to repair the installation.
- Find and use Hiren's Boot CD to fix the partition table.

---

### Post by ndinadis on 2007-07-06
I thought to use the vista DVD problem being it does not boot, (I had to install windows to install it Ahhhh) Its from the MSDN (I have a friend lol) I will look up the cd that you mentioned as well.
Any other ideas, it starts to boot thats the part that confuses me.

---

### Post by sab0403 on 2007-07-06
Ok, I've read that other thread. So what didn't work? Seems pretty straightforward to me.

Did you use the correct device name (which in your case would be sda1)? What errors did it report? From what I can tell, that method takes a bit of time.

Let us know.

---

### Post by ndinadis on 2007-07-06
Well it said it did work, but it did not solve the problem.
Here is the successful output after completion, but sadly vista still does not boot :(

---

### Post by sab0403 on 2007-07-06
Hmm... 

I wish I understood what the problem is, that's for sure. Let me research and I'll get back to you - probably until Monday, though.

I'll subscribe to the thread.

---

### Post by Old Pink on 2007-07-06
How about asking on a Vista forum?

Don't say Linux, you'll just be flamed outta there by Windows noobs. ;) 

Just say you were repartitioning for separate media storage or something and see if there's any "oh yeah, you just need to do **** after partitioning" steps out there? :) 

Also have a look at [http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html) - etc.

---

### Post by ndinadis on 2007-07-06
Yeah I thought it was a bad idea to ask in a vista forum as the problem would not have arisen without installing another operating system that required the new bootloader 
I will read the link you posted though.

---

