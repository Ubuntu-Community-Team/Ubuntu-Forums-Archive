---
title: "Centralized mail."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2008-02-17
I will try and explain my setup here.

I have a POP3 account with my ISP for my business mail. At the moment this comes into my thunderbird on my "server" where i keep all my files. However, when i am working on my laptops or away from home, the only way i can get my mail is to log in via ssh/vnc and use thunderbird.

Is there a way of having my server download the mail, Then whenever i run thunderbird on another machine, still able to view the mail & contacts?

In outlook this can be done fairly easily by mounting the PST file over the network.

I guess the best way would be to turn my server into its own pop3 system which collects new mail from my real account automatically but i log into that instead of the real one.

Anyone know how?

---

### Post by davec64 on 2008-02-17
Hi sorry I can't tell you how to do it, but ig you can get hold of Linux Format, there's a tutorial in the Magazine on how to build your own mail server.

I also found this link which might be useful:

[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

---

### Post by bergersau on 2008-02-17
You need to setup your own IMAP mail server, and use fetchmail or similar to retrieve your mail from your POP3 account/s in order to be able to access your mail from any machine in this fashion.

Have a listen to this podcast for idea's.

[http://www.linuxreality.com/podcast/episode-61-home-servers-part-7-simple-email-server/]("http://www.linuxreality.com/podcast/episode-61-home-servers-part-7-simple-email-server/")

---

