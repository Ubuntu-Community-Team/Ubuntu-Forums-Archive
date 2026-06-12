---
title: "Evolution Mail"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2008-03-20
Is there an easy way to back up all the mail in Evolution?

Is there a way to stop it from deleting the mail from Yahoo! servers when I check it using Evolution?

I'm mainly look for a way to back up my mail, because I want to upgrade to a new version of Ubuntu, using a fresh install. Will this mess up anything?

---

### Post by Rolcol on 2008-03-20
You have to set up the email account on its own so it does not remove the emails from the server.

Edit > Preferences > Mail Accounts > (Select the account you wish to fix) > Edit > Receiving Options > Leave messages on server > OK

---

### Post by neotasic1 on 2008-03-21
> **OhioYJ said:**
> Is there an easy way to back up all the mail in Evolution?

Is there a way to stop it from deleting the mail from Yahoo! servers when I check it using Evolution?

I'm mainly look for a way to back up my mail, because I want to upgrade to a new version of Ubuntu, using a fresh install. Will this mess up anything?


File>Backup Settings... will bring up a dialogue box asking where you want to save the default backup file- 
evolution-backup.tar.gz
Pick a destination directory (the default will be your home directory) or save it to an external drive.  You will be able to restore all your settings from this file using:-

File>Restore Settings... and pointing to this saved file.

If you do a fresh install you may want to consider backing up all your data in your home directory if you have not already done so.

Good luck

---

### Post by neerajadsul on 2008-03-21
Simple way is to use IMAP protocol for setting up Evolution. If you are using POP3 account then mails will be deleted from server. In IMAP it won't

POP3 is **P**ost **O**ffice **P**rotocol therefore it doesn't keep emails, like Post Offices.
IMAP is **I**neternet**M**essage**A**Access**P**rotocol. Which is developed for using email client on a lot of different computers so it keeps emails on server always.



Also you might need to turn on IMAP settings in your yahoo account.
 Follwoing might help you -
[http://yahoo.weblogsinc.com/2006/06/24/yahoo-mail-getting-free-imap-access/](http://yahoo.weblogsinc.com/2006/06/24/yahoo-mail-getting-free-imap-access/)

---

