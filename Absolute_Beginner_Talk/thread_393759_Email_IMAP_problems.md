---
title: "Email IMAP problems"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-03-26
Hi

I am new to Ubuntu and have a major problem with email.

Un summary I have two users each with Thunderbird and Evolution installed, I use an IMAP email account with different folders for each user , i.e. USER1.Inbox & USER2.Inbox.

When I set up either email clients and set to show only subscribed folders i.e. User1 can only see User1.Inbox ans User2 can only see User2.Inbox the settings are not unique to each user, changes I make in one Thunderbird profile effect the other profile.  Likewise and folders I hide in Thunderbird get reflected in Evolution.

Is there a central setting file that I need to change, with Outlook in XP each profile is unique.  With Ubuntu it looks like a system setting is being effected each time I subscribe/unsubscribe to IMAP folders.

Help Please!!!

---

### Post by cowlip on 2007-03-26
That's very odd, so they have separate /home directories and they're still somehow interacting?  Were these both programs installed from the Ubuntu repositories?

---

### Post by ushills on 2007-03-27
Yes, they were installed from the add/remove option in Ubuntu.  Evolution was part of the initial install, Thunderbird I added to see if that would work.

I assume that there is a share email configuration file that is common to the system and that this remembers the subscribed IMAP folders.

I thought that each user account was totally seperate, I also thought that programs installed as one user were also seperate, as a note the User1 account has admin priviliges.

---

### Post by ushills on 2007-03-27
The same Fastmail account is used for both users as I direct all email from my domain name to that fastmail account, I then filter the email to each user depending on the to: email address. ie. [email]user1@domain.com[/email] and user [email]2@domain.com[/email]. 

What I used to do with Outlook(or anyother email clinet) under XP, was to set up two profiles and in one hide user1's folders in the other hide user2's folders. 

Each user in Ubuntu has their own login and own profile that is stored under /home/user1/Thunderbird and /home/user2/Thunderbird respectivly. 

All of the settings in tools >etc are as default, and some of the settings appear to be downloaded from the fastmail server as I did not fill anything in but some boxes are filled, with "INBOX", "", "user.". 

Why would settings be copied from one profile to another, I thought that each profile stood alone.

---

