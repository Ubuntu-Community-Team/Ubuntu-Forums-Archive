---
title: "Problem Installing Postfix"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Akebono on 2007-02-07
Hello all:

I am trying to install Postfix on Ubuntu 6.10 (Edgy Eft). I run "sudo apt-get install postfix" and I get the Postfix configuration screen. I go to "OK" and select "Internet Site". I then enter my mailname of abcdef.com and "OK". At this point, I get the following message:

Warning: NewLine present in parameters passed to debconf.
This will probably cause strabge things to happen!

And it does.....all I get is the following repeated over and over:

hostname: Unknow host


My ISP has my domain name and MX record point to my static IP as follows:

Domain Name: abcdef.com
MX Record: Mail.abcdef.com

The computer that Ubuntu is setup on has a computer name of MYSERVER.

What should my mailname be?

abcdef.com
mail.abcdef.com
MYSERVER.abcdef.com

Is this what is causing the problem or is it something else?

Thank you very much for any assistance!

---

### Post by kidders on 2007-02-07
Hi there,

The best thing to do might be to post your /etc/postfix/main.cf ... or maybe attach it to your next post ... it could be a bit long! I'll take a quick look and see if the configurator did something silly.

---

### Post by Akebono on 2007-02-08
Hello:

Unfotunately, I don't believe that Postfix actually finished installing because of this error. I don't have an /etc/postfix/main.cf on the system.

Thanks.

---

### Post by kidders on 2007-02-08
Hmmm... it may be that it installed, but never got around to configuring itself. See if "main.cf.dist" turns up at /usr/share/postfix. If you find it, you can copy it to /etc/postfix/main.cf.

It's quite a large file, that contains explanations of many configuration directives for postfix, much of which you can delete. What you want to end up with is something like the following, but (even if your postfix *had* successfully configured itself), it's important to make sure that things like relay control are sensible, so your server won't get hijacked!

```
smtpd_banner                          = $myhostname ESMTP $mail_name
soft_bounce                           = no
smtpd_delay_reject                    = yes

mynetworks                            = 192.168.1.0/24 127.0.0.1
myhostname                            = mail.hostname.com

mydestination                         = hostname.com
mydomain                              = hostname.com
myorigin                              = hostname.com

smtpd_require_helo                    = yes
disable_vrfy_command                  = yes

queue_directory                       = /var/spool/postfix
command_directory                     = /usr/sbin
daemon_directory                      = /usr/lib/postfix
mail_owner                            = postfix

unknown_client_reject_code            = 550
unknown_local_recipient_reject_code   = 550
smtpd_client_restrictions             = permit_mynetworks

sendmail_path                         = /usr/sbin/sendmail
newaliases_path                       = /usr/bin/newaliases
mailq_path                            = /usr/bin/mailq
setgid_group                          = postdrop
html_directory                        = no
manpage_directory                     = /usr/share/man
sample_directory                      = /etc/postfix
readme_directory                      = /usr/share/doc/postfix

default_destination_concurrency_limit = 2
alias_maps                            = hash:/etc/postfix/aliases
alias_database                        = hash:/etc/postfix/aliases
local_recipient_maps                  = hash:/etc/postfix/aliases
local_mailbox_maps                    = $alias_maps

home_mailbox = .maildir/
luser_relay = root
```

---

### Post by Akebono on 2007-02-08
Hi, Kidders:

I am not finding that file in /usr/share/postfix. I have just reinstalled Postfix and left the configuration information to "No configuration". I now have Postfix in /etc/Postfix and there is a main.cf.dist file in /usr/share/postfix. However, I do not have a main.cf in /etc/Postfix, just a master.cf. Sorry for all the trouble.

---

### Post by kidders on 2007-02-08
> **Akebono said:**
> Sorry for all the trouble.
No trouble!

> **Akebono said:**
> I am not finding that file in /usr/share/postfix. I have just reinstalled Postfix and left the configuration information to "No configuration".Good move. :-)

> **Akebono said:**
> I now have Postfix in /etc/Postfix and there is a main.cf.dist file in /usr/share/postfix. However, I do not have a main.cf in /etc/Postfix, just a master.cf.Yep, that's what to expect. Ubuntu has not attempted to configure postfix for you. You've lost very little though, since I would always very strongly recommend going through main.cf with a fine tooth comb anyway ... even if Ubuntu *had* written one.

The first thing to do is copy /usr/share/postfix/main.cf.dist to /etc/postfix/main.cf. Then you can set about rewriting it. In my last post, I wanted to try to give you an impression of what bits of it you'd be most likely to need ... anything you don't think you'll want can be deleted, so you should be left with a nice, short file. Once you're done, try **sudo /etc/init.d/postfix start** and see what happens.

If it starts up, be sure not to leave it up for too long, unless you're sure people outside your local network can't use it to do inappropriate things. (Let me know if you need help there.)

---

### Post by Akebono on 2007-02-08
Thanks, kidders. I will try that out and let you know the outcome.

---

### Post by kidders on 2007-02-08
> **Akebono said:**
> Thanks, kidders. I will try that out and let you know the outcome.No problem. I'm happy to walk you through the setup in more detail over IM, if you need a hand.

---

