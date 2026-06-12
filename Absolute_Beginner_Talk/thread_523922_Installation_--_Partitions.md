---
title: "Installation -- Partitions"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by stag65 on 2007-08-12
The install instructions are not clear to me (as a Linux newbie).

Twice I have gone thru the CDR install steps up thru the partitioning routine, and then backed out because I was unclear of what would happen next.

I have 2 drives and a number of partitions on each (FAT32 and NTFS), and am running WinXP SP2

I can use a 10GB, FAT32 partition available for Ubuntu. 
Will somebody please advise me:

1.  Can FAT32 be used for Ubuntu?, else
    Which format option would be used for Ubuntu partitions?
    
2.  What partitions should be created in my 10GB space?

3.  How should they be identified?  Is the root "/", or "/{root}"

4.  How should I size these partitions)?
    2GB min for the root. 
    What size for the /swap?
    Which others are most useful?
    
Thanks

---

### Post by insane_alien on 2007-08-12
yes FAT32 can be used to install on but it is recommended to go for a native format as FAT32 is a sucker of the ***.

with only 10GB available you would make 2 partitions a '/' (root) and a swap partition.

you'll identify them in the installer as '/' and 'swap' (without quotes of course)

make the swap 512MB and assign the rest to /

since the space is constrained it would be better for a single partition than to bother with /home and /boot partitions.

i also urge you to choose ext3 over FAT32. there are driver available for windows that can allow it to read ext3.

---

### Post by stag65 on 2007-08-12
Thanks for the quick response.

Your answers are succinct and exactly what I was looking for.

I'll give it a try

---

### Post by AndyCat on 2007-08-12
Hello there. This might help you since this is your first time with linux. Instructions are pretty clear.
In case you dont understand it just add me on msn (naotse@hotmail.com) or just post in here. Ill be willing to assist you.
check this first : [http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04)

---

