---
title: "Once commited, is there any going back?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by socalsrh on 2007-03-01
Hi. First post here. I have had Ubuntu Dapper Drake installed for about a week now and am really liking it. The only headache so far is getting my wireless network up and running, so I'm returning a Linksys WMP54G v4.1 to the store for a NATIVE wireless card this weekend. Other than that, I'm impressed with the ease of use and how well WINE handles win32 apps that I use commonly. I have almost completely freed myself from the m$ teat; which I am quite proud of.

I have a 300gb sata drive currently connected by USB which is formatted in NTFS with a large percentage of my vids, music, etc. on it. I am considering temporarily copying the files to my home folder and then formatting the drive to ext3 and copying the files back over to the ext3 formatted drive for archival of my data with full read/write privileges. 

My question is...if for whatever reason I decide that I need or would want to go back to windoze, is it possible to read the newly ext3 drive in windows and recover my data from the drive in windoze? I don't have XP installed anymore =) and haven't tested that out yet. I would just like to know that all of my data wouldn't be lost on a file system that can't even be recognized by windoze. I assume it's the same deal as in ubuntu with a NTFS drive only being read only, but I would like to be certain of that. Thanks.

---

### Post by meng on 2007-03-01
You can install fs-driver in Windows [www.fs-driver.org](www.fs-driver.org) and then Windows will recognize the ext3 partition.

Another option would be to use ntfs-3g for read-write access to an NTFS partition through Linux (search the forums if you're interested). ntfs-3g was considered experimental until recently.

Personally, I prefer the first option.

---

### Post by socalsrh on 2007-03-01
Thanks for the quick reply. That's exactly what I was looking for. I'll go with the first option and bookmark that link for future reference; though I doubt I'll go back to windoze. Free software ownz. Thanks again.

---

