---
title: "How to set standard chmod for uploads in Gftp?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-04-10
Hi,

When I upload something with Gftp to my website the standard chmod of the new (or replaced) file is always 770. How can I set this to something different? It's really annoying that when I update a file it suddenly gives an error because I need to update the chmod immediately after I uploaded it..

Does anybody know how to solve this?

---

### Post by Compyx on 2007-04-10
Under FTP->Options, there's a checkbox 'Preserve file permissions', maybe that'll solve your problem.

---

### Post by kramer65 on 2007-04-10
That is already set to 'Preserve file permissions'. So that actually doesn't solve it. (thanks anyway.. :-)) 
All the files come from a fat32 filesystem (which I have shared among windows and linux..). Wasn't it that fat32 doesn't have rights at all? 

Don't know if that has anything to do with it?

---

### Post by Compyx on 2007-04-10
It does, file permission translate poorly from Windows/Dos to Unix, they usually end up with execute permissions on Unix. You would be better of copying the files to your ext3/reiserfs partition and doing a 'chmod -x' on them there, and then transferring them via gFTP.

Sorry I can't be of more help, but I never use anything Microsoft-related.

---

### Post by kramer65 on 2007-04-10
ok. Well, at least now I know whats the problem...

Makes it easier to handle as well..

Thanks!

ps. I hope I'll be only using non-microsoft in a while as well. But don't blame me.. I'm still dependent on some microsoft things..

---

