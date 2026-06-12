---
title: "Setting up for dual boot, would like to ISO current copy of Windoz"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by paulmo_on_tour on 2007-02-12
Hello all,

Finally have a reason to get off my bum to install Ubuntu (dead hard drive) on my Alienware laptop.

After trolling the forums, have decided on the following to divide up my nice and shinny 100G drive:

12G, NTFS for Windows and Office (and any other programme that needs to be on "C")
18G, NTFS for any other programmes such as AutoCAD, VectorWorks, WYSIWYG Adobe, etc...
2G, ext3 for swap (keeping in mind the "x2" of Ram)
10G, ext3 for Linux and some data
The rest, Fat32 for data, at a later date may convert over to to ext3 or somthing but would like some time under my belt as far as Linux goes.

If I could trouble everyone for comments on the above, that would fantastic!  Also, would it be easier to do my Window partitions before the Linux partitions?

But before I even BEGIN installing Ubuntu, I would dearly love to find some freeware Window spyware/virus protection.  Am looking to shy away from Norton, IMO it's a great programme, but is a memory and HDD hog!  

Also, looking to do an ISO copy of my window (:/C) drive so I can quickly recover the next time it crashes or if I want to reinstall that drive for whatever reason.

Of course I'm "googling" it, trolling this forum and others, but would like any suggestions for this particular situation.  

I'm in no real big hurry to install Ubuntu, but have to get the "Windows side of life" back up and running.  


Cheers,

Paulmo_on_tour

p.s. if this needs to be move, please move to the correct forum!....

---

### Post by seshomaru samma on 2007-02-12
Since you cannot have more than 4 primary partitions why dont you unite the second NTFS partition with the FAT32 data one? You can have your Windows programmes running on a FAT32 and use it to store data at the same time. This way you will be able to access the data from the Linux side.
. Linux has a programme called partimage which can make backups but i dont know how it deals with Windows and anyway you would need to have Linux running in order to use it. Probably better to ask in a windows forum.
On Windows machines I use AVG , adware and spybot , I also scan all partitions weekly with ClamAV, ewido and Panda (online scan) . I rarely get a virus.
On Linux I don't run any AV.

---

### Post by paulmo_on_tour on 2007-02-12
seshomaru samma,

Thank you.  I'll check out your suggestions for AVG, have used adware and spybot for years.  Will also check out partimage, have seen it discussed in other forums.

I will post this question in Windows forums, but one quick question, the 4 partition rule, is that a window or linux rule?  I do remember hearing that years ago, but completely forgot about that requirement.

Again, thanks!

Paul

---

