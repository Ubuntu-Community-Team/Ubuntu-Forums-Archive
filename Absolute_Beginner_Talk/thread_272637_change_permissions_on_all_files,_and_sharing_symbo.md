---
title: "change permissions on all files, and sharing symbolic links?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by yellowband on 2006-10-06
Hi guys

i have two problems that are causing me grief on my home network. 

1. i have folders within folders, and files in subfolders that all have strict permissions on them that i want to remove. I want to know how to, given a folder, change the permissions on all subfolders and files at once.  Right now i have to go to the deepoest location and change the files one by one.  

2. I have a server sharing my media across the network, and right now i'm sharing a bunch of folders. I was wondering if i could just make a folder, and put symbolic links to all of the folders/files i want to share, and then just share that one main folder? would that work? can symbolic links be shared?

thanks.

---

### Post by aysiu on 2006-10-06
Please be careful.

Too many times I've seen new users want to change permissions on all their folders only to find that breaks their system, and they can't even log in any more.

What is the folder you're trying to change permissions on?

In all likelihood, there's a much better way to approach this. Read these three links:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by yellowband on 2006-10-06
hi aysiu

thanks for the caution, and i agree, i don't want to tamper with any system files.

basically i have a folder called media and in it looks something like:

media
--mp3
----artists
------a
------b
------c
--------file1
--------file2
--------etc...
--pics
--video
----movies.

When i change the permissions on "mp3" folder, i can write to it remotely, but i can't write to any files within it (say artists). Then when i change "artists" permissions, i can't write to any folders in that.  Finally, i can't delete any songs in the lettered folders because they are write-protected. I want to have everything in my media folder write-enable by any user, so i can manage my media remotely.  

how do i do this without changing the permissions on each file individually?

thanks.

---

### Post by aysiu on 2006-10-06
Have you tried this? ```
sudo chown -R yellowband:yellowband ~/media
``` This assumes your username is *yellowband* and that the media folder is in /home/yellowband/media

---

### Post by yellowband on 2006-10-07
cool thanks for the help.

one more question though. i was aware of the -R option (recursive) but isn't this going to go the oposite way?  i thought recursive meant if i ran this command on a file, it would change the permissions on all parent folders, not the other way around (children folders) like i want.  I'll give this a try anyways, as now that i think about it, my logic doesn't make sense. If what i though happened, the entire computer would have it's permissions changed, as the root folder is parent to all other folders (i'm an idiot).

---

### Post by aysiu on 2006-10-07
-R means it will change ownership to all the *child* folders, not the parent ones.

---

