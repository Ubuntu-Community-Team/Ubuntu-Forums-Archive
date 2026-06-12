---
title: "ubuntu 6.06 LAMP server - send mail only (no mail server)"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by bede on 2006-11-28
Have successfully set up ubuntu6.06 LAMP server - thanks to many helpful tutorials found on the web and in this forum.

My php based app needs to send e-mails via a SMTP server on  another box/ip, but I do not want a mail server installed.

php.ini seems to want sendmail installed, which from my reading seems to be a server, not just a MTA for sending to a remote SMTP server.

An alternative may be ssmtp, but although installation looks reasonably straightforward  (assuming it can be obtained using apt-get install) I am not sure how to interface it to php - or do I simply put the command line into the sendmail config line?

Have looked in the forums but posts seem to refer to sendmail or to setting up a mail server.

Comments/help welcome
TIA

---

### Post by roobarb! on 2006-11-28
I'm no expert, but it sounds to me like you need [Postfix]("http://packages.ubuntu.com/dapper/mail/postfix"). Yes, it's a mail server, but I don't know of any apps that would give you *just* mail sending support. I could very easily be wrong though.

```
apt-get install postfix
```

So long as the incoming port for SMTP connections is closed on your firewall, you shouldn't have anything to worry about - it's port 25 by default.

Hope that helps. Might be a good plan to check back here to see how wrong I've been too. ;)

---

### Post by Alpha_omega16 on 2006-11-29
I also just need my server to just send e-mails. If need be I will setup a full mail server it makes no difference to me. I have installed postfix but can't seem to get it to send an e-mail. I also have the 6.06 LAMP installed. any help with the configurations would be greatly appriciated

---

### Post by ginkhao on 2006-11-29
I was waiting for someone more knowledgeable to answer your question, but in the meantime I had a play around with a VM and got it sending mail so I'll share what I did.

I installed Ubuntu server (didn't install LAMP but that shouldn't make any difference)
Then installed Postfix using this command:
apt-get install postfix libsasl2 sasl2-bin libsasl2-modules libdb3-util procmail
(from here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix))

Then basically answered the questions as per the link except used blank for domain name

I had to edit the /etc/postfix/main.cf file as follows:
relayhost =
mynetworks_style = subnet <- this means that hosts on the same subnet can send mail - if your network setup is different then you'll need to change this.

Then Thunderbird could connect to the VM and it sends mail fine.

---

