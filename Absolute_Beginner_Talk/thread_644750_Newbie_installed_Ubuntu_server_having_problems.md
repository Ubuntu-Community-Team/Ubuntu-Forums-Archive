---
title: "Newbie installed Ubuntu server having problems"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by shabakahn on 2007-12-19
I just installed ubunto LAMP server (Gutsy) Install went clean a boot's and allows me to login. When I try and sudo apt-get install or any sudo command I am getting the following command:

sendmail: fatal: open /etc/postfix/main.cf: No such file or listing

It looks like a permissions issue? but if I can't sudo I can't correct it.

Thanks for the anticipated help

---

### Post by hyper_ch on 2007-12-19
Can you copy'n'paste the whole thing?

---

### Post by Cypher on 2007-12-19
Strange that Sendmail should complain when you do any Sudo command..for the time being you might want to disable Sendmail and enable it later on (after configuring it) if needed..

---

### Post by shabakahn on 2007-12-19
**>>Can you copy'n'paste the whole thing?**

Copy and paste what ? The error was exactly as I typed it in.

The orginal command I typed in was :

sudo apt-get install vim

Error it returned:

sendmail: fatal: open /etc/postfix/main.cf: No such file or listing

**>>Strange that Sendmail should complain when you do any Sudo command..for the time being you might want to disable Sendmail and enable it later on (after configuring it) if needed..**

How do I disable sendmail without being able to sudo ?

I did look in the /etc/postfix/ folder and there is no main.cf file listed.

Thanks :)

---

### Post by shabakahn on 2007-12-19
Fixed it

I did a re-install and didn't and the Mail server... All is well! But still Strange!

Thanks Again:popcorn:

---

