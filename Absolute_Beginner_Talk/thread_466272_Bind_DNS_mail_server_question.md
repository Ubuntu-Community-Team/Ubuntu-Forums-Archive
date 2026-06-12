---
title: "Bind DNS mail server question"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Nathan_Scott_Grey on 2007-06-06
I am attempting to set up a mail server and have some (i assume) basic questions.

In my attempted install of Zimbra, I keep having an issue. The domain name mail.example.com doesn't show up in Bind or on a DNS query. 

The mail service is currently hosted on another server (a Microsoft Exchange server on another site). 

Is there anything specific I have to do to move the load from server offsite to server onsite? 
How would I update DNS to reflect the new address?
Do I have to move the webserver operations as well?
The smtp server is just example.com - does this have any special requirements in the listing?

Is there any other general things I should know/do before I try to make the migration?

Thanks for the soon to be forthcoming help!

---

### Post by sandwitch on 2007-06-07
Zimbra needs a fgdn with an existing mx on install

---

