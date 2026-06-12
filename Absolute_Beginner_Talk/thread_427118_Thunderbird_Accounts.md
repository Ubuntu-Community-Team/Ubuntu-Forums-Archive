---
title: "Thunderbird Accounts"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-04-29
Hi,
I want to set up multiple accounts on Thunderbird which will filter all incoming mail by the recipients name.  I have multiple log ins on Ubuntu and want to set up Thunderbird for each person, our mail addresses are the same but differ only by the first name.  I have searched around and can set different identities OK which alter the signature and return address, and can set different folders for mail but cannot see any way to filter by first name.  It was relatively simple on Outlook to do this.   I have probably missed something obvious but if somebody could point me in the right direction.

---

### Post by quark_77 on 2007-04-30
Hi campingman,

If you have multiple log ins, then each user will have a directory /home/username/.mozilla-thunderbird where their user profile is stored for the thunderbird program. If each user has their own email address [email]firstname@ourfamilyname.co.uk[/email] then each user only needs to set up their email address on their own account.

That is one solution, possibly the most simple and secure. If you have one email inbox and aliases for the other email addresses things become a little more complex. You can use Thunderbird to filter (search folders) based on certain criteria including recipient so you can separate your email apart this way. There is a method of moving mail too should you not want to use search folders. As far as file system access goes, each user needs to configure the email account themselves. Email should not be stored in a 'global inbox' as this really means 'this users inbox'. Instead locate the folder where the email is stored on a directory with read-write permissions for all your users and have each account point to this folder. That way all of you will access the same local copy of your inbox.

If you are talking about having profiles on Thunderbird, this is also possible using the profile manager which should be in the internet menu, if not mozilla-thunderbird -ProfileManager from the console. Bear in mind that profiles created on one user only reside in that users .moziila-thunderbird directory. Other users be prompted to set up an email address, just as under Windows.

These are the most common scenarios I can think of, hope this helps!! Post back if you need any further help.

Quark_77

---

