---
title: "Evolution e-mail feature"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-06-23
Is there a feature in Evolution e-mail application that will allow me to just have the SENDING of outgoing mail take place (similar to the feature in Outlook Express) but not have the application retrieve incoming e-mail from the ISP e-mail server ?

If not, how would I go about requesting that this feature be added to the program.  This is NOT a bug but just a feature enhancement request.  Would a request for this be address to the developers of Ubuntu or to Novell ?

Thanks.

---

### Post by bruce89 on 2006-06-23
Not sure why you would want such a feature, but this is the relevent bug - [http://bugzilla.gnome.org/show_bug.cgi?id=212765](http://bugzilla.gnome.org/show_bug.cgi?id=212765)

---

### Post by Scunizi on 2006-06-23
There's a couple of ways to accomplish what you want.  I dual boot w/XP and some of my email addresses I want pulled from windows and ereased off the server and a couple I want to do the same way on Ubuntu.  The first method is probably the easiest and least painfull.  When you set up your email account make sure you check the box that says "leave messages on the server".  You'll actually pull the messages in Ubuntu but they will remian with your ISP to be pulled by another program/operating system.

The other way is to just change the SMTP server address to something "wrong".  You'll get errors that I can't retreive messages, but so what?  You'll still be able to send.  I hope that helps!

---

### Post by bruce89 on 2006-06-23
[QUOTE=Scunizi]The other way is to just change the SMTP server address to something "wrong".  You'll get errors that I can't retreive messages, but so what?  You'll still be able to send.  I hope that helps![/QUOTE]
You mean the POP/IMAP server, SMTP is the sending one.

---

### Post by wpshooter on 2006-06-23
[QUOTE=Scunizi]There's a couple of ways to accomplish what you want.  I dual boot w/XP and some of my email addresses I want pulled from windows and ereased off the server and a couple I want to do the same way on Ubuntu.  The first method is probably the easiest and least painfull.  When you set up your email account make sure you check the box that says "leave messages on the server".  You'll actually pull the messages in Ubuntu but they will remian with your ISP to be pulled by another program/operating system.

The other way is to just change the SMTP server address to something "wrong".  You'll get errors that I can't retreive messages, but so what?  You'll still be able to send.  I hope that helps![/QUOTE]

Yes, your second suggestion is what I used, of course, to accomplish this but it would be nice to have this little feature that is included in Outlook Express.

But I have never understood the leave messages on the server parameter.  Can you give me a brief explanation of this, including how these messages would ever be expunged from the server if they were allow to stay resident there.  Would this be accomplished by resetting this parameter to OFF ?

Thanks.

---

### Post by bruce89 on 2006-06-23
[QUOTE=wpshooter]Yes, your second suggestion is what I used, of course, to accomplish this but it would be nice to have this little feature that is included in Outlook Express.

But I have never understood the leave messages on the server parameter.  Can you give me a brief explanation of this, including how these messages would ever be expunged from the server if they were allow to stay resident there.  Would this be accomplished by resetting this parameter to OFF ?[/QUOTE]
Yes, I leave all my messages on the server, and yes, it does fill up quite a lot.  I delete all the spam with the web access.  There is discussion of having a "Delete from Server" option in Evolution.

---

### Post by wpshooter on 2006-06-23
I don't understand "**I delete all the spam with the web access**".

I am using Verizon DSL and they service my e-mail.

And is discussion on this forum or in help in Evolution program ?

Thanks.

---

### Post by Scunizi on 2006-06-23
I think what he means with delete from server with web access is simply to log into your online email account without using an email program.  You can only do this if your ISP provides what may be commonly known at "webmail" much like yahoo mail, msn mail, hotmail etc.  You actually go to a website that will display your email.  

Delete from server option is currently in Evolution as the default.  To not delete you have to choose "Leave messages on server".

---

### Post by adam.tropics on 2006-06-23
I just set gmail to archive when read, and evolution to not delete off server. There are a few reasons to do this, but mainly for me, it matters not what I do to this computer, my mail will remain available. Let's face it, for most backup is little more than a good intention, so every little helps!

---

