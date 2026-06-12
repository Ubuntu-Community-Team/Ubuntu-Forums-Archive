---
title: "DVD Movies not recognized anymore?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Eladon on 2006-10-10
OK, yesterday my system recognized DVD Movies, and today it doesn't.  I seriously can't think of anything profound I have done with my computer in the last 24 hrs.  

When I originally installed Dapper, I used Automatix 2 to get myself set up, and everything was fine.  When I put a DVD in the drive, it would mount and show as an icon on my desktop named appropriately after the name of the DVD Disc.  Now, when I put the disc in, it just pops up a "DVD-ROM Disc" icon which has no contents.

Data discs still work fine (DVD or CD), and the movie discs work fine when I plug them into a Windows box...

I tried uninstalling and reinstalling pretty much everything in the "Multimedia" menu of Automatix (including the AUD-DVD Codecs), but it hasn't fixed the problem.

Any ideas???

---

### Post by Eladon on 2006-10-10
OK, so I had a brainwave, and tried a **data** disc I have that I know was burned **UDF**, and it came up the same "blank" way.  So a search on UDF issues brings up loads of posts:

[http://www.ubuntuforums.org/showthread.php?t=206913&highlight=udf](http://www.ubuntuforums.org/showthread.php?t=206913&highlight=udf)
[http://www.ubuntuforums.org/showthread.php?t=224983&highlight=udf](http://www.ubuntuforums.org/showthread.php?t=224983&highlight=udf)
[http://www.ubuntuforums.org/showthread.php?t=225461&highlight=udf](http://www.ubuntuforums.org/showthread.php?t=225461&highlight=udf)
[http://www.ubuntuforums.org/showthread.php?t=195403&highlight=udf](http://www.ubuntuforums.org/showthread.php?t=195403&highlight=udf)

... and the list goes on.  So it seems I'm not alone.  Only catch is, the workaround doesn't work for me.  The suggestion is to make a change in your /etc/fstab from (in my case):

/dev/hda        /media/cdrom0   **iso9660,udf**    user,noauto     0       0
...to...
/dev/hda        /media/cdrom0   **udf,iso9660**    user,noauto     0       0
...or alternately...
/dev/hda        /media/cdrom0   **auto**           user,noauto     0       0

however, made these changes, rebooted my computer each time, and none of them fixed the problem.

So I tried manually mounting it:
```
mount -t udf /dev/hda /media/cdrom0
```
and presto!  It doesn't mount as a "disc" persay (when I run Totem, the "Play disc..." option is still greyed out), but I can open the "location" (/media/cdrom0), and the movie plays!

So there seems to be a bug in the Nautilus mounting system, since when I open the desktop shortcut it goes to **burn:///** rather than **/media/cdrom0** even after I have properly mounted it.

If anyone has any ideas on how a person can get this working again, it would be much appreciated!  Or even some instructions on how to make the manual mount appear as a DVD disc to software would be better than nothing!

---

### Post by Eladon on 2006-10-10
Wholly cow, 19 hrs later my post is on page 13!  This is a busy forum!
Not so busy for me though.  :( 

Did I perhaps post this in the wrong forum?  Is there any way to move posts?

---

### Post by TheMono on 2006-10-11
You'd have to ask a mod to move it for you... I'm mostly posting this to give the thread a bump for you because I don't know either lol.

---

### Post by gargoyle on 2006-10-12
It seem like a few people are have problems with burnt dvd.
I have a post going on it
[http://www.ubuntuforums.org/showthread.php?p=1603189#post1603189]("http://www.ubuntuforums.org/showthread.php?p=1603189#post1603189")

Yes it seem to be a problem with the reading of UDF disk.
However it gets stranger.
I made a test disk and it worked.
I looked at it properties under windows and it was listed as a UDF.
I looked at other burnt disks that will not play in Ubuntu and it was also listed as UDF.
Also Nautilus will not even recognized the disk.
Like you I have tried modifying the fstab, I have had no success their.

I really wish I could figure out this damn problem.
It seem like some people can play burnt dvds and others can not. But their does not seem to be any common reason why one can and the other can not.

To me this is a problem that is big enough not to use Ubuntu.

---

