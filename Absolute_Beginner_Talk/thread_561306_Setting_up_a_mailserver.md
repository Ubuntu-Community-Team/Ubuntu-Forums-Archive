---
title: "Setting up a mailserver"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by kuhsay on 2007-09-27
Current situation:
We use multiple laptops throughout the day and travel.  We have a webhost that offers POP3, IMAP, and webmail.

Problem:
Email is not synced when using POP3.  My boss does not want to store email on our webhost's servers because of privacy concerns and space reasons (over time he's accumulated >2gb of email!).

Solution?:
I want to set up an IMAP mailserver that downloads all of our email from our webhost.  It doesn't need to do any of the sending, it just needs to be able to get our email and allow us to access it from any machine.  We'll need to access this from outside our office as well.  It should also store copies of sent email.

What do I need to do to get this working, or is there a better/easier way to solve my problem?

---

### Post by hyper_ch on 2007-09-27
you have IMAP at your webhost, why do you want an own server then?

---

### Post by kuhsay on 2007-09-27
Boss does not want to store email on our webhost's servers because of privacy concerns and space reasons.

---

### Post by mutation on 2007-09-27
not ubuntu related but try [http://smeserver.org](http://smeserver.org) it based on fedora and will do what you want it to do, and its free
:)

---

### Post by hyper_ch on 2007-09-27
well, in that case I would get an own domain and dedicated IP address and setup full fledged email server... I can point howtos for that if you want to...

But having to fetch all mails from your webhost and store them at another location but sending is done again through the webhost, that sounds very complicated and I see no purpose in that.

---

### Post by kuhsay on 2007-09-27
hyper_ch: How hard is it to set one up?  I've never set up a mail server before and I am somewhat of a linux noob.  The most complicated thing I've done so far has been installing bugzilla.

mutation: thanks for the link.  I'm downloading the VM torrent now.

---

### Post by CaptainInsaneO on 2007-09-27
I'm a net admin for the U.S. Government, we use Windows Server to set up our mail servers and it's no walk in the park when you first learn how to do it. You have to learn about things like MX records, connectors, mailboxes, etc. There's a lot of information you have to know to do it.

Here's a link to get you started though: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by hyper_ch on 2007-09-28
Well,

I'd recommend to go over to [http://www.howtoforge.com](http://www.howtoforge.com) and have a read at the perfect Debian Etch howto. This will not only install a fully functional email server but also a required DNS server. The whole ISP config setup would probably be a bit too much overhead but it's a starting point.

Another howto is this:  [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)

However with that there's still the question of a DNS server that needs to setup. You can't really operate a mailserver without domain and fixed IP - some Domain registrars allow you to set the DNS records at their place... if that is the case, then you only need to able to resolve other domains.

---

