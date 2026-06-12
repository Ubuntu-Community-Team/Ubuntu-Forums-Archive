---
title: "dvd+rw - delete or over-write file??"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-07-25
To backup my home directory I create a tar file and write it to a dvd+rw media. Works fine the first time. Now I want to refresh my backup - create an updated tar file and over-write the old tar file on the dvd. But I cannot over-write or delete the copy on dvd. 

If this cannot be done, then why did I spend the extra money for dvd+rw media?? Very basic question I realize, but I cannot seem to find the answer. Rather than experiment with permissions on /dev/cdrom, /etc/fstab entries ... and maybe cause problems, thought I would ask here first. Thanks for suggestions.  -- Bob

---

### Post by Malta paul on 2007-07-25
Hi,
I would say you problem is that when you burned the disk  your 'Burner Program' was not set to 'multi session'  
You could try K3B or Gnomebaker which have more setting features than the default Nautilus burner. 
I presume you are using Ubuntu. Go to >Applications > Add/remove > Search DVD burner
Hope this is of some help :wink:

---

### Post by Orochi on 2007-07-25
You can't just delete or overwrite the files on a RW disc, you need to wipe the whole thing and then reburn. I've never done it in Linux, but on Windows and OSX most burning programs have an option to wipe RW discs. You'll probably need an actual burning program like gnomebaker or k3b instead of the built-in Nautilus burner.

Multi-session is different, it allows you to add extra data to the end of a burnt CD (not overwrite or delete) and it works with R's and RW's.

---

