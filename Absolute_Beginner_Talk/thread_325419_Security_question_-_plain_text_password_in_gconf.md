---
title: "Security question - plain text password in gconf"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by roastbeef on 2006-12-25
This probably will expose my misunderstanding of users on linux, however I noticed this today and wanted to get some clarification.

If I open gconf-editor and browse to apps->Banshee or apps->Rhythmbox I can find a folder 'audioscrobbler' for last.fm information.  In there is the stored username and password that I entered when configuring that information in those applications.  The passwords are kept in plaintext which scared me at first since I don't need su privileges to access gconf-editor.

My first thought on this is that if I kept my audioscrobbler info in these apps then anyone could open up the conf editor and retrieve my password.  This worries me, but one question I had was if the gconf is relative to each user? (I assume so although I'm the only user on my system besides root).  

I suppose my main question here is - should I be concerned?

(First post, have made the switch to ubuntu and loving it so far!).

---

### Post by mykalreborn on 2006-12-25
> (First post, have made the switch to ubuntu and loving it so far!).
your on the right track my friend! ;)

you shouldn't be scared by that because of a couple of reasons:

 - the other passwords, such as root password, user password, mail password etc aren't by any chance that easy to get. they are encrypted in such a way  it's HARD to get them except if you were the one who made them.
 - the audioscrobbler password isn't such an important thing, because one can't really do too much damage to your user-except for deleting it :D. and even so i don't think anyone else can see your password that easily

still it's pretty strange. maybe someone with a little more tech experience will explain this. all-in-all you shouldn't really worry about that.

---

### Post by roastbeef on 2006-12-25
Thanks for the reply mykalreborn.  Very true, but (and this is due to me being lazy) I like to use as few passwords as possible!  So I guess I need to change some passwords then!

---

### Post by mykalreborn on 2006-12-25
oh. i understand. :D i have been using one password for the last few years. but i guess i shouldn't have said that :rolleyes:

---

