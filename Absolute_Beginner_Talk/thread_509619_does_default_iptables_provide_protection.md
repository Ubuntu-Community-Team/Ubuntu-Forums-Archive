---
title: "does default iptables provide protection?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by feistyfirsttimer on 2007-07-25
Does iptables, as installed by default in feisty, actually comprise a firewall and provide protection?

---

### Post by lisati on 2007-07-25
From what I've read elsewhere, the tendency in Linux is to provide stronger protection than "other systems"

---

### Post by wolfen69 on 2007-07-25
yes, it is a basic firewall.

---

### Post by feistyfirsttimer on 2007-07-25
Thanks for the swift responses guys!

I'm currently using my box for web browsing (duh!), SSH, and the email stuff that evolution does (POP and SMTP?)  iptables doesn't seem to interfere with any of that.  But soon I'm gonna be doing some FTP work.  Will iptables need any configuration?  And if so, can anyone point this newbie toward a simple tutorial?

---

### Post by lemonseed on 2007-07-25
As far as I know, the default setting of iptables allow ALL outgoing connections and incoming is limited to average user services (http, ftp, stmp, etc). I could be wrong though.

---

### Post by annda on 2007-07-25
firestarter is a simple GUI for iptables. you can install it and see what is going on, and also easily configure what it calls 'policies', which translates to traffic rules.

---

### Post by feistyfirsttimer on 2007-07-25
**Thanks a lot everyone!!**

---

