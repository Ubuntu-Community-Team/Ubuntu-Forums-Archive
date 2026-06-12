---
title: "Firefox security warning"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-07-26
This is a standard Firefox security warning > 
the information you have entered is to be sent over an unencrypted connection and could easily be read by a third party I was wondering, does anybody know how this is possible --how can it be read?

---

### Post by zanglang on 2007-07-26
It just means you're POST-ing a form over a non-SSL connection. In this case, there is a possibility that someone might have intercepted your connection to perform a "Man-in-the-middle attack":
[http://en.wikipedia.org/wiki/Man-in-the-middle_attack](http://en.wikipedia.org/wiki/Man-in-the-middle_attack)

Edit: A diagram here summarizes how an SSH man-in-middle-attack could be performed.
[http://www.vandyke.com/solutions/ssh_overview/ssh_overview_threats.html](http://www.vandyke.com/solutions/ssh_overview/ssh_overview_threats.html)

With SSL, all data is essentially tunneled through an encrypted connection so the "middle-man" cannot eavesdrop on the data easily, and both client and server's identities may be verified via certificates to detect spoofing.

---

### Post by wieman01 on 2007-07-26
Network sniffing tools will do the job. No SSL = No security.

---

### Post by asmoore82 on 2007-07-26
In order to do so you would have to run a packet sniffer such as 'wireshark' over the wide internet.
'wireshark' is fun to play with on a local network but using it on misc. Internet traffic is almost always a gross violation of your agreement with your Internet Service Provider. If you are not very sneaky and carefull the Men in Black WILL come Cut your HardLine :ninja:

---

### Post by arijarot on 2007-07-26
Thanks for the replies, guys. So after reading about the MITM attacks and how it can be done, it seems to me that there is really no way to have a prevent secure transfers on pages that don't encrypt the info, for example, an email like hotmail or gmail.

---

### Post by wieman01 on 2007-07-26
> **arijarot said:**
> Thanks for the replies, guys. So after reading about the MITM attacks and how it can be done, it seems to me that there is really no way to have a prevent secure transfers on pages that don't encrypt the info, for example, an email like hotmail or gmail.
No, there isn't unless you encrypt the data yourself (e.g. GPG). Nothing remains secret on the web.

---

### Post by arijarot on 2007-07-26
"scary" stuff when you think about it.

---

