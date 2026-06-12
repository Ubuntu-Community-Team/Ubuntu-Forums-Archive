---
title: "Evolution and Exchange problems (LDAP related?)"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by tsumi on 2007-06-29
I do not know if this falls under absolute beginner talk but I was not sure where else to put it..

PROBLEM: Evolution launches VERY slowly loses connection to Exchange back end process.

It seems like when I kick on Evolution in the morning it can take between 3 and 5 minutes (sometimes much longer) just to get the app launched and talking to the Exchange server. That is rather annoying but what is worse is that often I find that Evolution loses connection to the Exchange back end process. This is very annoying because the end result is that I have to kill evolution, drop out to a shell and hunt down all the other processes that Evolution uses, then relaunch Evolution waiting for the app to launch again. ](*,)

My mailbox size is just over 114 megs. Looking through the Exchange system manager I notice that 114 megs is not a huge mailbox size by company standards (although I am the only person in the entire organization using a non MS machine). Is that large by most peoples standards? Could that have something to do with the slow app launch?

I did notice something that I found interesting today tho that might be of interest to the developers of Evolution / anyone else who wants to take a closer look at it. It seems like Evolution loses the connection to the Exchange back end process when I do a global LDAP query. Thinking back on it this might have everything to do with why it crashing as a mail app may decide to do an LDAP query any time you start to enter a To address.

Does anyone have any ideas as to how I might resolve this? OWA (web access) is a pain in the butt to use.

---

### Post by Skrynesaver on 2007-06-29
I have heard of this before, Evolution has to sync all the mails in your IMAP account before you can send an IMAP command (move mails to new folders, send mails etc.) This is due to Exchanges unique support for the IMAP standard.

I have heard of a fix for Evolution that only pulls the first 100 mails from the Exchange server, but sadly don't remember were I heard of it :(

---

### Post by into_311 on 2007-06-29
It seems to me that Evolution, when using the e xchange plugin, seems to access your email through an OWA interface.

Is OWA slow if you fire up a browser and browse into it that way?

---

### Post by tsumi on 2007-06-29
Dang. Anyone else know about the first 100 email fix? That would work so long as I checked it frequently enough. Maybe I can use that fix and up the number of emails it pulls?

What I gather here is ultimately what is failing is the number of messages while syncing?

---

### Post by tsumi on 2007-06-29
> **into_311 said:**
> It seems to me that Evolution, when using the e xchange plugin, seems to access your email through an OWA interface.

Is OWA slow if you fire up a browser and browse into it that way?

Yes, I am using the exchange plugin to access the OWA interface, and no, the normal browser OWA works very quickly its just an annoying interface.

---

### Post by ryan-au on 2007-07-06
Strace evolution in the environment it starts slowly in, mine was related to the GAL which uses port 3268 to do an LDAP query (host 10.2.10.3 below):

```
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 17
setsockopt(17, SOL_TCP, TCP_NODELAY, [1], 4) = 0
fcntl64(17, F_GETFL)                    = 0x2 (flags O_RDWR)
fcntl64(17, F_SETFL, O_RDWR|O_NONBLOCK) = 0
connect(17, {sa_family=AF_INET, sin_port=htons(3268),
sin_addr=inet_addr("10.2.10.3")}, 16) = -1 EINPROGRESS (Operation now in
progress)
```

<3 minute delay goes here>

This was when I was trying to contact the local work 10.2.10.3 address from home.  In the end I setup a persistent key based SSH tunnel to work and set my GAL to use localhost.  The beauty of that is when you don't set the tunnel up, localhost still responds at startup so the program loads instantly.

YMMV, but worked for me :)

---

