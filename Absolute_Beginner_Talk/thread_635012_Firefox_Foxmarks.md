---
title: "Firefox Foxmarks"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by TouchuvGrey on 2007-12-08
I have Firefox on all my computers including my linux machine.
i installed foxmarks on the linux computer to avoid having to redo
all my bookmarks. I click on "synchronize now" see "overwrite local
 with server" click ok, see "downloading now" and yet nothing further
happens.

---

### Post by gn2 on 2007-12-08
Tools>Add-ons>Foxmarks>Preferences>Other> click "reset advanced server settings", then re-run the set-up wizard.

---

### Post by TouchuvGrey on 2007-12-08
No luck there, even after a reboot. Any other suggestions ?



                                                                   Mike

---

### Post by m9ke on 2007-12-08
I haven't used the Synchronize now feature in Foxmarks.  If this doesn't work out for you here is some info.

If you open Foxmarks you will see a tab called "Other".  There you will see a "Maintenance" area where you can either upload or download book marks.

My method requires a bit of discipline but it's worked for me perfectly for a long time, keeping two Windows  XP boxes and one Ubuntu box in synch.  The discipline comes in because you *must* think of and use one box as the master and the other(s) as slaves if you want to keep all in synch in an orderly manner.

The software doesn't require or support Master/Slave, it's just something you have to do if you want to keep things consistent.

I designate one box as Master (again just in my mind not in Foxmarks) and always upload my book marks to Foxmarks servers as they change.  Then I download that set of bookmarks to the other two boxes.

This is kinda clunky but it works for me.  Foxmarks has never let me down, and I use this software when ever my bookmarks change which is often.

Cheers,
m9ke

---

### Post by m9ke on 2007-12-08
On re-reading your post it looks like you might be having trouble connecting to the Foxmarks sever.

Foxmarks is very open with the customers when they have issues.  It appears they had one with the 2.x release.  You can go to their mainweb page, or to their blog.

One entry that might help you is here
[http://blog.foxmarks.com/?p=97](http://blog.foxmarks.com/?p=97)

---

### Post by crimesaucer on 2007-12-08
You might already know about this... and I'm not really sure what Foxmarks does since I've never used it...


... but I always find it very easy to just use the "import" feature in the Firefox Bookmarks Manager.

In Firefox 2 it was the "Organize Bookmarks" option in the Bookmarks drop down menu.

In Firefox 3 it is the "Show All Bookmarks" option in the Bookmarks drop down menu.


All you have to do is find the "Import and Backup" option, click it an pick "Import"... then it asks you "Import  From File"... so yes, Next... then choose your bookmarks.bak file from your profile, or for your most recent file, look in your profile's ~/.mozilla/firefox/qwe4rty8.default/bookmarkbackups/ folder for your most recent html file, mine is:

"**[COLOR="Red"]bookmarks-2007-12-08.html[/COLOR]**".... then import the one you choose.


If you have different computers, just burn it to disk, and import the file from a disk.

---

### Post by TouchuvGrey on 2007-12-08
> **m9ke said:**
> On re-reading your post it looks like you might be having trouble connecting to the Foxmarks sever.

Foxmarks is very open with the customers when they have issues.  It appears they had one with the 2.x release.  You can go to their mainweb page, or to their blog.

One entry that might help you is here
[http://blog.foxmarks.com/?p=97](http://blog.foxmarks.com/?p=97)

That did it, i had Foxmarks 2.032 on my Vista ( Main ) box and 1.01
on my linux machine. Upgrading to 2.032 on the linux machine fixed
it.


                                                                             Mike

---

