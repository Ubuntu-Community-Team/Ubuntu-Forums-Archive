---
title: "File permissions and security"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by dasyad on 2006-09-11
I noticed that in my home folder the permissions for files has "Others:Read" ticked and im abit of a novice at file permissions so does this mean anyone can read my files?

I also noticed that when i click file system all the folders their have "Others:Read" ticked and some even have execute and write ticked so i was wondering is this a bad thing?

---

### Post by fatsheep on 2006-09-11
"Others" is reffering to other users and services on your computer I believe.  It's not like any random person on the internet can read and execute your files...

---

### Post by dasyad on 2006-09-11
Cool thanks :)

---

### Post by John.Michael.Kane on 2006-09-11
This should offer some help.

[Securing a fresh Linux install, part 2]("http://www.linux.com/article.pl?sid=04/04/15/1918219")

[Editing Files that Belong to Root]("http://www.psychocats.net/ubuntu/permissions")

[Understanding Linux file permissions]("http://www.freeos.com/articles/3127/")

---

### Post by Jussi Kukkonen on 2006-09-11
> does this mean anyone can read my files?
Yes, anyone with an account. If you want to change permissions of existing files, it's not hard even for your whole home dir: ```
chmod -R o-r ~
``` will do that.

Like you found out, the default new file permissions are 022: read/write for you, read for everyone else. *umask* can change that, but I have no idea where you should run it to get it applied to your x session...

> 
I also noticed that when i click file system all the folders their have "Others:Read" ticked and some even have execute and write ticked so i was wondering is this a bad thing?
Most files are readable to all, but sensitive ones are not (try /etc/sudoers). the execute flags you saw were probably for directories -- that's normal. Write shouldn't be allowed except in special cases, like /tmp/.

---

### Post by dasyad on 2006-09-11
Fantastic help guys thank you all for your input :)

---

