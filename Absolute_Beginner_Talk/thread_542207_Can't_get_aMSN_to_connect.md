---
title: "Can't get aMSN to connect"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Fraoch on 2007-09-03
What do I have to do to get this program to connect?

I keep getting "Error connecting to server: couldn't open socket: host is unreachable".

I believe I have opened this port in iptables:

```
sudo iptables -A INPUT -p tcp --dport 1863 -j ACCEPT
```

and I port-forwarded 1863 in my router, but no dice.

I also tried the HTTP (port 80) connection, which should work because I have web access, but same error.

Any help?  Thanks.

---

### Post by shearn89 on 2007-09-04
Are you behind a proxy server?

---

### Post by Fraoch on 2007-09-04
> **shearn89 said:**
> Are you behind a proxy server?

No.

Maybe my trouble is with the incredibly hard-to-use MSN site.  I *think* I signed up and I can sign in but I have no idea what my handle is!  Whenever I try to get it I get redirected to "Microsoft Live" and can't seem to get anywhere - it wants me to download the Windows app and won't do anything else.

Do you have to get a Hotmail account in order for it to work?  My gMail account is working fine for logging into the site, but maybe not for logging into aMSN?

This is why I left Microsoft - this Web 2.0 approach means that if things go wrong you have no idea what to do or what/where you should go.  The application/web page/instructions get trimmed and customized for what it thinks is your use case and you lose everything else.

---

### Post by Fraoch on 2007-09-04
Well I appear to have gotten Pidgin working without too many heroics, so I'll stick with that.

---

### Post by shearn89 on 2007-09-05
I think your meant to have a hotmail account to use MSN, although i'm not 100% certain...

---

### Post by inflamous on 2008-01-10
I have the exact same problem, I'm using Kubuntu 7.04 with aMSN v0.97.

I even took out my firewall and it didn't get fixed. I checked my /etc/hosts file and, well I didn't know what thats for so I didn't touch it :S

I can't see why it won't connect... what else would reject a program from connecting to the internet?

I'm using a hotmail account and it works in KMess, but I want to use aMSN for its offline messaging abilities :)

---

### Post by inflamous on 2008-01-12
I got amsn to work by changing my /etc/hosts file and changing the MSN Messenger Server to "messenger.live.com" to "messenger.hotmail.com"

---

