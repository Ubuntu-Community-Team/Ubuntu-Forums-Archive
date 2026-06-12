---
title: "Email Setup Questions"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-03-29
I'm trying to set up a small email system for a classroom of 10 XP computers, which are connected in a P2P networking arrangement. We do not want students to be able to send mail outside the classroom -- anything they do wrong should just give them an "undeliverable" message. The classroom machines have names, and are arranged into a XP Workgroup, but their IP addresses are assigned by DHCP.

I've got Postfix running, and I can mail messages to myself from myself on Ubuntu. But now I don't know what to do next. I'm **way** too ignorant to be doing this so ...

1) Can anyone recommend a simple overview of what has to be done? I've tried reading about networking but it everything I have found so far is so complex it makes my brain glaze over. 

Other outstanding questions.

2) Do I have to set up a domain?

3) Do I have to set up a primary and secondary server?

4) Do I have to set up an address for another server to handle requests which the local one cannot?

5) Do I have to protect the server from outside influences, beyond the Linus firewall installed by Ubuntu?

6) Do I have to make changes in the firewall so that students machines can use the email services?

See what I mean? I'm way too ignorant to be doing this, but that's what we need to do, and nobody else is even close. 

TIA

Gary

---

### Post by nixclusive on 2007-03-30
all you need to do is edit the file /etc/postfix/main.cf
check out the directive 'mydestination' in postconf(5)```
man 5 postconf
```

---

### Post by nixclusive on 2007-03-30
3) Do I have to set up a primary and secondary server? -- only if you intend to build a reduntat fault tolerant system. For a 'school' of ten computers (!) I don't think that would be necessory.

4) Do I have to set up an address for another server to handle requests which the local one cannot? -- depends on the actual load on the local server itself.

5) Do I have to protect the server from outside influences, beyond the Linus firewall installed by Ubuntu? -- Are you thinking of the default firewall in a newly installed Ubuntu sytstem? Postfix can be configured to accept connections from a fixed domain. However, firewalling your smtp ports on external interfaces is certainly a good idea.

---

### Post by nixclusive on 2007-03-30
6) Do I have to make changes in the firewall so that students machines can use the email services? -- even that depends on your current firewall configuration.

---

### Post by nixclusive on 2007-03-30
minimally -- all of that can be achieved (to that effect) from the single file /etc/postfix/main.cf and (ok another file) maybe /etc/postfix/master.cf

good luck...

---

### Post by Gary Nored on 2007-03-30
Thanks for the suggestions. I'm studying the conf file man page now. 

Still wish there was something approachable I could read so that I could understand this better ...


Gary

---

### Post by Mr. C. on 2007-03-30
Setting up postfix for your needs is not too difficult.

1) Let's do this last...  See comments below
2) No.  Since your machine is on a LAN, you can name it what you will.  You will configure postfix with a name.

3) Just one server is fine.

4) I read that you wanted mail to stay internal.  If this is correct, no need for further relay.

5) When you configure postfix, you will configure it to accept email from your subnet only.  Since it is not going to relay outside, there is no concern.

6) Enable port 25 to pass.

Since you already have postfix running, lets take it from where you are now.  Please show output from
```

postconf -n
```

This will tell us the changes made to postfix that are not defaults.  Once I see that, I'll further assist with modifications.

I presume you have some way to ensure that students do not configure they systems to send mail offsite (or they do not have internet access).

MrC

---

### Post by nixclusive on 2007-03-31
Ok dude you've got an expert on this one now.. good luck.

---

### Post by Gary Nored on 2007-04-04
Many thanks. Here is the output from postconf:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = loopback-only
mailbox_size_limit = 0
mydestination = lcnet70, localhost.localdomain, localhost
myhostname = lcnet70
mynetworks = 127.0.0.0/8, 10.100.15.25/100
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes


In answer to other questions, students do have access to the internet, but they are just learning to use computers and are working under close supervision. Also, they work in a special classroom account that other visitors do not have access to.

Gary

---

### Post by Mr. C. on 2007-04-04
Hello Gary,

To configure postfix to accept mail from your LAN, but not forward externally, you can use a transport map in main.cf:

main.cf:
   myhostname = lcnet70.local
   mydomain = lcnet70.local
   transport_maps = pcre:/etc/postfix/transport

transport:
    /@lcnet70.local$/     local:
    /./                 error:Email forwarding disabled

This will allow local email to the lcnet70.local domain, but return an error otherwise.

You will need to remove or comment out the inet_interfaces = loopback-only from main.cf, otherwise, your server won't be listening from requests from anything other than its loopback internal interface.

Unless you have the latest postfix, you will need to have at least one dot in mydomain; this is why I added .local.

I would also recommend disabling TLS (smtpd_use_tls = no) in main.cf; you likely do not need it for your local LAN, and it will ease configuration for your students.  After you have everything working correctly, if you want TLS enabled, you can do so.

The network 10.100.15.25/100 in the line: 

mynetworks = 127.0.0.0/8, 10.100.15.25/100

doesn't make sense; you're specifying a 100-bit network.  If you were trying to specify IPs .25 to .100, you'll have to use a combination of single IPs and a range of IPs which looks like:
10.100.15.25/32
10.100.15.26/31
10.100.15.28/30
10.100.15.32/27
10.100.15.64/27
10.100.15.96/30
10.100.15.100/32

You likely just want:

mynetworks = 127.0.0.0/8, 10.100.15.0/24

MrC

---

### Post by Gary Nored on 2007-04-17
Thanks again for your help. 

I've edited main.cf as you said, with one possible exception. 

I didn't understand your example of specifying a range of IPs from .25 to .100.

I believe (but I will have to find out for sure) that our machines all live in the range of .50 to .80. Do I change the mynetworks line to read 10.100.15.50/80??

Sorry about the long delays here -- I have to snatch time in moments between ....

Gary

---

### Post by Mr. C. on 2007-04-17
You are thinking that the /xx (as in your 10.100.15.50/80 example) means range, as in 50 to 80.  It does not work that way.  The range 10.100.15.50 to 10.100.15.80 must be specified as multiple addresses:

10.100.15.50/31
10.100.15.52/30
10.100.15.56/29
10.100.15.64/28
10.100.15.80/32

so mynetworks would be:

```
mynetworks = 127.0.0.0/8 10.100.15.50/31 10.100.15.52/30 10.100.15.56/29 10.100.15.64/28 10.100.15.80/32
```.

MrC

---

### Post by Gary Nored on 2007-04-23
Hmmm. I thought you hadn't found time to answer, but when I try to Post it shows up in the thread. I assume the numbers 31,30,29 ... 32 isn't literal; ie, I can use any series of numbers that have meaning here?

Gary

---

### Post by Mr. C. on 2007-04-23
No, the /N numbers DO have meaning.  They are a standard notation used to indicated how many bits in the IP address are used for the network (thereby leaving 32-N indicates how many bits are used for the host part of the IP).

If you want the range you indicated, you must use the mynetworks string I provided for you in the code box.

If you want a more thorough overview of how this works, read Week 2's Coursework "Data Delivery" at: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

