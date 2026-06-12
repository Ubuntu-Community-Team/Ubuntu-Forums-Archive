---
title: "NTFS mount, with write support?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-26
I ve just done a clean install of WINXP pro and Dapper.

Stupidly I formatted my winxp partition with NTFS (didnt know it would be a problem). So I cant write to the NTFS partition. I found this on the forums:
[http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs)

Is there any other way doing this, Im seriously considering reformatting everything all over again. And using fat32 for windows.

Is there a way I could just reformat my winxp partition and just install windows again with out having to reformat my unbuntu install? 

thanks for any help!

---

### Post by bodhi.zazen on 2006-08-26
Yes, you have seveal options.

First option is to make a shared FAT32 partition.

Second is to try this:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009).

---

### Post by mostwanted on 2006-08-26
> **bodhi.zazen said:**
> Yes, you have seveal options.

First option is to make a shared FAT32 partition.

Second is to try this:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009).

I used that tutorial (which seems simpler than the other one) and it works brilliantly.

---

### Post by bplus on 2006-08-26
hmm, maybe i'll just go for tutorial way.

Anybody have any problems?
Big files problematic?

---

### Post by bodhi.zazen on 2006-08-26
I mount a shared NTFS USB drive, rw, on Linux with no problem. Can write data to the USB with either Windows or Linux and have not had problems.

I would be cautious about writing to a "mission critical" ntfs partition.

---

