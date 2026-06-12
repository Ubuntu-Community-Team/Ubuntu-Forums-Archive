---
title: "Japanese named files not appearing in Nautilus"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by mierinco on 2007-07-11
Hi all. I certainly hope this is a beginner question.  

I have just recently loaded up Ubuntu 7.04 Feisty Fawn on a 1 Ghz AMD Athlon.  I managed to mount my external USB drive that is formatted as NTFS with NTFS-3g and all was going well until I discovered that a lot of files weren't appearing.  I have determined that the similarity between these files is that they all have Japanese characters in their file name.  I checked to make sure they still exist on my Windows XP box and they do indeed.

The odd thing is that my external drive is labeled &#30334;&#24335; and this shows up just fine as it is mounted in /media/&#30334;&#24335;.  I can type Japanese characters (&#12459;&#12479;&#12459;&#12490;&#12289;&#12402;&#12425;&#12364;&#12394;) because I have managed to setup SCIM with ANTHY.

For the life of me I can't figure out why folders and files with Japanese characters are not appearing AT ALL.  This happens with MP3's (which I have a l have a lot of that are named in Japanese) and folders (containing those MP3's.

I cannot for the life of me figure out what is going on and I would greatly appreciate the help.  Thanks in advance for any help anyone can provide.  If any more information is provided please let me know.

---

### Post by compwiz18 on 2007-07-11
What filesystems are you using?  Mine show up on ext3 and fat32 file. (I just copied your kanji &#30334;&#24335; because I don't have scim installed right now and named a file after them).  Maybe try enabling hidden files?  That shouldn't have anything to do with it but you never know :P  I've never had that problem in my experience typing Japanese...

---

### Post by mierinco on 2007-07-11
The external drive's file system is NTFS.  When I plugged in the drive it automatically detected the drive's label which is &#30334;&#24335; (which I thought was weird since the other files that are named in Japanese wouldn't appear).  I have been able to mount it as I said but all the files are not showing up.  Only the ones that have Japanese characters in them are not showing up in the browser (thus not allowing me access to the files, since I don't know another workaround).

I have enabled hidden files, allowing me to see files like the windows thumbs.db and the system volume information directory, but that has not allowed me to see the files that have Japanese characters in their name.

---

