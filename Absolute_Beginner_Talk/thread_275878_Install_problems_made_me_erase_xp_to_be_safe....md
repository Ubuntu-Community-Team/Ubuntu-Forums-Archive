---
title: "Install problems made me erase xp to be safe..."
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-12
Hello again, this is a long explaination to 2 fustrating days, but the simple question is at the bottom. 

Well, I ran into some more problems with my install. It seems that the alternate i386 xubuntu 6.0.6 install frooze in the same place for two different installs. I checked them both with md5summer and they both passed. After the first bad install I had to re-install WinXp and after I did, I checked the disk out from the xubuntu boot screen "check disk" and it failed the md5summer. So I downloaded again form the xubuntu 6.0.6 alternate i386 so I could do a "text install", and after passing md5summer I re-checked on the xubuntu boot screen, and it passed.

Then it frooze in the same spot.

The first time it frooze it totally screwed my notebook up because the partitions formed for the Fat32 and the ext3 for linux (plus 1gb swap) but the actuall linux installs never installed because they frooze while 60% finished, and when I went back to my Xp after the bad install, I was having an error message that kept having my Xp's boot up page check disks for errors, and when it finally booted correctly, my Xp was very slow and sometimes not responding to simple things like clicking on My Computer and My Documents.

So, like I said above, I re-installed the Xp and tried the xubuntu text install process all over with a new ISO burn and both the md5summer and the xubuntu boot screen "check cd" verifications, and it frooze again.

This time my Xp only showed the "check disks" message once, and the add hardware message once and worked fine. It still had created the new Fat32 partition. So I went ahead and downloaded the "Desktop 6.0.6" version from Softpedia and it passed both md5 tests and booted and installed fine.

The thing is, is that when I got to the manual edit of my partition, I had all of the old partitons from the last incomplete install, and 2 new ones, and I didn't really know what to do and I was just over the process (windows takes so long), so I went back and decided to just re-write the whole 60gb to xubuntu 6.0.6. instead of guessing.

So my question to this long confussing post is: Can I now add windows xp to my notebook that only has xubuntu 6.0.6, and create a small Fat32 drive about 5gb or less, like 3gb for file transfer? How would I go about doing that.

Thanks and sorry for the novel,
-c.

---

### Post by nalmeth on 2006-10-12
the Gparted liveCD is getting better and better, it's good for your partitioning needs.

I may be wrong here, but I've gotten the impression from other users that problems arise unless windows is the first partition on the table.

So you may need to move the xubuntu to the end, add your media partition, then install windows. If you create a FAT32 partition first, I've heard you can tell the windows installer to use it rather than defaulting to NTFS.

Hopefully that answers a couple Q's, I'm sure others can elaborate

---

### Post by crimesaucer on 2006-10-12
Thank you, I might just use my xubuntu desktop and add all the packages that can best replace the xp, and if I'm totally happy with it then maybe I won't even have to install xp at all. 

At least I'll rest for a few days because I just spent almost 2 days with all of the re-installs and disk burning, plus all of my data back ups.

but of course, any posted info or instructions will help me so please, if anyone has the exact instructions or can link me to a guide, that would be appreciated.

Thank you.

---

