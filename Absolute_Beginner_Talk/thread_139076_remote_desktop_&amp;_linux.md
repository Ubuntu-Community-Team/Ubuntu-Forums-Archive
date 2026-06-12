---
title: "remote desktop &amp; linux"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by shadowfist on 2006-03-03
I am using breezy and there seems to be two different "remote desktop" programs. KRDC and terminal server client. it looks like both of these support microsoft xp remote desktop but I cant get either of them to work. is there a differnt program I need to use? why is it not working?

---

### Post by yota on 2006-03-03
For me both tsclient and krdc (having installed rdesktop package that enables rdp support) "Just Work" with win 2000 and 2003 telminal servers.

Have you used the correct syntax (rdp:/fqdn.or.ip.of.the.server) in krdc?
Have a look at "examples" on the krdc window...

If so, what errors do you get? Is the lan working?

---

### Post by shadowfist on 2006-03-03
well the lan is working because i can get to the machines with samba. but when i try to connect I get error messages like "cannot find remote host" (tsclient) and unable to astablish connection (krdc)

---

### Post by yota on 2006-03-06
What versions are you using? (0.140-1ubuntu2 and 3.4.3-0ubuntu1 here)

I'm asking that because I did some test on my my machines (disabling dns, turning firewall on, shutting down the service on windows...) to simulate your problem, but I can't get the same messages as you.

So, feeling curious, I did a:
```

grep -i establish /usr/bin/krdc

```
and a
```

grep -i remote /usr/bin/tsclient

```
This way I found that the messages you reported are not even existent on my binaries... ("view /usr/bin/krdc" confirmed that messages are in clear text inside binaries). Maybe we are using different versions: can you update to the latest one? If you're already up to date can you please post more details like your ubuntu version, kernel version and the exact procedure you're following.

Hope we can figure this out! ;-)

---

