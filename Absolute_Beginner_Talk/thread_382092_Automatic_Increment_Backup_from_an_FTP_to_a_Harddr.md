---
title: "Automatic Increment Backup from an FTP to a Harddrive"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-03-11
Just wondering if Ubuntu has any software which can incrementally backup from an FTP to my harddrive every other day?

Regards

Robin

---

### Post by mlissner on 2007-03-11
Let me get this straight...you want to backup your harddrive via FTP every other day?

Yes, Linux can do that, but it's going to take some work on your end.

What you're going to want to do is make a script that does all the FTP work, and then run it as a cron job every other day. The program I'd look at if I were you is called scp, which stands for secure copy. It will use an encrypted technique to move your files to the other computer, but if you need to use FTP, the program is lftp. I just don't think you'll be able to do it without some interaction from you if you do it via FTP as opposed to scp. 

That might give you a good start. Good luck.

---

