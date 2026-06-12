---
title: "Revert Chown in not so many files (looking for log)"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by fedejofa on 2008-03-22
Yeah, i have seen many people asking them, but the solution i found was reinstalling.
I made that error, but without -R (ufff!) so i guess the going bakc solution, if its possible, is not so hard.
I would like to know where i can find a log or something that tell me what i changed or something. I promise i will be more cautious adn work hard reading from start to end a good linux manual and wont come more with this newbies questions.
THx for your help. Really.
Greetings. ( i lost the similar questions also!)

---

### Post by fedejofa on 2008-03-22
> **fedejofa said:**
> Yeah, i have seen many people asking them, but the solution i found was reinstalling.
I made that error, but without -R (ufff!) so i guess the going bakc solution, if its possible, is not so hard.
I would like to know where i can find a log or something that tell me what i changed or something. I promise i will be more cautious adn work hard reading from start to end a good linux manual and wont come more with this newbies questions.
THx for your help. Really.
Greetings. ( i lost the similar questions also!)

Adding other question: I think i can get a backup with the correct owners. Can anyone tell me a 'quick' way of extracting the user info of the files (files out of date but same name) (using ls -l ) and changing the other files with that info. using the pipe thing (output | input) .
Thx.

---

### Post by nick_h on 2008-03-23
If you used sudo then the commands will be in the /var/log/auth.log file.

You can view it with System->Administration->System Log

With a single directory all the files were probably owned by the same user so it probably isn't worth doing anything complex to reset ownership.

---

### Post by fedejofa on 2008-03-23
Thanxs. :KS

---

