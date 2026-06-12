---
title: "Reoccurring Internet Problem"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2007-09-04
Good afternoon,

I have a problem with certain websites such as gmail.com not loading. Although this problem is infrequent, I have not found any solution. Essentially, what happens is, my browser loads most pages, but when I visit gmail.com, the site doesn't load until I reboot my computer.

This is what I have tried:

Disabling ipv6 in firefox
Using opera
Running firefox in safe mode
Unplugging the ethernet cable from my computer
Resetting the router
Changing general.useragent.extra.firefoxComment Ubuntu-feisty to Ubuntu 7.04

Here's what I haven't tried:

Changing DNS servers (What are the pros and cons of this option?)
changing /etc/resolv.conf to a different I.P. (Not exactly sure how to do this... Which I.P.?)

(Note I am on the 64bit architecture)

Any help would be appreciated,

- John

(P.S. As a side note, when I am in the terminal and I type a command, the success or failure of the command is not shown. For instance, if I type "sudo chown john /home/.dmrc", the terminal does not display any information after the command is entered. Is there a remedy for this problem?)

---

### Post by guardsman85 on 2007-09-04
> **anothrguitarist said:**
> Here's what I haven't tried:

Changing DNS servers (What are the pros and cons of this option?)
changing /etc/resolv.conf to a different I.P. (Not exactly sure how to do this... Which I.P.?)

These essentially do the same thing as /etc/resolv.conf lists your DNS servers.  While I think it's best to use a server you trust (e.g. your ISP's or company's) there are some other options.  I know some people who swear by  [http://www.opendns.com/](http://www.opendns.com/).

---

### Post by anothrguitarist on 2007-09-05
Thanks for the information.

I think I will stick with my ISP's server.

Does anyone else have another solution?

---

### Post by anothrguitarist on 2007-11-04
Alright, so now that Ubuntu 7.10 has been released and I've downloaded the update, I thought that my internet woes would go away, yet the problem remains. I still cannot log onto gmail.com, on occasion. Any help would be appreciated.

---

