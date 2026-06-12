---
title: "a CD-RW that cant be re-written b/c of read-only...."
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-04-16
i have a CD-RW that, if i remember correctly, was burnt using a windows system, now i want to update my music on it using ubuntu, but its read-only... (i already right clicked --> properties --> permissions but that isnt able to be changed)

how do i fix that?

---

### Post by rmemm on 2007-04-16
You'll need to use something like K3B to write new files I think.  As far as I know only DVD+RWs can be mounted as actual RW volumes.

What file system do you have on the RW?  Iso9660/CDFS, UDF, FAT,...?  If Iso which is probable than it's not an RW format in terms of directly mounting the FS.  You'll need to use K3B instead.

UDF, FAT, Ext2, etc can be mounted RW if they are on a direct access media -- but as I said -- DVD+RWs are the only media I know of that support this.  I've done this with DVD+RWs and Ext2 -- but have not been able to do this with UDF though and have not tried FAT.

Rob

---

### Post by Fittersman on 2007-04-16
i installed the k3b thing, but it doesnt want to support .mp3 files (thats all i have so i dont know if it just doesnt like music, or if its just .mp3)

and sorry, but i dont know the answers to any of your other questions.

---

### Post by NeoLithium on 2007-04-16
Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  Particularly the section in regards to installing the extra codecs, which will give you support you need for mp3's, et al.

---

### Post by Fittersman on 2007-04-16
i already have all the mp3 codecs (you need these to listen to songs right?), i can listen to all my mp3s, its just with these burner programs im having problems for some reason

---

### Post by dwblas on 2007-04-17
You can burn to a CD-RW in a single or multi-session mode.  If you originally burned in a single session mode I don't think you can add files.  You will have to copy what is on the CD to disk, erase or reformat and then copy everything to it.  I use burncenter because it's simple, but this is all personal preference.

---

### Post by Fittersman on 2007-04-17
it wont let me clear the cd-rw either, its just like a cd (non-rewritable)... so i really dont know what to do

---

### Post by rmemm on 2007-04-17
If your talking about k3b -- I had the same problem with DVD+RWs.  If it's the same for CD-RWs then I can tell you how you do it.  If not I don't know.  At least for DVD+RWs the way you start over is once you selected BURN there is a settings tab in the burn dialog.  You have to either select Start Multisession or No Multisession and when you start the burn it will ask you if you want to re-write the DVD. At least for DVD+RWs the settings tab is key.

I've also noticed in k3B there is an erase cd-rw menu selection.  I've never tried that -- but maybe it does something useful... don't know.

Oh -- and yes -- I think the rewriting thing is totally non-obvious.

Rob

---

### Post by Fittersman on 2007-04-18
well, you solved my erasing problem, but i cant even get to the burning part, it wont let me open some of my .mp3 files (why only some of them? that doesnt make and sense to me...) 

im past the permissions problem now, thanks 

now on to the reason why some .mp3 files arent supported

EDIT: well, i guess i screwed up when i made my playlist for some reason, some of my songs were trying to be copied from my mp3 player for some reason (which wasnt plugged in) lol, i feel dumb now :D

thanks for all the help though

---

