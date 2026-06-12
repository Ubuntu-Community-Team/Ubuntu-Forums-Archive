---
title: "how to login irc"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by purpleleave on 2007-04-28
Here is the guide,
"If you are very new to Ubuntu, and haven't used IRC before, find the application 'gaim' from Applications->Internet on your Ubuntu desktop. Then login to irc.freenode.net and join the #ubuntu channel."

but where can I register a new account to login #ubuntu channel.
I went to freenode.net but cannot find the address for registration.
Thank you.

---

### Post by dante.regis on 2007-04-28
The registration process takes place inside irc itself. 

When you connect, first make sure that your nickname is not already taken. If it is, You will receive a message like this one:

```
-NickServ- This nickname is owned by someone else
-NickServ- If this is your nickname, type /msg NickServ IDENTIFY <password>
* Recebeu um CTCP VERSION de freenode-connect
```

On this case, all you can do is choose another nickname (/nick my_other_nickname)

If it is not, just send the following command:

```
/msg NickServ register mypassword
```

Remember to change "mypassword" for something else, and also remember that passwords, as everywhere else, are case-sensitive. 

If the registration went fine, the next type you login, all you will have to do is authenticate with this comand:
```
/msg NickServ identify mypassword
```

If you need more help with NickServ, just type 
```
/msg NickServ help
```

Best,
Dante

---

### Post by purpleleave on 2007-04-28
Thank you very much. It works.
I successfully login on #ubuntu channel.
but when I try to get information about #ubuntu channel,
type "list #ubuntu", and it works like the following.

(01:39:19 AM) purple: list #ubuntu
(01:39:20 AM) ChanServ: (notice) -- Listing channels matching [#ubuntu] --
(01:39:20 AM) ChanServ: (notice) #ubuntu       << ACTIVE >> created 2 years 45 weeks 2 days (17h 41m 54s) ago
(01:39:20 AM) ChanServ: (notice) -- End of list (1/1 matches shown) --

but when I try to search more ubuntu channels and type:
> list #ubuntu*
it just crash.
bug? any idea?

---

### Post by Nythain on 2007-04-28
not sure... i know a long long time ago in a galaxy called windows, most clients would crash if the list return was to big... but that was a logn time ago, surely that cant be the issue now... maybe it doesnt like * in the commands... i havent used gaim for irc...

---

### Post by purpleleave on 2007-04-28
It is normal for 
```
list #ubuntu-z*
```

(02:05:55 AM) purple: list #ubuntu-z*
(02:05:55 AM) ChanServ: (notice) -- Listing channels matching [#ubuntu-z*] --
(02:05:56 AM) ChanServ: (notice) #ubuntu-za    << ACTIVE >> created 1 year 40 weeks 1 day (6h 38m 12s) ago
(02:05:56 AM) ChanServ: (notice) #ubuntu-zh    << ACTIVE >> created 2 years 4 weeks 1 day (10h 55m 43s) ago
(02:05:56 AM) ChanServ: (notice) #ubuntu-za-fans                 created 45 weeks 6 days (2h 51m 11s) ago
(02:05:56 AM) ChanServ: (notice) -- End of list (3/3 matches shown) --

maybe it is really the "return too big" problem,

---

