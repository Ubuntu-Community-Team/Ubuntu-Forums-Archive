---
title: "Hard Drive Access"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by joedirt313 on 2007-10-14
Hi I am new to linux and the ubuntu os but so far I am really excited about using it and getting to learn it. 
My question is quick and painless I have two external hard drives that I use for storage connected via usb. Ubuntu recognizes them and the files which is great but I want to make some changes or download files to the hdd's though it states in properties that they are read only.
How do I change their accessibilities in ubuntu . No I am not trying to change anything on the main internal  hd's just the external ones to read and write.
Thanks in advance to anyone who helps me on this or even takes the time to read this post.

---

### Post by bsharp on 2007-10-14
What are they formatted in?  It would be best if they were formatted in FAT32 because (someone correct me if I'm wrong) NTFS write support is experimental at this point.

---

### Post by conehead77 on 2007-10-14
> **bsharp said:**
> What are they formatted in?  It would be best if they were formatted in FAT32 because (someone correct me if I'm wrong) NTFS write support is experimental at this point.

NTFS writing is supported in Gutsy, so it should be quite stable i think.

---

### Post by Frak on 2007-10-14
> **joedirt313 said:**
> Hi I am new to linux and the ubuntu os but so far I am really excited about using it and getting to learn it. 
My question is quick and painless I have two external hard drives that I use for storage connected via usb. Ubuntu recognizes them and the files which is great but I want to make some changes or download files to the hdd's though it states in properties that they are read only.
How do I change their accessibilities in ubuntu . No I am not trying to change anything on the main internal  hd's just the external ones to read and write.
Thanks in advance to anyone who helps me on this or even takes the time to read this post.
When you Right Click it and go to the last tab, what is the mount point of them?

---

### Post by scrooge_74 on 2007-10-14
> **bsharp said:**
> What are they formatted in?  It would be best if they were formatted in FAT32 because (someone correct me if I'm wrong) NTFS write support is experimental at this point.

ntfs read/write  support works very well since at least last year

On the original question, it depends on how the drives are formated, it would seem they are in ntfs and that would be the reason you can't write to them like if they were a usb pendrive.

the ntfs package for read/write is ntfs-3g

---

### Post by Frak on 2007-10-14
> **scrooge_74 said:**
> ntfs read/write  support works very well since at least last year

On the original question, it depends on how the drives are formated, it would seem they are in ntfs and that would be the reason you can't write to them like if they were a usb pendrive.

the ntfs package for read/write is ntfs-3g
ntfs-3g is already installed on Feisty and Gutsy, and is completely stable.

---

### Post by joedirt313 on 2007-10-14
I do apologize thery are formatted in ntfs
HD1 not a big deal older and less memory and has files already.
HD2 just bought this weekend plug and play 250 gigs and but I am guessing upon automatically plugging it in windows(I am dual Booting)
Formatted to ntfs.
Now in windows I have completes access to it and right click to format but only option in that is ntfs not fat32?
Damn sorry this turns out to be a windows question lolololol.....

---

### Post by Frak on 2007-10-14
> **joedirt313 said:**
> I do apologize thery are formatted in ntfs
HD1 not a big deal older and less memory and has files already.
HD2 just bought this weekend plug and play 250 gigs and but I am guessing upon automatically plugging it in windows(I am dual Booting)
Formatted to ntfs.
Now in windows I have completes access to it and right click to format but only option in that is ntfs not fat32?
Damn sorry this turns out to be a windows question lolololol.....
Never, **EVER**, format a drive larger than 100GB with FAT32, it doesn't have the capability.

But,
```
gksudo nautilus
```
Then navigate to /media/<drive> and you should be able to write.

Also, you can goto /dev/<drive> to change permissions of who can write.

---

### Post by joedirt313 on 2007-10-14
Thanks didnt know that about the formatting of large Hard drives
But being that I am totally new to ubuntu please could you walk me through the steps of what you just said on the "gksudo nautilus" I wouldnt know where to begin in the manner in which you posted it
anything I do know has been through crash and burn or forums like this.
Sorry but do appreciate the help.

---

### Post by Frak on 2007-10-14
Goto Application-Accessories->Terminal
Then type
```
gksudo nautilus
```
Then double click on File System(Sidebar) -> dev

Then find find your HD, which is probably scd, then right click -> properties -> File Permissions -> (second row) Read & Write Access.

---

### Post by joedirt313 on 2007-10-14
Ok went into the dev file - then to disk folder-then to by label folder- then in there it has what I call my hd EXHD2 but when I right click in the properties under permission it states it to be read and write though on my desktop or comp it says read only
Am I doing something wrong?

---

