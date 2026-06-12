---
title: "dns mail server"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-09-08
Hi,

I still am trying to get my postfix mail server to send mail to my hotmail account.

I run a email check tool and it tells me the following.  Anyone have a clue on how to fix it?  

Thanks!

Step 1:  Try connecting to the following mailserver:
         [ERROR: A CNAME appeared in the MX records; this is not valid (per RFCs 974 "Minor Special Issues" section, and 1034 section 3.6.2.
          Mailservers are not required to send E-mail to smtp.secureserver.net.]
CNAME(s) I found are: [smtp.secureserver.net. CNAME smtp.where.secureserver.net.]

---

### Post by CaptainInsaneO on 2007-09-13
Try removing the CNAME file and putting in a connector to Hotmail's servers.

---

