---
title: "Installed dvd player"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by MarkCrider on 2006-09-21
I recently removed my cdrom player and installed a dvd player in my IBM laptop.  I am trying to configure it.  Umbutu see's the drive but still labels it a cdrom.  I also have a cdrom and a cdrom-1 listed.  I only have 1 cdrom.  When I do updates and need to use disk to install software, I can not direct updates to the cdrom. 
IBM 600x, 550cpu, 4 gig hard drive, 192 ram.

---

### Post by davmac on 2006-09-22
Mark,

Both my laptops (Asus S6F and Dell Inspiron 510m) have DVD writers in them and both show up as /media/cdrom and both work perfectly.

If you put a DVD in the drive can you read it?

I'm not sure what you mean by "I can not direct updates to the cdrom". Can you explain in a bit more detail about what you're trying to achieve?

Dave Mac

---

### Post by 3rdalbum on 2006-09-22
I think what he means is: When he's trying to install a package that's on the Ubuntu disc, and it asks him to insert the disc, it doesn't recognise it.

Try this:

```
gksudo nautilus
```

Go into the /media directory, where you've got "cdrom" and "cdrom-1". Put a disc into your drive and find out which of those directories holds the contents of the disc.

Delete the one which DOESN'T hold the contents of your disc - I'll assume it will be "cdrom". Middle-drag the remaining folder icon (cdrom-1) to the same directory that it's in; i.e. middle-drag /media/cdrom-1 to /media. From the popup menu that appears, click "Link here".

Now change the name of the link from "Link to cdrom-1" to "cdrom".

Try that and see how it goes.

---

### Post by MarkCrider on 2006-09-23
I have tried to delete the cdrom that is not being used.  I think updates is looking at the wrong cdrom drive.

---

### Post by davmac on 2006-09-27
Mark,

Could you open up a terminal and type "cat /etc/apt/sources.list" and paste the output back here?

If you also "cd /media" followed by "ls -la" and paste the output back into the thread that might give some clue to your problem.

Dave Mac

---

