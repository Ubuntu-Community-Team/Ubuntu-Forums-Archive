---
title: "Creating a replacement server from backed up files"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by toyotafosgate on 2007-09-28
I've tried over the last week to find a way to create a replacement server using the backup files I have which consist of the directories of /home and /etc. Does anyone have any suggestions for me on how to go about restoring them to an Ubuntu server. I've tried many different ways and I always end up with some sort of error or something won't work. I just need smtp and pop running so that I can copy over the maildir's and preferences so that it will function like an e-mail server.

                  Thank you in advance for any help you can provide.......
:mad:Its so frustrating after a week of trying everything I could.

---

### Post by HermanAB on 2007-09-28
Hmm, there is no easy way.  You have now discovered why Unix Admins only back-up data.  You have to install the machine from scratch, then copy the data over.  

You could probably save yourself a lot of trouble by using a Linux distribution that has proper server wizards, like Mandriva, which has wizards for everything, so using that, you can have a Postfix mail server running within two or three hours.

Cheers,

Herman

---

### Post by Gone fishing on 2007-09-28
I found this:

[http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/)

I was wondering whether, webmin might make the migration of user accounts easy - I'm interested to know how this goes as I'm considering migrating a Suse server to Ubuntu or Debian

---

