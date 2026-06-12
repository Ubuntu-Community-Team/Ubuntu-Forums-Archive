---
title: "permissions problem copying individual sound files"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-30
My long-term goal is to set up a Ubuntu computer more or less exclusively as an Amarok machine.

Am in the middle of copying all my sound files from my Mac G5 to a new RAID ARRAY on the Ubuntu.

The sound files are currently on a series of five USB drives.  I start copying, and, for the most part it goes smoothly, but I keep running into this problem:

I stopped copying on my big drive, because I was encountering too many of those files with permissions problems.

They seem to be completely random - some are MP3s, some are AACs, there's no rhyme or reason.  The copying program will go along smoothly for 5-10 minutes, and copy maybe 1,000-2,000 files, and then hits a file with a permissions issue and stops.  I get roughly a dozen of those, then it starts copying again - and 5 minutes later, same darn thing!  (NONE of these are purchased files from the iTunes store with DRM - they are all ripped from my CDs.)

Is there anything I can do to fix permissions on all files on a drive?

When I view the files on the Ubuntu, they show up with a little lock and an X on their icon (see illustration)

[http://docs.google.com/Doc?id=dfm5htp9_0g4whdc](http://docs.google.com/Doc?id=dfm5htp9_0g4whdc)

[http://docs.google.com/Doc?id=dfm5htp9_2f7q8t7](http://docs.google.com/Doc?id=dfm5htp9_2f7q8t7)

when I view them back on the Mac, there's no difference between these files and any other - like I say, it seems to be completely random...

am grateful for any help...

(am going to post this on the Amarok forum as well, now that I think of it..)

---

### Post by tdrusk on 2007-09-30
> **willfriedwald said:**
> My long-term goal is to set up a Ubuntu computer more or less exclusively as an Amarok machine.

Am in the middle of copying all my sound files from my Mac G5 to a new RAID ARRAY on the Ubuntu.

The sound files are currently on a series of five USB drives.  I start copying, and, for the most part it goes smoothly, but I keep running into this problem:

I stopped copying on my big drive, because I was encountering too many of those files with permissions problems.

They seem to be completely random - some are MP3s, some are AACs, there's no rhyme or reason.  The copying program will go along smoothly for 5-10 minutes, and copy maybe 1,000-2,000 files, and then hits a file with a permissions issue and stops.  I get roughly a dozen of those, then it starts copying again - and 5 minutes later, same darn thing!  (NONE of these are purchased files from the iTunes store with DRM - they are all ripped from my CDs.)

Is there anything I can do to fix permissions on all files on a drive?

When I view the files on the Ubuntu, they show up with a little lock and an X on their icon (see illustration)

[http://docs.google.com/Doc?id=dfm5htp9_0g4whdc](http://docs.google.com/Doc?id=dfm5htp9_0g4whdc)

[http://docs.google.com/Doc?id=dfm5htp9_2f7q8t7](http://docs.google.com/Doc?id=dfm5htp9_2f7q8t7)

when I view them back on the Mac, there's no difference between these files and any other - like I say, it seems to be completely random...

am grateful for any help...

(am going to post this on the Amarok forum as well, now that I think of it..)

Try going to the folder on the drive, right click, properties. Make sure your permissions are set so you can read and write. That MIGHT remove the lock.

---

### Post by willfriedwald on 2007-09-30
ah - I think I have it solved, thanks to input from Mr. Meyer... I can fix the permissions on the mac end (I think) and / or do a universal permission fix rwrr on the Ubuntu end...

thanks - will let me you know if there are any problems...

thanks also to Mr. Fuzzy for his very helpful reply!

will

---

