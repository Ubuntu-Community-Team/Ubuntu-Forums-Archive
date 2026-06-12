---
title: "Evolution not downloading gmail"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by jtomoso on 2007-04-02
Hello

I had evolution working with gmail for about a month, and then recently the update manager updated a bunch of stuff on my install.  Now, even though the settings have stayed the same, I can't download or send emails using gmail.  So I tried firefox, and it has the same problem.  It's like the pop.gmail.com and smtp.gmail.com servers aren't there.

I've tried specifying the ports to connect to, I've tried deleting and recreating the account.  Nothing seems to work to resolve the problem in Evolution.

I CAN ping the pop and smtp servers, though. And I CAN use gmail through the web client.  It just doesn't work through Evolution.  Any ideas?

---

### Post by PurplePenguin on 2007-04-02
I've got gmail working fine through evolution and Edgy.  Let's see if our settings are the same (keep an eye out for the proper ports).

Receiving mail
Server type: POP
Server: pop.gmail.com:995
Use: SSL

Sending mail
Server type: SMTP
Server: smtp.gmail.com:465
Check box marked "Server requires authentication"
Use: SSL

For authentication, in both cases, your username MUST have the @gmail.com attached.

Do these match up with what you've got?

---

### Post by jtomoso on 2007-04-03
Set up the same as you.  It still doesn't work.  Hmm...are there any settings in Ubuntu itself that would keep Evolution from communicating w/ gmail?

---

### Post by nike984 on 2007-04-03
go to your account of gmail and change the pop3 setting to 
"Enable POP only for **mail that arrives from now on**".

Then delete the current gmail account information in Evolution and 
made a new one. 

Then try to fetch your mail again.

---

### Post by RKCole on 2007-04-03
I had this same problem about a week ago with Thunderbird.  I actually went into my GMail account (via Firefox), and went to Settings->Forwarding and POP.  I figured I'd give this a shot in the dark, so under the **POP Download** section, I activated the **Enable POP only for mail that arrives from now on** radio button and saved the changes.  I don't know how or why Thunderbird stopped getting my mail...but doing that solved my problem.

I'm not sure if it's the same issue for you or not, but I wanted to post just in case.

Take care.

---

### Post by RKCole on 2007-04-03
Sorry for the repeat.  Got to it just a second before me, nike984.  :)  Wonder what the deal was with GMail...

---

### Post by Permafrost91 on 2007-04-21
This is weird ... for the last week or so Evolution has completely stopped downloading emails from one of my gmail accounts but not from the other ... any ideas why? Is there a way to flush evolution's mail cache so it sees all the messages on the gmail server as new messages?

---

