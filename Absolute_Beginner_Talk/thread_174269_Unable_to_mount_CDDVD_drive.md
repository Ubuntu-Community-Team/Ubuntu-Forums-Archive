---
title: "Unable to mount CD/DVD drive"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by gomezj00 on 2006-05-11
Hi and thanks for trying to help me.
Question.  How do I get the Ubuntu File Browser to mount my cd/dvd drive.  I can mount it manually by using a term and the mount command and then navigating to the /media/cdrom mount point.  But when I mount it via the File Browser I get the message "Unable to mount the selected volume".  Any suggestions?  Thanks!

---

### Post by macdo on 2006-05-11
Please don't repost the same question 3 times. Someone who knows the answer  will eventually get round to you, and reposting doesn't help: it just annoys people...

As for your question: Post the contents of "/etc/fstab", please.

---

### Post by gomezj00 on 2006-05-11
[QUOTE=macdo]Please don't repost the same question 3 times. Someone who knows the answer  will eventually get round to you, and reposting doesn't help: it just annoys people...

As for your question: Post the contents of "/etc/fstab", please.[/QUOTE]

Hi!  I know and didn't actually mean to repost the question three times.  The site kept giving me an error message saying that my post was invalid due to an invalid forum.  I didn't know it was posting my messages despite the error.  I've been sitting here for the last half hour trying to delete my posts and I can't find how to do it.  Anyway, sorry for the reposts.

---

### Post by macdo on 2006-05-11
Oh, fair enough! I don't know where one can file a **forum** bug though :-)

Moving on, /ect/fstab?

---

### Post by gomezj00 on 2006-05-11
[QUOTE=macdo]Oh, fair enough! I don't know where one can file a **forum** bug though :-)

Moving on, /ect/fstab?[/QUOTE]


The contents are:
<filesystem> <mount point>   <type>   <options>    <dump>  <pass>
proc     /proc     proc     defaults     0     0 
/dev/hda4     /     ext2     defaults, errors=remount -ro 0
/dev/hda2     /media/hda2     ntfs defaults      0     0
/dev/hda3     none     swap     sw     0     0
/dev/hdb     /media/cdrom0     udf,iso9660 user,noauto      0     0

I had to type this stuff in since my laptop is not on the web right now so I hope I didn't make any mistakes.  Once again thanks for your help!

---

### Post by macdo on 2006-05-11
Well, that looks OK...
Go to Systems>administration>Users and Groups, then choose your username, Properties, User Privileges, and check that 'Use CD-ROM drives' is checked.

---

