---
title: "complex characters in ubuntu"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-05-14
i have problem with central-european complex characters in ubuntu (slovak language).

[IMG]http://shanike.szm.sk/diakritika.png[/IMG]

this ID3tag had been viewed correctly back in windows. it's not just about rhythmbox, problem itself includes gaim/pidgin, subtitles in mplayer etc..to make things more complicated, some applications/files aren't affected (and therefore display these symbols correctly).
i have installed language support for slovak (my native language), czech and english language and checked the "support for complex characters" box, but it didn't help.
link below shows, what is needed to be done in windows so that these special characters can be viewed correctly:
[http://img1.zoznam.sk/icq/img-help/regional-settings.htm](http://img1.zoznam.sk/icq/img-help/regional-settings.htm)

can anyone help? :(

---

### Post by bapoumba on 2007-05-14
may be some issue with UTF-8 ?

---

### Post by hyper_ch on 2007-05-14
Yes, it's a character encoding issue... Ubuntu uses Unicode (UTF-8) and windows uses some other stuff... for me, in German, it was ISO-8559-1 I think... or something like that.

---

### Post by shanike on 2007-05-14
yeah, i could actually fix this in windows by installing support to non-unicode characters... but what am i supposed to do?
it's not such drama to rewrite all the id3tags, but editing all the subtitles would be like.. impossible :(

---

