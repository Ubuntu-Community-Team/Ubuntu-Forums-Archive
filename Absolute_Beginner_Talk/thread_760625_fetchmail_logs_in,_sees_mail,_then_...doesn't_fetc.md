---
title: "fetchmail logs in, sees mail, then ...doesn't fetch it"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by abalone on 2008-04-20
I had fetchmail working before, but ever since reinstalling 32 bit Gutsy (fresh drive) it's not doing anything anymore, not even with a very minimal ~/.fetchmailrc.

Example run:

abalone@earthworm:~$ fetchmail
66 messages for username at pop.gmx.net (15989957 octets).

(Nothing happens... I wait for a long time... then press Ctrl-C)

Message [email]username@pop.gmx.net[/email]:1 of 66 is being read (1604 bytes)fetchmail: terminated with signal 2
abalone@earthworm:~$    

(Yes, that bit about reading message 1 of 66 appears **after** aborting fetchmail)

I rebuilt .fetchmailrc with fetchmailconf, but same thing. Fetchmailconf crashes when I test the configuration. 

set postmaster "abalone"
set bouncemail
set no spambounce
set properties ""
poll pop.gmx.net with proto APOP
       user 'username' there with password 'password' is 'abalone' here options keep
#set daemon 60 (just starting it manually for testing)

.fetchmailrc is readable and writable for my user only.

The /var/mail dir is empty.

I can't think of anything I've done differently this time. (Postfix stopped working, too. But I don't think this has anything to do with it.)

PS: Sorry, quoted output was re-translated from German.

---

### Post by abalone on 2008-04-20
Mh. Maybe it does have something to do with it?

When I wait for fetchmail about as long as it takes for my dysfunctional postfix to time out:

fetchmail: SMTP connection to localhost failed
fetchmail: SMTP transaction error while fetching from [email]username@pop.gmx.net[/email] and delivering to SMTP host localhost
Message [email]username@pop.gmx.net[/email]:1 of 66 is being read (1604 Bytes)fetchmail: query status=10 (SMTP)

(again translated from German)

So I suppose my fetchmail problem has become a postfix problem.

---

### Post by abalone on 2008-04-20
Which I've "solved" by letting dpkg-reconfigure postfix reconfigure whatever it reconfigures, and then writing my own main.cf back over the one it wrote. Well, if you can call something your "own" that you don't really understand :rolleyes:

---

