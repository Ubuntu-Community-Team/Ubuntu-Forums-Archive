---
title: "[SOLVED] Can I view all chat log of one single day in pidgin?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-04-13
Hi
Thank you for reading my post
Is there any way to export all chat logs of an specific day in pidgin?
for example I want to see today chats that I had with different people. is there any way to do it ?
I dont want to check each person logs individually as  it is time consuming.

Thanks.

---

### Post by elmer_42 on 2008-04-13
```
cat [log1].txt && cat [log2].txt && cat [log3].txt
```
Run that, it will display all the logs you put in the command. If you add more && cat [log].txt, it can display more files. It doesn't matter what extension they are as long as it is plain text.

---

### Post by legolas_w on 2008-04-13
Hi
Thank you for the reply
But I do not know where does pidgin store its log files, I tried ~/.pidgin and no folder with that name is in the home folder.

Thanks.

---

### Post by Freddie.Ruddick on 2008-04-13
The logs are stored in ~/.purple/logs/**TYPE OF IM ACCOUNT**/**SCREENNAME**.

Each chat has its own html file, in folders by screenname of who they're with.

The reason for the folder being called .purple is that the Pidgin team have divided Pidgin into 2 products; Purple, which provides the backend that actually talks to the IM providers; and Pidgin, which handles the frontend prettyness. (There's also Finch, a terminal based client that uses the Purple backend)

HTH

:)

---

### Post by legolas_w on 2008-04-15
Thanks, to complete the solution for other people.
You should sort your all folders (which represent your chat friends IDs) by date and see the content of each folder that meet your date criteria.

---

