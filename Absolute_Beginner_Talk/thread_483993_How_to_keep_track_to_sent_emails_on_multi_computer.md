---
title: "How to keep track to sent emails on multi computers"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-06-25
Hi,
I have to work on 3 different computers and I use my email on all these computers. I have to use my school email.
 One option is forgetting email client and using web access however the mailbox is really small (100 MB) then it is not enough for me to keep all emails there. I have to download them. 
Currently, I collect all incoming emails one computer using Evolution.I would like to use an email client on all computers (e.g.pine, evolution) however the problem of sent email arises. Each computer will keep sent emails that were sent by that specific computer. I would like to access all sent emails from any computer. 

What is the best way to manage sent mails at different computers. Please let me know how you handle this problem.
Thank you....

---

### Post by eentonig on 2007-06-25
Private mail accounts I forward all to my gmail. 
Gmail is setup to forward to work. At work, If not critical, they get deleted immediatly after reading or discarding.

@Home, I have evolution downloading my mails to my pc.

This way. At home, i have a full blown mail application. At work, I can see the mails that need my attention. And if I'm on the move, I can still access my mails through the gmail web interface.

---

### Post by shearn89 on 2007-06-25
maybe storing the sent emails in a network share (if they're all on the same network)? I think as long as you have all computers set up to use that share as the outbox, then they should all pick up the sent messages (i guess)....

---

### Post by EndPerform on 2007-06-25
This may not work for you, but you asked how we handled it, and here's what I have:

I have two machines.  My desktop, and my laptop.  I use mutt + procmail + getmail for my mail setup.  The mail is processed and pulled into /home/fubar/mail/.  So, I sync up my settings files and my mail directory between both machines using Unison.  So, I now have a mirror image of my mail on both machines.  I just sync up when I go to use the laptop or desktop, and the sent mail comes right with it.

---

