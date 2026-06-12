---
title: "free space on FAT32?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by l0l on 2006-05-24
Hi, this is my first post here, so, be nice..

I installed Ubuntu 2 days ago and I must say I am very impressed. I never thought Linux could be so easy to install/configure. It is better than Windoze in some ways, for example, I have no problems w/ my printer (in Win it asked me to install it everytime I would turn it on) and I can play videos perfectly (in Win I had a problem with the video driver). :p :-D :D 

Now here is my problem. Maybe it isn't really a problem, but anyway I'm desperate to find a solution.

I have a FAT32 partition mounted automatically. It was nearly full, so I deleted some files, but the free space did not increase (I deleted ~ 1.5GB). I used bittorrent to DL a 300MB file, and it sort of filled the HD, although there should have been at least 1.2GB free. Does Ubuntu have problems w/ 'getting' the correct amount of free space?

Another question: My FAT32 partition shows one folder that I cannot edit. Why is this, if I can edit all other folders in the partition?

Thanks.

---

### Post by mority on 2006-05-24
Are you sure that you actually _deleted_ the files or did you maybe just move them to trash? In the latter case the disk space will be freed as soon as you empty your trash folder.

Speaking of bittorrent: File sharing tools like bittorrent use much more diskspace during downloading a file than the finished file eventually will have. This is because those tools download files in very little chunks and has to store meta information about what chunks belongs where in the file. After the download has finished the meta information gets deleted.

The issue with the folder you can't edit: can you post the output of 'ls -l' in the folder where this folder is?

---

### Post by l0l on 2006-05-24
My ls -l on the partition F is:

```

dr-xr-xr-x  23 root root 32768 2005-06-13 11:31 documents
drwxrwxrwx   4 root root 32768 2005-06-13 01:57 DOCUMENTS AND SETTINGS
drwxrwxrwx   5 root root 32768 2006-05-24 15:02 downloads
drwxrwxrwx  42 root root 32768 2005-06-13 11:28 programs
drwxrwxrwx   2 root root 32768 2005-06-14 00:10 Recycled
drwxrwxrwx   2 root root 32768 2005-06-10 22:47 Skolas darbinji
drwxrwxrwx   3 root root 32768 2005-06-13 01:38 System Volume Information
drwxrwxrwx   6 root root 32768 2005-06-10 23:43 usefulls
drwxrwxrwx   2 root root 32768 2005-07-04 07:41 Windows

```

a keylock icon appears next to my "documents" folder, and as far as i can see, its letters (drw) are different than for the other directories. What does this mean?

The free space is now back to what it should be. I dont really know what I did, but now it has removed the files.

As for deleting files through the trash bin; I'm not sure I saw a full trashbin icon. Is there a way to delete a file without placing it into the trashbin (i.e. Shift+Delete in  Windoze)?

---

### Post by mority on 2006-05-24
[QUOTE=l0l]
a keylock icon appears next to my "documents" folder, and as far as i can see, its letters (drw) are different than for the other directories. What does this mean?

As for deleting files through the trash bin; I'm not sure I saw a full trashbin icon. Is there a way to delete a file without placing it into the trashbin (i.e. Shift+Delete in  Windoze)?[/QUOTE]

You should read some documentation about unix file access permissions cause this is really fundamental when operating a unix like system (which ubuntu is).
This is the file security chapter of a really well written introduction to linux: [http://www.tldp.org/LDP/intro-linux/html/sect_03_04.html](http://www.tldp.org/LDP/intro-linux/html/sect_03_04.html)

You should consider to read not just this chapter but the whole guide. Trust me, it will make you much more efficient using ubuntu in the long run.

A quick solution to your problem: type 'chmod 777 documents' as root in the folder where the read-only folder is. Then you will be able to delete it.

There is certainly a way to delete files in gnome without moving them to trash but I don't know what the key combination is. It shouldn't be difficult to find it out with the gnome help. Or you delete files through CLI with the 'rm' command. That will delete them irreveribly.

---

### Post by Sgood1971 on 2006-05-24
[QUOTE=mority]This is the file security chapter of a really well written introduction to linux: [http://www.tldp.org/LDP/intro-linux/html/sect_03_04.html](http://www.tldp.org/LDP/intro-linux/html/sect_03_04.html)
[/QUOTE]

Nice link, thanks.


[QUOTE=l0l]As for deleting files through the trash bin; I'm not sure I saw a full trashbin icon. Is there a way to delete a file without placing it into the trashbin (i.e. Shift+Delete in Windoze)?[/QUOTE]

Shift+Delete will work in Ubuntu as well.

---

### Post by l0l on 2006-05-24
Thank you for the link.

[QUOTE=mority]
A quick solution to your problem: type 'chmod 777 documents' as root in the folder where the read-only folder is. Then you will be able to delete it.
[/QUOTE]

i did this (with the correct path) as 'chmod 777 /home/janis/F/documents' and i got an error
 "chmod: changing permissions of `/home/janis/F/documents': Operation not permitted."

I don't really understand the reason for this error.

[COLOR="Red"]**EDIT: **[/COLOR]Forgot to add 'sudo' in front of the line. Thanks for all the help, mority!

---

### Post by mority on 2006-05-24
[QUOTE=l0l]
[COLOR="Red"]**EDIT: **[/COLOR]Forgot to add 'sudo' in front of the line. Thanks for all the help, mority![/QUOTE]

You're welcome :)

---

