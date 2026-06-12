---
title: "Evolution &amp; Exchange Server"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by aeroprof on 2007-05-17
I am a long time Windows XP user and have used Outlook in my office for years.  I have just started learning Ubuntu (Feisty).  Is there a good reference or sticky someone can point me to that will give some step-by-step instructions on how to set up Evolution to run with an exchange server?  Anybody know how well this would work or am I nuts to be thinking about doing this?

Thanks in advance for your help,

Aeroprof

---

### Post by tact on 2007-05-18
Hey there...

I am using fiesty in an otherwise totally windows environment.  Our corporate email is via MS Exchange also and I used to use outlook heavily.

I have been using evolution the past 3 mths or so.  It has a lot of bugs and weirdness but so far has worked for me at least enough to get things done.

I would welcome any pointers to guides or lists or tips and tricks that may help sort out the reliability issues.  (Or pointers to any other software that will connect to an exchange server and give ms-outlook like functionality that is less quirky or buggy!?)

I have evolution connecting to the corporate exchange server via the OWA interface.  I understand this is the only real option to use it with exchange server.

If you need help configuring let me know and I will try and help.

Amongst the quirks...  I find:
1.  Far too frequent "lost connection to back end server" events.   
Getting evolution to actually get back to reconnecting can be frustrating.  Sometimes just clicking the work offline button, then clicking to go back online works.  Sometimes I have to close evolution and restart.  Sometimes I have to open a command prompt and issue a "evolution --force-shutdown" command to kill it and then restart.  Sometimes restarting (via any of the foregoing methods) wont work right away... but if I close/kill evolution, have a coffee and restart after 20 minutes it will connect.

2.  Far too frequently it shows a number of "unread messages" when I have read all in the inbox and it is supposedly "online".   If I fire up firefox and log onto OWA I will then see the unread msgs... on OWA but not in evolution.  So go thru the close/kill options above and restart evolution til it pulls in the new emails.

3.  I find that if there are a lot of emails in any folder the unreliability is much worse.  So I tend to move mails out to other folders so inbox is usually less than 300 emails.

---

### Post by Atomic Dog on 2007-05-18
> **tact said:**
> 
Amongst the quirks...  I find:
1.  Far too frequent "lost connection to back end server" events.   
Getting evolution to actually get back to reconnecting can be frustrating.  Sometimes just clicking the work offline button, then clicking to go back online works.  Sometimes I have to close evolution and restart.  Sometimes I have to open a command prompt and issue a "evolution --force-shutdown" command to kill it and then restart.  Sometimes restarting (via any of the foregoing methods) wont work right away... but if I close/kill evolution, have a coffee and restart after 20 minutes it will connect.

2.  Far too frequently it shows a number of "unread messages" when I have read all in the inbox and it is supposedly "online".   If I fire up firefox and log onto OWA I will then see the unread msgs... on OWA but not in evolution.  So go thru the close/kill options above and restart evolution til it pulls in the new emails.

3.  I find that if there are a lot of emails in any folder the unreliability is much worse.  So I tend to move mails out to other folders so inbox is usually less than 300 emails.

The same gripes I have.  I wish it worked better, but I gave up and just started using web exchange.  I really wish some of the annoyances were cured.

---

### Post by win2456 on 2008-03-25
Has evolution improved for anyone?  After the evolution update, besides graphic enhancements, i have yet to discover any other benefit...

---

