---
title: "I loss my mp3 files !!"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Me! on 2008-01-06
Helo all
:confused:

I organzed my data with Amarok , evry thing was nice

after reorgnaizing with other directory the old directories were not removed , so I maked sure that is not mp3 files on it then delete it

all thing is nice ,but after the restart I can not find some mp3 files ??

I can not recover my data in ext3 !!

I can reget , reorganize , re... but is my data is safe in ext3 !
or can somebody tell me what hapen !
:confused:

thanks all

---

### Post by SOULRiDER on 2008-01-06
Is that directory gone or does it not appear in amarok? Try searching for one of those 'lost' files using the search tool. Go to Places and then Search for files.

---

### Post by Me! on 2008-01-06
> **SOULRiDER said:**
> Is that directory gone or does it not appear in amarok? Try searching for one of those 'lost' files using the search tool. Go to Places and then Search for files.

The files is not in its directory
and not in other directory

directory is still but files not included (was included before restart -That what I think)

I used search tools in my home & in / , but did not find the file

I hope to know what hapen ? how my files deleted ? is this bug in hard links or other bug ??

I made sure that no files in directories before deleting ( by amarok it self drag dir to it , no sound files in them )

thank you

---

### Post by nowshining on 2008-01-06
do u still have the mp3s on ur hardisk? if not, u should of put them in a safe place, if not, have u tried the trash folder to see if they went into there?

---

### Post by Me! on 2008-01-06
Not in Trashs (of gnome or kde)
Not in Trashs (of root or users)

:(

---

### Post by Me! on 2008-01-06
I am searching with:
```
sudo find / -name "*&#1602;&#1604;&#1576; &#1575;&#1604;&#1605;&#1582;&#1578;&#1575;&#1585;*"
```

I am waiting this search

---

### Post by Me! on 2008-01-06
My problem is with reorganizing thos files , I retag them !

from Windows encoding ( cp-1256 to utf8 ) , adding good tags for title, artist, album, genure , year , .. for each file of more than 300 files

Amarok is nice for tag fill for directories , but still needed human editings (re-editing :( )

---

### Post by Me! on 2008-01-06
I organized more than 600 files but more than 300 was lost with unkown problem !

---

### Post by nowshining on 2008-01-07
u could of also used

locate name.extension

to update the locate database manually type

sudo updatedb

:)

---

### Post by Me! on 2008-01-07
> **Me! said:**
> I am searching with:
```
sudo find / -name "*&#1602;&#1604;&#1576; &#1575;&#1604;&#1605;&#1582;&#1578;&#1575;&#1585;*"
```

I am waiting this search

not find any thing

---

### Post by Me! on 2008-01-08
can somebody tele me :

If I have 2 harde links to one file , And I delete on of them , is this file will be deleting ? or still to use by other hard link ?

thanks all

---

### Post by peabody on 2008-01-08
No, if you only delete one of the hard links, the file will not be deleted.  Symbolic links, however, are another story.

---

### Post by Me! on 2008-01-08
> **peabody said:**
> No, if you only delete one of the hard links, the file will not be deleted.  Symbolic links, however, are another story.

Thank you 

but I still want to know How did my files deleted ??? :confused:

I don't want to do same stupid action !
:(

---

### Post by spiderbatdad on 2008-01-08
the mistake was in not having data backed up. the HD is not a safe place to store data.

---

### Post by nowshining on 2008-01-08
> **spiderbatdad said:**
> the mistake was in not having data backed up. the HD is not a safe place to store data.
do sudo updatedb

enter ur pw and let it run and try locating again.

---

### Post by Me! on 2008-01-12
> **nowshining said:**
> do sudo updatedb

enter ur pw and let it run and try locating again.

I use:
```
sudo updatdb
sudo locate "*&#1602;&#1604;&#1576; &#1575;&#1604;&#1605;&#1582;&#1578;&#1575;&#1585;*"
```

It can not found them !! 
:(

I think thay deleted some how :confused: I want to know what happen to save my data

thank you

---

