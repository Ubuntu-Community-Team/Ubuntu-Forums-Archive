---
title: "FIREFOX problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by dineshs on 2008-01-02
I am a beginner using 7.04 and 7.1 on different partitions . I find too much delay in getting certain sites while using  gutsy ( OK while using Feisty).IPv6 is disabled in both.Please help

---

### Post by ~LoKe on 2008-01-02
Are you using the same version of firefox?

---

### Post by alienexplorers on 2008-01-02
Did you disable IPv6 in Ubuntu.  I found this helped speed things up with Firefox. In modprobe.d in the directory /etc/modprobe.d edit the aliases file and add these first 3 lines and comment out the last.
> alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

---

### Post by ~LoKe on 2008-01-02
> **alienexplorers said:**
> Did you disable IPv6 in Ubuntu.  I found this helped speed things up with Firefox. In modprobe.d in the directory /etc/modprobe.d edit the aliases file and add these first 3 lines and comment out the last.

His original post says he did. =]

---

### Post by dineshs on 2008-01-02
I shall check the version and post the reply.Any way can I install the older version(The one in Feisty) of firefox in Gutsy and how?

---

### Post by ~LoKe on 2008-01-02
> **dineshs said:**
> I shall check the version and post the reply.Any way can I install the older version(The one in Feisty) of firefox in Gutsy and how?

The only way I can think of is to track down the source package for that version and compile it yourself, unless you can find an old .deb.

---

### Post by dineshs on 2008-01-02
Let me try

---

### Post by ~LoKe on 2008-01-02
If you tell me what version you want, I could probably find the source/deb file.

---

### Post by Rippie on 2008-01-02
You could try this guide, i found it very useful

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by dineshs on 2008-01-03
I dont think the problem is with firefox because I fully removed firefox then installed opera,but the problem remains.Anyway i shall try above suggestions

---

### Post by lasthand on 2008-01-03
What sites are giving you lots of lag? What speed is your connection?

---

### Post by dineshs on 2008-01-03
Regarding the version 2.0.0.3 will work I think

---

### Post by dineshs on 2008-01-03
There is a site data.bsnl.in (maintained by our service provider) The speed of connection is 2.048Mbps

---

