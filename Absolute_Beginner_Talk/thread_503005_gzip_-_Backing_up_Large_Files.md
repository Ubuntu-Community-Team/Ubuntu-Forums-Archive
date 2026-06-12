---
title: "gzip - Backing up Large Files"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by mrsticks on 2007-07-17
Ive got a Win2k application server.  I have installed cygwin / rsync on the windows box and every night at 10PM it does successfully back up about 30GB to my backup server, which has Dapper 6.06LTS on it.  The files are on a RAID array that uses the ext3 FS.
3 files in particular are > 4GB, they are 4.5GB, 7GB and 10GB.  I can do a "ls -lash" on these files and it lists them as those sizes.  
Then every night these files, along with many others are individually gziped for archive.  Last night I specifically gzipped these 3 files, with unexpected results.
They successfully gzipped, but when I did "gzip -l" on the files, the compressed and uncompressed columns worried me.
The 7GB file was compressed to 100MB, but the uncompressed column showed it at only being 3.1GB.
The 4.5GB file was compressed to 85MB, but the uncompressed column showed it at only being 450MB.
The 10GB file was compressed to 28MB, but the uncompressed column showed it at only being 1.7GB.

Ive done some googling, and saw that gzip 1.2 had file size limitations, but 1.3 should have none.  "gzip --version" confirms that I have gzip 1.3.5, which cames shipped with Dapper LTS, and Synaptic shows no newer versions.

The mere fact that the files uncompressed on the RAID array ( ext3 FS ) show up as being > 4GB leads me to believe that this is not an issue of a file system size limit, as the wiki tells me that the individual file size limit is 16GB at it's smallest kb block size.  I dont know which kb block size Dapper uses, but at any rate, none of these files is close to 16GB.

So this leads me to blame gzip in some way.

Anyone have any clues as to why gzip seems to be cutting off these files when compressing?

Any || all suggestions || advice welcome.

-peter

---

