---
title: "Active Directory on Fiesty"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Jenillaroma on 2007-05-01
I am having a problem with : kinit [email]domain_admin_account@DOMAIN.INTE[/email]RNAL.  When I put that in it comes up with  kinit: krb5_get_init_creds: Client (domain_account@DOMAIN.INTERNAL) unknown.  I can't figure out where I went wrong.  Can anyone help me please!!!!!!!!  Thank you in advanced.:)

---

### Post by lamalex on 2007-05-01
are you trying to connect to a window AD server or an openldap server? are you sure that account even exists? that error looks like the account just doesn't exist or your login syntax is wrong

---

### Post by Jenillaroma on 2007-05-01
I am trying to connect to a Windows box.  And yes my account is in there.  And I did have a ticket at one point but I still got the same error and now I don't get a ticket.  Does that make sense??

---

