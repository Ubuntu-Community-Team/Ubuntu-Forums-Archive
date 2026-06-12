---
title: "Windows Vista Backup -&gt; Ubuntu, pasting Zips together"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by HungarianErich85 on 2007-05-14
Before I switched to Ubuntu, I used the Windows Vista backup program to store my files.  This resulted in hundreds of .zip files (each about 200 MB) and a whole bunch of catalog files of type .wbcat and .wbverify.  I have no problem manually unzipping these onto Ubuntu, the only thing though is that for my files that are > 200 MB, Windows split them into how ever many zip files, and there's no obvious demarcation and the names aren't different.  How do I paste them back together?  I believe it'll utilize the catalog .wbcat files, but is there a Ubuntu utility to go through this for me?

Thanks for help... I'd hate to have lost all of my video files.

- Erich

---

### Post by dstew on 2007-05-14
I have spent some time looking for a tool to restore Vista backups to Ubuntu, but have not found one yet. You might have to restore the files to another Vista computer, then copy them over to your Ubuntu system.

---

### Post by dlodge on 2008-05-22
> **HungarianErich85 said:**
> Before I switched to Ubuntu, I used the Windows Vista backup program to store my files.  This resulted in hundreds of .zip files (each about 200 MB) and a whole bunch of catalog files of type .wbcat and .wbverify.  I have no problem manually unzipping these onto Ubuntu, the only thing though is that for my files that are > 200 MB, Windows split them into how ever many zip files, and there's no obvious demarcation and the names aren't different.  How do I paste them back together?  I believe it'll utilize the catalog .wbcat files, but is there a Ubuntu utility to go through this for me?

Thanks for help... I'd hate to have lost all of my video files.

- Erich

Check out this link:
[http://blogs.technet.com/filecab/archive/2007/06/19/how-windows-vista-backup-uses-zip-files-to-store-backups-and-how-to-extract-files-from-zips.aspx](http://blogs.technet.com/filecab/archive/2007/06/19/how-windows-vista-backup-uses-zip-files-to-store-backups-and-how-to-extract-files-from-zips.aspx)

In summary, if you have a 700MB file named DISC1.MP4, it will be split into 4 zip files - 3 around 200MB and 1 of about 100MB - containing a file named DISC1.MP4. If you simply extract all the zip files, each extraction will overwrite the previous segment.  The order you find the segments in the zip files (conveniently numbered to indicate order) is the order you must sequence the new file names in. You have to manually extract each of the 4 parts from the zip files and give each a unique name. E.g. You need to give each file a name such as
```
DISC1_1.MP4
DISC1_2.MP4
DISC1_3.MP4
DISC1_4.MP4
```

Followed by the command (only in Windows / DOS):
```
copy /b disc*.mp4 disc1.mp4
```

I haven't tried this myself yet, but I expect the unix command to be
```
cat DISC1_*.MP4 > DISC1.MP4
```

It wouldn't be difficult to write a shell script to do this if you are so inclined.

- Dan

---

