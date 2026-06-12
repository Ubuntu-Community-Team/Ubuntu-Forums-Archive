---
title: "Email Clients and PST files"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by houseisland on 2006-08-07
1.  What are the better home-use email clients available for Dapper?

Evolution is packed with it.  Thunderbird is readily available.

Opinions?

2.  How can one import an Outlook PST file in to one's Dapper client of choice?

I would assume that something would have to be done in Windows first to prepare the importation -- importing Outlook mailboxes into a 3rd party, Linux friendly client such as Thunderbird.

Advice?

Thanks.

---

### Post by houseisland on 2006-08-07
Well that was painful........ but is is done.  Outlook mailbox moved to Evolution.

Since the migration tool in Evolution does not accept PST files, I installed Thunderbird and migrated the Outlook mailbox in Windows.  I then copied the mail folder for Thunderbird over to the Dapper box.

The Evolution import tool would not recognize the Thunderbird files and so would not import them.

So I found the Evolution folder in the /home/user directory removed the mailbox files and replaced them with the Thunderbird ones.  Then I started Evolution and created the necessary subfolders to match those from Outlook.  I shut down Evolution, went the /home/user folder, deleted the files for the new subfolders and replaced them with those from Thunderbird.  Seems to be OK.  Functional.  No error messages.

What an ugly ungraceful migration.   :p

---

