---
title: "Deleting a shortcut to an NTFS directory"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by deldredge on 2006-06-04
Ok, so I mounted my NTFS windows HD in ubuntu so I could get access to some of my document files, before I moved them over to a new FAT partition.

I made a shortcut to the "My Documents" folder of my windows drive on the ubuntu desktop, Then in screwing around I accidentally made a link to that shortcut. 

I want to delete the link that I made by mistake, but it won't let me. When I try to just hit delete it doesn't do anything. When I look at the permissions, it only gives read and execute permissions, and it's owned by root so I can't change them.

When I open the desktop folder in root, the permissions aren't greyed out, but when I try to change them it tells me I can't change them because the file is on a read-only partition.

Is it trying to change the partitions of the actual folder or just the link?

All I want to do is delete the link file on my desktop! help!

---

### Post by dvarsam on 2006-06-04
To add the "write" permissions:

1. Open a Terminal

2. Perform a "sudo -i"

3. Log-in as "root" user

4. Move to the Desktop directory

5. Perform a "chmod 777 your_shortcut"

And then you could move to trash...

Or:

Perform a "rm your_filename"

Or:

How about if you boot to "Safe Mode" & then Delete...

Just a few suggestions...

Good Luck!

---

### Post by deldredge on 2006-06-04
Thank You!

It worked :)

---

