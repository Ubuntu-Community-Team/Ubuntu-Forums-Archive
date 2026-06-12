---
title: "Cross platform Thunderbird syncing/sharing email, contacts and calendars."
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-08-25
I have computers running OS X, Ubuntu Jaunty and XP. I would like to be able to sync/share e-mail, contacts and calendars between the computers and operating systems. I also have an iPhone 1st. generation, so I have started testing [http://www.interways.de/en]("http://www.interways.de/en") This works for everything except for the local e-mail message folders.

(I don't want to sync/share all of my mail with my iPhone.)

I have done a lot of searching, but haven't found workable solutions that support Thunderbird on all platforms. The closest I have found is [http://www.syncables.com/]("http://www.syncables.com/") but weirdly, it doesn't seem to support Thunderbird on all platforms, and only supports MS Office files.

Can anyone provide me with a link to a HowTo or to a product that provides the features that I am looking for?

Cheers

---

### Post by tovrstra on 2010-06-13
I had a similar problem. I already use an IMAP mail account so that all mail is in principle automatically synchronized between different clients, but the quota on this mail account do not allow me to keep all large emails with large attachments. I used to store them in local folders in Thunderbird, but these are not synchronized, which is at least annoying. So we have sort of the same problem.

The following worked for me. I have one machine that is practically always running with internet access. On that machine I run Dovecot (on Ubuntu 10.04), an IMAP mail server that just takes 5 minutes to configure. Because I administer that server myself, I have no real quota limits there. I only have a 'Big' folder on that account to keep all the mails with large attachments. On all machines I configure Thunderbid to use that server next to my work and other private accounts. I hope this helps.

---

