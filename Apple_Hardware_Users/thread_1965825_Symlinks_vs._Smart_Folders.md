---
title: "Symlinks vs. Smart Folders"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by krisb82 on 2012-04-26
The marketing and design director in my company has asked me to look into a solution to a problem he has encountered. I'm hoping that the Ubuntu Community will have an answer for me.

The problem has to do with directory layouts and options for Mac users accessing a Samba share on a Ubuntu file server I recently built for them (10.04 x64). The users store all of their artwork files based on the brand and release date the files relate to. The marketing director would also like to keep a separate folder structure that includes/references all like products across the various releases, akin to Smart Folders on a Mac.

For example, one product we design would be patterned scrapbooking paper. We have a paper folder under each new product line release (2 releases a year) folder. So, if a user is looking for a particular past paper's artwork they would need to remember or search through all the different release folders until they found it. We'd like to have a way where they could open a top-level folder called "Paper" that would bring in all of the different paper artworks from across all of the various releases.

I'm sure there is a way to do this, but I have no clue how to do so. I'm still very much a Linux novice, but learning new things everyday and loving what I'm learning!

Thanks in advance for any help on this. Feel free to bump me to a different thread if more appropriate.

---

### Post by lykwydchykyn on 2012-04-26
This is typically functionality that would be in the file browser; for example, in KDE dolphin will let you find files of a certain type or matching a certain expression.

Still, it's an interesting idea; maybe there is a samba VFS module out there that does this.

If the data doesn't change much in real time, the hackish way to do this would be to use a find command in a cron job to generate symlinks.  For example, if your samba root is /srv/smb and you want a folder containing all the jpegs:

```

find /srv/smb -iname "*.jpg" -exec ln -s {} /srv/smb/jpegs/ \;

```

Of course, you'd run into problems if there were jpeg files in different folders with the same name, you'd have to have some way to deal with that.  Just a rough idea, maybe it can be developed into a working solution.

---

