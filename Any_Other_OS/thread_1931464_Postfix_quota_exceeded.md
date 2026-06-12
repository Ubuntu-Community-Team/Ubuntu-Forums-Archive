---
title: "Postfix quota exceeded?"
date: 2012-02-25
forum: Any Other OS
---

### Post by Nailox on 2012-02-25
Hi. Host is Debian 6 32bit
Server is crashing and is fixed after reboot only to crash again. In mail.log i get this error
> 
postfix/postdrop[5342]: warning: mail_queue_enter: create file maildrop/748382.5342: Disk quota exceeded 
My ISP is not setting any quota
Disk is 23% usage
I havent set any quota for the mailbox in main.cf of postfix
repquota -avug doesnt give any output


Any ideas ?

---

### Post by mörgæs on 2012-02-26
Moved to Other OS/distro talk.

---

### Post by lisati on 2012-02-26
> **Nailox said:**
> Hi. Host is Debian 6 32bit
Server is crashing and is fixed after reboot only to crash again. In mail.log i get this error

[COLOR="Red"]My ISP is not setting any quota[/COLOR]
Disk is 23% usage
I havent set any quota for the mailbox in main.cf of postfix
repquota -avug doesnt give any output


Any ideas ?

I don't think it's an issue with your ISP. Do you have disk quotas set up for users on your server?

---

