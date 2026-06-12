---
title: "Desktop CD Login Credentials?"
date: 2014-03-19
forum: Apple Hardware Users
---

### Post by bbarton11 on 2014-03-19
Hi all. I made a Desktop CD for 32-bit PowerPC from [this link]("http://cdimage.ubuntu.com/releases/precise/release/").  I'm able to get it to boot but it puts me a a logon screen for which I'm unable to login.  

I've tried all sorts of combinations: username Ubuntu with Ubuntu password, username Ubuntu with no password, my username and password for the account I was logged in as when I made the CD, no username or password.  Just can't seem to find the correct password.  

Can anyone help?  Thanks!

---

### Post by ajgreeny on 2014-03-19
Did you check the .iso file's md5sum to ensure that the image is good?

You should not get a request for username/password when running a live system, so something seems to be wrong with your CD

---

### Post by bbarton11 on 2014-03-19
Yes, I compared the md5sum from the downloaded .iso to the md5sum on the Ubuntu site and they matched.

---

### Post by bbarton11 on 2014-03-19
[COLOR=#000000][FONT=Roboto]Found out what the issue was.  It must've been a faulty .iso file (even though the md5sums matched) or a bad burn.  I re-downloaded and burned again (with the verify burn option) and it works great.[/FONT][/COLOR]

---

