---
title: "Where are the FF Bookmarks stored?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-29
Hi
I want to save my FireFox Bookmarks prior to wiping the drive and re-installing Ubuntu.
However, I can't find where they are.
I can locate two bookmarks.html files (one in each of /etc/firefox/profile and /etc/mozilla-firefox/profile) but NEITHER of these contains the bookmarks I have created. The information in them refers to the FF, Mozilla and Ubuntu links only.

Anybody know where I should be looking?

Thanks
Paul

---

### Post by Swab on 2006-07-29
Just go into Bookmarks > Manage Bookmarks > File > Export

---

### Post by Lord Illidan on 2006-07-29
Go to your ~/.mozilla/firefox/ directory.

Then you will see a folder beginning with a random set of letters and numbers, ending with .default.

Open the folder, and you will see the bookmarks.html file in all its glory!

---

### Post by confused57 on 2006-07-29
Here's a good how to restore FF bookmarks, if upgrading FF with Automatix(Breezy):
[http://ubuntuforums.org/showpost.php?p=681904&postcount=1545](http://ubuntuforums.org/showpost.php?p=681904&postcount=1545)

---

### Post by PaulFXH on 2006-07-29
Hi
Thanks to everybody for the quick replies.
Unfortunately, I still don't get it.

Here's where I slipped up:

1) The first post suggests Bookmarks>Manage Bookmarks>File>Export.
So far, so good but I want to export this file to a CD and the CD RW drive does not show up in the GnomeBaker dialog box. Why not? I really have no idea as I have already used it with success to do a similar burn today.

2) The second and third replies refer to a folder the first part of which is ~/.mozilla/firefox/
I have searched every available location on my computer for this and cannot put my finger (or anything else) on it.
In particular, could somebody please explain what is "~/."

Thanks
Paul

---

### Post by Swab on 2006-07-29
> **PaulFXH said:**
> Hi
Thanks to everybody for the quick replies.
Unfortunately, I still don't get it.

Here's where I slipped up:

1) The first post suggests Bookmarks>Manage Bookmarks>File>Export.
So far, so good but I want to export this file to a CD and the CD RW drive does not show up in the GnomeBaker dialog box. Why not? I really have no idea as I have already used it with success to do a similar burn today.

2) The second and third replies refer to a folder the first part of which is ~/.mozilla/firefox/
I have searched every available location on my computer for this and cannot put my finger (or anything else) on it.
In particular, could somebody please explain what is "~/."

Thanks
Paul

1) I don't know about gnomebaker, you could just burn the CD with nautilus.

2) ~/ is a shortcut to your home directory, equivelant to /home/username/

---

### Post by PaulFXH on 2006-07-29
Thanks for the reply Swab
OK, I looked in /home/paul for anything called .mozilla (i.e. with a DOT before the word Mozilla) and there is nothing at all like that present.
Is the DOT another abbreviation of which I should be aware?
Alternatively, or there some hidden files or something involved here?

Thanks
Paul

---

### Post by scxtt on 2006-07-29
if you do it through nautilus, you'll have to enable "show hidden files" first ... should be in the "View" menu ... but you're looking for this:

```
scxtt@madiera.ubuntu [~/.mozilla/firefox/e4o51nl4.default]
:> pwd
/home/scxtt/.mozilla/firefox/e4o51nl4.default

scxtt@madiera.ubuntu [~/.mozilla/firefox/e4o51nl4.default]
:> ll
total 1.2M
drwx------ 2 scxtt scxtt 4.0K 2006-07-29 04:50 bookmarkbackups
drwxr-xr-x 2 scxtt scxtt 4.0K 2006-07-29 14:30 Cache
drwxr-xr-x 2 scxtt scxtt 4.0K 2006-07-28 05:17 chrome
drwxr-xr-x 2 scxtt scxtt 4.0K 2006-07-28 05:17 extensions
-rw-r--r-- 1 scxtt scxtt 9.9K 2006-07-29 18:05 bookmarks.bak
-rw-r--r-- 1 scxtt scxtt  204 2006-07-28 06:14 extensions.cache
-rw-r--r-- 1 scxtt scxtt 120K 2006-07-28 06:14 compreg.dat
-rw-r--r-- 1 scxtt scxtt  987 2006-07-29 17:11 formhistory.dat
-rw-r--r-- 1 scxtt scxtt  55K 2006-07-29 18:05 history.dat
-rw-r--r-- 1 scxtt scxtt  89K 2006-07-28 06:14 xpti.dat
-rw------- 1 scxtt scxtt  64K 2006-07-29 18:05 cert8.db
-rw------- 1 scxtt scxtt  16K 2006-07-29 18:05 key3.db
-rw------- 1 scxtt scxtt  16K 2006-07-28 05:17 secmod.db
[color=red]-rw-r--r-- 1 scxtt scxtt 9.9K 2006-07-29 18:05 bookmarks.html[/color]
-rw------- 1 scxtt scxtt  124 2006-07-28 06:14 compatibility.ini
-rw-r--r-- 1 scxtt scxtt  184 2006-07-28 06:14 extensions.ini
-rw-r--r-- 1 scxtt scxtt 1.1K 2006-07-29 18:05 prefs.js
-rw-r--r-- 1 scxtt scxtt 772K 2006-07-29 18:05 XUL.mfasl
-rw-r--r-- 1 scxtt scxtt  206 2006-07-28 05:24 downloads.rdf
-rw-r--r-- 1 scxtt scxtt 2.0K 2006-07-28 06:14 extensions.rdf
-rw-r--r-- 1 scxtt scxtt 2.3K 2006-07-29 18:05 localstore.rdf
-rw-r--r-- 1 scxtt scxtt  287 2006-07-28 05:17 mimeTypes.rdf
-rw-r--r-- 1 scxtt scxtt  752 2006-07-28 05:17 search.rdf
-rw------- 1 scxtt scxtt 8.5K 2006-07-29 14:30 cookies.txt
-rw------- 1 scxtt scxtt  434 2006-07-29 04:51 signons.txt
```

---

### Post by Swab on 2006-07-29
> **PaulFXH said:**
> Thanks for the reply Swab
OK, I looked in /home/paul for anything called .mozilla (i.e. with a DOT before the word Mozilla) and there is nothing at all like that present.
Is the DOT another abbreviation of which I should be aware?
Alternatively, or there some hidden files or something involved here?

Thanks
Paul

Yup, files starting with a dot are hidden files.  As suggested you can choose to view hidden files in nautilus.  If you are using the command line you can use "ls -a" to display all files including hidden files.

---

### Post by FusionXN1 on 2006-07-29
Open firefox goto bookmarks -> manage bookmarks -> File -> Export -> save bookmarks.html

Make sure you dont lose the file and after the format do..

bookmarks -> manage bookmarks -> File -> Import -> open bookmarks.html

I always do it. Hope this helps.

---

### Post by GStubbs43 on 2006-07-29
Hey, I just wanted to make a note that it is Firefox, not FireFox and it is Fx or fx, not FF... I see this a lot and it bugs me. ;)

Anyway. Go to Places>Home Press ctrl+h open .Mozilla>Firefox>(random numbers/letters>Bookmarks.html

[http://www.mozilla.org/support/firefox/faq#spell-abbreviate](http://www.mozilla.org/support/firefox/faq#spell-abbreviate)
[http://www.mozilla.org/support/firefox/faq#profiles](http://www.mozilla.org/support/firefox/faq#profiles)

---

### Post by PaulFXH on 2006-07-29
Thanks to everybody for the replies. I learnt a lot from these (principally that I have an awful lot to learn about Linux).

Anyway, I've solved the problem.
The suggestion of FusionXN1  was useful in that I just saved the bookmarks.html file to the desktop (rather than trying to get it directly onto a CD) and burned it to CD from there. No need to worry about hidden files in that case.

Best wishes
Paul

---

### Post by catlett on 2006-07-29
nevermind

---

### Post by karloscarweber1 on 2007-10-29
I have a similar problem. I need to copy the bookmarks from the old firefox install and bring it to a new one.  But I have a problem.  I need to access a restricted file.

I upgraded to Gutsy from feisty, my old video drivers apparently weren't provided in the new update.  Now I am using the original live CD to backup my files. but now I need those bookmarks and access is denied.

how do I get them?

---

