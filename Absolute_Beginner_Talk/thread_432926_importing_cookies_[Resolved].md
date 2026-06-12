---
title: "importing cookies [Resolved]"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-04
I have a few critical cookies I need to get from W2K.  I drag and dropped the W2K version onto the fiesty desktop then backed up the original cookie.txt in ~/.mozilla/firefox/xxxdefault and plunked the new file, replacing the old cookies.txt.

When I open the bookmark the data is not there.  In the preferences/privacy/showcookies window, my cookies are not there.

Any ideas?

Thanks,
bobland

---

### Post by aysiu on 2007-05-04
You can just replace the entire /home/bob/.mozilla folder with C:\Documents and Settings\bob\Application Data\Firefox

---

### Post by BobLand on 2007-05-04
The structure seems a bit different with different folders.  Would that make any difference?  To bring my bookmarks in I had to cut & paste and do a bit of editing but they work.

Since the cookies.txt in windows is the same in fiesty, why won't it read?

Thanks,
bobland

---

### Post by aysiu on 2007-05-04
I've successfully moved entire Firefox profiles from Windows XP to Ubuntu a couple of times. If you do run into problems, you can edit the ~/.mozilla/firefox/profiles.ini file to reflect the difference in profile location.

---

### Post by BobLand on 2007-05-04
I copied the entire w2k firefox directory over.  I gave me a clean slate.  No bookmarks, no cookies.

bobland

---

### Post by aysiu on 2007-05-04
Have you tried editing the profiles.ini file to reflect the new location of the profile?

---

### Post by BobLand on 2007-05-04
My browser is messed up.  It is not displaying correctly.  The profile.ini is pointing to a location but I'm no longer sure what's what and where's where.

At this point, I'd like to start over.  Can you give me suggestions on reinstalling firefox?

Thanks,
bobland

---

### Post by aysiu on 2007-05-04
You don't need to reinstall Firefox. Just close Firefox and then remove the profile by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/firefox): ```
mv ~/.mozilla ~/.mozilla.backup
```

---

### Post by BobLand on 2007-05-04
When I view other sites they look normal.  When I view this site it does not look normal.  Since I reinstalled firefox it probably overwrote all of the default plugins or whatever.

Is there a command to run to get firefox to get all of the ubuntu plugins?

Thanks,
bobland

---

### Post by BobLand on 2007-05-04
There were multiple instances of bookmarks and cookies.  Once I found the correct versions in w2k and the correct home in fiesty, everything worked just fine.

I'm liking fiesty more and more.  I'd like to get my old mail but its probably not that important.  Looks like the only reason to boot windows it for Half-Life2: episode 2.

Many thanks to this community for all the information given so freely.
bobland

---

