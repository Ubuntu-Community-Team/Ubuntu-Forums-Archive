---
title: "Safe way to copy files?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-18
Hey guys,

I just did a fresh install of Ubuntu 6.06 i386 last night. I had backed up my files to an external 250gb hard disk (fat32). 

The problem is when I tried copying the stuff back to my newly formatted ext3 hard disk, after copying a few files, it said that there was an error copying "xxx" file or something, and asked me to cancel, skip, or retry. A retry seemed to fix the problem(I haven't checked for the file yet), but after a few files, it would pop up again..., retry(sometimes a few times) would get me past it again.

The problem is:
1) I'm not sure whether its correctly copying the files(maybe it missed a few files, I can't check all :( ).

2) when i says it failed to copy, it says failed to copy "/home/kinson...me.doc" where "me" would be the last few letters of the filename/path, so I really don't know *which* file it failed to copy as well :(

3) Is there a better way to copy/backup files in my case/scenario?

Sorry if I sound very fussy, but its all important data to me. If I make a mistake and lose my photo's, I'll get murdered by my family :p I'll have to burn a copy just in case that happens. But seriously...any suggestions guys? :)

Cheers,
Kinson

---

### Post by alamba on 2007-03-18
Only thing I can suggest is running du <folder_name> after you copy to see if the number of MB/GB matches from your backup drive. That would be a sure shot indicator if it's missed any file. 

Perhaps rsync would suit you better next time while backing up/restoring. 

A

---

### Post by kinson on 2007-03-18
I considered rsync, but I haven't tried it yet. I initially thought of using it for incremental backups.

Btw, what would happen if there were errors while copying the files using rsync? Can I set it to continue, but log the files that had errors?

Cheers,
Kinson

---

### Post by Palypup on 2007-03-18
The same thing happened to me in reverse. ext3 to fat 32 external. I found that certain characters in the file name wouldn't copy, so had to rename the file w/o
using those characters. I copied my entire home directory to the external, so it was
no small amount. At least you have the stuff in a safe place and can be transported
to another computer. You can sort your stuff into batches, roll up your sleves and copy them through a batch at a time. Copy and check, copy and check, copy and check. Or if you are like me, always mucking about and fowling up my OS, consider just leaving that stuff there and mounting that drive.

---

### Post by kinson on 2007-03-18
> **Palypup said:**
> The same thing happened to me in reverse. ext3 to fat 32 external. I found that certain characters in the file name wouldn't copy, so had to rename the file w/o
using those characters. I copied my entire home directory to the external, so it was
no small amount. At least you have the stuff in a safe place and can be transported
to another computer. You can sort your stuff into batches, roll up your sleves and copy them through a batch at a time. Copy and check, copy and check, copy and check. Or if you are like me, always mucking about and fowling up my OS, consider just leaving that stuff there and mounting that drive.

Hrmm, not that you mention it, I think those files that were mucking up were those with funny symbols(jap file names or stuff). Not that I can see exactly whats mucking up, cause as I mentioned earlier, I can't see exactly which file is mucking up :(. If thats the case, its gonna be a pain, cause I have a lot of those files. I don't think its practical for me to do it bit by bit :(

As for mounting that drive...I use that external drive to backup my data(redundant). This time I'm trying to copy it back cause I formatted my os. :(

---

### Post by AtrejuT on 2007-03-18
yeah, different character encodings are always a pain if you copy from ext3 to fat32, they handle things differently and I never really figured out how to do it properly in any case.
for next time (though that is too late now): consider formatting the external drive as ext3, if that's an option for you. made things easier for me...

---

### Post by kinson on 2007-03-18
> **AtrejuT said:**
> yeah, different character encodings are always a pain if you copy from ext3 to fat32, they handle things differently and I never really figured out how to do it properly in any case.

Well, in this case I'm copying from FAT32 to ext3, but I suppose its the same problem :/

> **AtrejuT said:**
> 
for next time (though that is too late now): consider formatting the external drive as ext3, if that's an option for you. made things easier for me...

I would, but I also use that drive to share data with me friends when I go to their houses. I suppose since I have a smaller(40gb) partion on that hard disk, I could put the windows read/write ext3 driver there, and install it when people need stuff from me. But I don't think a lot of me friends would be happy with that :p Not to mention, I'll still need to backup those files from my external before I can format it to another file system..and I don't have another hard disk that size :p I just have a 200gb and a 250gb(for backups). Since I can't copy the files back from the 250gb to the 200gb, I'm stuck with only one copy of the files :(

Cheers,
Kinson

---

### Post by vinnn on 2007-03-18
If you ever have problems copying/moving/manipulating files, the first thing you should think of is permissions, permissions, permissions,.

The case here is that you have copied your home directory (where permissions are important) to a filesystem (FAT32) which does not support those permissions. Therefore those permissions have been stripped from the files and you would have lost any symbolic links, therefore you haven't got a proper backup.
When you're copying them back from FAT32 to ext3 you're applying ***new *** permissions to every file which are not necessarily the same permissions as they where before you copied them to the FAT32 filesystem.

You should only use unix filesystems for unix files.
In future if you're going to backup your files, copy them to a unix filesystem such as ext3 with **cp -a** which copies files/directories recursively, preserving mode, timestamps, permissions & symbolic links.
You could also log the process so you can later review everything that happened with...
```
sudo cp -av [source] [target] > /tmp/logfile.txt
```



This time though, as you've already done the damage DO NOT copy everything back in it's original place, as some subdirectories/files in your home directory such as .gconf, .gnome, .Xauthority (i think) require specific permissions set on them for you to login properly into gnome.
Depending on what you've backed up (was it just your /home directory?, did you copy the hidden directories within /home?) only copy back the files where permissions are not going to be as important such as your music/videos/documents/pictures and then reapply permissions to them...
For example...
```

sudo cp -fv /mnt/backup/home/vin/Video /home/vin && \
sudo cp -fv /mnt/backup/home/vin/Music /home/vin && \
sudo cp -fv /mnt/backup/home/vin/Pictures /home/vin && \
sudo cp -fv /mnt/backup/home/vin/Documents /home/vin > /tmp/logfile.txt
cd ~
sudo chown -R vin:vin Video Music Pictures Documents
sudo chmod -R 775 Video Music Pictures Documents

```
In the example, all the copying is done in one operation and output to a logfile, when finished you can view or grep the logfile for problems.

---

### Post by kinson on 2007-03-18
@vinnn:

Thanks for your reply. Its something I didn't think about then. So it's interesting :)

However, I'm not sure whether it would apply to me currently. Cause I Backed up 2 folders mainly.

1. Home (I didn't copy the hidden files, cause I wanted to start fresh without any previous settings) Ext3 drive I think

2. My folder with my music and all. but this was from a windows NTFS drive. I copied *this* folder in a windows xp environment. So it was kinda NTFS -> FAT32.

I haven't tried copying the /home folder back, and when I do, I might run into the problems that you decribed. But currently the problems I'm facing is copying back the folder(#2) that I backed up from my NTFS drive. So would the file permissions thing apply here? And like I said, hitting the "retry" button seemed to make the file copy successfully...until the next file of course :(

Cheers,
Kinson

---

### Post by kinson on 2007-03-21
I tried using 
[code[
rsync -av <source> <dest> > abc.txt
[/code]

To copy the files over. Most of the stuff worked, but some of them still are encountering errors :( And they aren't necessarily files with funny filenames or whatever.

```

rsync: read errors mapping "/media/usbdisk/Backup/Data/170307/Kinson/Junk/Videos/abc.mpg": Input/output error (5)

```

Any ideas guys? :(

Cheers,
Kinson

---

### Post by kinson on 2007-04-18
Didn't notice that I didn't update this after I "solved" it.

I think the problem was due to the source being a FAT32 file system. I used windows and copied some of the problem files to an NTFS partition, and tried copying it from the NTFS to my ext3 partition and it was fine. So thats what I plan on doing :)

On a side note, does anybody know how to make rsync ignore those "./" folders? Cause I don't wanna backup those hidden preference folders(or whatever they're called) to my external hard disk :/

Cheers,
Kinson

Backup up me stuff now in preparation to install Feisty when its released tomorrow :p ...When did any windows user ever prepare and anticipate a release like this? lols !!

---

### Post by seetho on 2007-04-18
> **kinson said:**
> 
I think the problem was due to the source being a FAT32 file system. I used windows and copied some of the problem files to an NTFS partition, and tried copying it from the NTFS to my ext3 partition and it was fine. 

The filesystem of the source drive should not be a problem.  I think you may want to check the integrity of your hard drives.  Sometimes when they are about to go bad you get funny problems like this.

---

### Post by zorkerz on 2007-11-07
Hi I have a simpleish question about copying files I hope. I have an external drive that I backup my important data two. When I copy over a number of folders that are already on the backup drive I am only given the option to "replace" the entire folder or to "skip" it. What i would like to be able to do is to add only the new files in each folder. A higher functionality would be to replace modified files also but this is not too important for me.

For example my music is stored like this. /music/artist/album recently i have added albums to multiple artists I would like to be able to copy the entire music folder over and have it only add the new music.

I have been doing this all simple gui but if there are other better solutions im up for learning

thanks

---

### Post by schorsch on 2007-11-07
Have you already tried grsync?

---

### Post by zorkerz on 2007-11-07
no i have only tried a simple gui copy past. I kinda like doing it manually because I don't keep the backup exactly the same its also extra storage space but if that is the best/only way I can always change my organization around.

---

### Post by kinson on 2007-11-08
You really should look into rsync, or at least grsync(rsync with a graphical tool if I recall properly).

Its a very handy backup/sync tool :)

Cheers,
Kinson

---

### Post by zorkerz on 2007-11-08
Thanks for the advice all its on my list now if i have trouble I will be sure to let you know.

---

