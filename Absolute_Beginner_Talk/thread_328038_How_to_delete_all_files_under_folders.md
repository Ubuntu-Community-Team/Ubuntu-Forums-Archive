---
title: "How to delete all files under folders"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-30
I'm using shredder to scramble and delete my files. I did a cmd on a folder which didn't work so I did ~/toshred/* which deleted all the files except the folders under this level.

I then tried adding more stars to delete the folders and their contents (~/toshred/*****) but that didn't work, kept giving me back that it's directories. There are hundreds of folders, It would take me yonks to do it all manually.

What's the correct code? :confused: :confused: :confused: :confused:

---

### Post by Pobega on 2006-12-30
The reason that isn't working it because ~/toshred/* is everything AFTER ~/toshred, not including it. I'm pretty sure rm -r <directory> should work fine.

```
rm -r ~/toshred
```

---

### Post by rlozano on 2006-12-30
did you try using the -R option of rm? and make sure that you own the folder otherwise you have to do it as a root

---

### Post by pseudonym on 2006-12-30
I've never used shredder but it sounds like you need to include a recursive option in your command line, like 'rm -r' for simple file deletion inside directories...

---

### Post by linuxbun on 2006-12-30
I'm a bit confused now as according to the shredders man page:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?shred+1](http://unixhelp.ed.ac.uk/CGI/man-cgi?shred+1)

...there is no "rm" option.

Everything in "toshred" folder I want to shred. 

My command is: shred -z -u -v ~/toshred/*   but that's only done the files. I want the directories shredded and deleted too :confused:

---

### Post by pseudonym on 2006-12-30
Hmm...that manpage only talks about files in the singular. At the bottom, though, it says -

The full documentation for shred is maintained as a Texinfo manual.  If
       the info and shred programs are properly installed at  your  site,  the
       command

	      info shred

       should give you access to the complete manual.

Have you looked it up?

Also, is there a specific reason you're using shred? Are you sellling the hard drive, perhaps, and want secure deletion because of that? If so, there are drive-wiping tools you can use that will make life easier for you. If this is what you're doing, I'll explain more...

---

### Post by linuxbun on 2006-12-30
> **pseudonym said:**
> Hmm...that manpage only talks about files in the singular. At the bottom, though, it says -

The full documentation for shred is maintained as a Texinfo manual.  If
       the info and shred programs are properly installed at  your  site,  the
       command

	      info shred

       should give you access to the complete manual.

Have you looked it up?

Also, is there a specific reason you're using shred? Are you sellling the hard drive, perhaps, and want secure deletion because of that? If so, there are drive-wiping tools you can use that will make life easier for you. If this is what you're doing, I'll explain more...

Yes it is, i'm shredding purely for security incase myhdd gets into the wrong hands and somone tries recover software on it :)

---

### Post by pseudonym on 2006-12-30
> **linuxbun said:**
> Yes it is, i'm shredding purely for security incase myhdd gets into the wrong hands and somone tries recover software on it :)
Well, if you're still going to be using the drive, this probably won't help you, but I'll mention it anyway. There are tools like dban and wipe, among others, which completely erase a hard drive to the point where data would only be recoverable by the sort of people who have access to the most top-secret equipment. Even then, they are still unlikely to recover much that is useable. The average Joe with an undelete tool, wouldn't be able to do anything at all.

if this is the kind of thing you're looking for, then you can download and burn the [System Rescue CD]("http://www.sysresccd.org/Main_Page"), which contains these tools and many others which are useful. In fact, i highly recommend this CD to everybody. Just boot up the CD, and pick your task. I use it to back up my system using partimage, and I wiped a couple hard drives before ebaying them.

HTH :)

---

### Post by linuxbun on 2006-12-30
> **pseudonym said:**
> Well, if you're still going to be using the drive, this probably won't help you, but I'll mention it anyway. There are tools like dban and wipe, among others, which completely erase a hard drive to the point where data would only be recoverable by the sort of people who have access to the most top-secret equipment. Even then, they are still unlikely to recover much that is useable. The average Joe with an undelete tool, wouldn't be able to do anything at all.

if this is the kind of thing you're looking for, then you can download and burn the [System Rescue CD]("http://www.sysresccd.org/Main_Page"), which contains these tools and many others which are useful. In fact, i highly recommend this CD to everybody. Just boot up the CD, and pick your task. I use it to back up my system using partimage, and I wiped a couple hard drives before ebaying them.

HTH :)

No use to me immediately, however that is very handy to know. I have been looking for something like this for a very long time. Got the link bookmarked, ta for sharing it :D :D :D :D

---

