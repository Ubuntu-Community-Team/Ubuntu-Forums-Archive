---
title: "[SOLVED] PostFix -- only accepts email like this:  Carl@mail.domain.com"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-04-04
I installed PostFix email server on my Ubuntu Server.

It will receive email if I send email to my srever like [email]Carl@mail.domain.com[/email] but I get a "loops back to myself" error if I send like [email]Carl@domain.com[/email]


Any ideas?

Thanks

Carl

---

### Post by cwmoser on 2008-04-04
Could this be a problem with my MX record?

First time for me to setting one up.

Thanks

Carl

---

### Post by mtbeedee on 2008-04-04
what is your MX record like and what is the config of postfix?  the MX record should just have an MX for probably both domain.com and mail.domain.com that points to your machine.

Postfix should be configured to accept mail for both domains.  I am not too familiar with its config though.

---

### Post by cwmoser on 2008-04-04
When I send outbound email, it shows like [email]root@Cerant.com[/email] or [email]carl@Cerant.com[/email].  

In order for me to receive email, the email address has to be like [email]carl@mail.Cerant.com[/email].  If I send email like [email]Carl@Cerant.com[/email], it comes back with the  "loops back to myself" error.

Carl

---

### Post by cwmoser on 2008-04-04
My PostFix server can receive email if I address it to:  [email]Carl@mail.Cerant.com[/email].



But, I get the following returned back if I send email to [email]Carl@Cerant.com[/email]

Reporting-MTA: dns; mail.cerant.com
X-Postfix-Queue-ID: 238481D7479E
X-Postfix-Sender: rfc822; [email]carl@carteblanc.com[/email]
Arrival-Date: Fri,  4 Apr 2008 17:07:38 -0400 (EDT)

Final-Recipient: rfc822; [email]Carl@cerant.com[/email]
Original-Recipient: rfc822;Carl@cerant.com
Action: failed
Status: 5.4.6
Diagnostic-Code: X-Postfix; mail for mail.Cerant.com loops back to myself

			email message attachment, "Undelivered Message"


Any insight into this is appreciated.

Carl

---

### Post by cwmoser on 2008-04-05
I solve this problem.  Thought I would document it in case anyone else had a similar problem.

This was my first time setting up PostFix and I must have entered some configuration information for the virtual server configuration.  PostFix documentation clearly warns about this.

So, my solution was to edit /etc/postfix/main.cf file and comment out the virtualize configurations.  

This is what I did ...

#virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
#virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
#virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
#virtual_mailbox_base = /home/vmail
#virtual_uid_maps = static:5000
#virtual_gid_maps = static:5000
#transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
#virtual_create_maildirsize = yes
#virtual_mailbox_extended = yes
#virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
#virtual_mailbox_limit_override = yes
#virtual_maildir_limit_message = "The user you are trying to reach is over quota."
#virtual_overquota_bounce = yes
#proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

... now my PostFix server will accept email like  [email]Carl@Cerant.com[/email].

Carl

---

