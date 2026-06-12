---
title: "configuring mail server"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by HurricaneDan on 2007-05-05
I am looking to set up a mail server on a feisty fawn server.  I have configured my apache install to handle virtual servers (they are up, tested and running).  I do not know much linux but I can follow directions pretty well.  I attempted this tutorial: [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer) but it does not seem to be working.  I cannot set up my mail client (on a macbook pro).  I attempted to send out an email through webmin after configuration but it never reached its destination.  I am thinking that I have issues with the MTA and MUA.

So basically I would like to start from scratch and get a mail server set up.

Thanks,

Dan

---

### Post by Metacarpal on 2007-05-07
Hi Dan,

Just a quick idea - have you checked to see if you have port 25 (the default for email) open on the server in question?

On the server, run this command (where *changethis* is the server's hostname or IP):

```
telnet *changethis* 25
```

If you get a "connection refused", then you need to open that port on your firewall.  If you're not familiar with firewall configuration, firestarter is a useful package to install.

---

