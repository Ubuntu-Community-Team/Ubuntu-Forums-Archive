---
title: "Email from command line"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-21
jordan@Jorcomp:~$ mail
"/var/mail/jordan": 11 messages 5 new
 R   1 Mail Delivery Syst Tue Nov 20 13:07  38/1254  Mail delivery failed: ret
 R   2 Mail Delivery Syst Tue Nov 20 13:07  37/1229  Mail delivery failed: ret
 R   3 Mail Delivery Syst Tue Nov 20 13:08  37/1224  Mail delivery failed: ret
 R   4 Mail Delivery Syst Tue Nov 20 13:11  37/1225  Mail delivery failed: ret
 R   5 Mail Delivery Syst Tue Nov 20 20:00  41/1446  Mail delivery failed: ret
 R   6 Mail Delivery Syst Tue Nov 20 20:07  41/1446  Mail delivery failed: ret
>N   7 Mail Delivery Syst Wed Nov 21 18:52  38/1408  Mail delivery failed: ret
 N   8 Mail Delivery Syst Wed Nov 21 18:52  38/1409  Mail delivery failed: ret
 N   9 Mail Delivery Syst Wed Nov 21 18:54  39/1430  Mail delivery failed: ret
 N  10 Mail Delivery Syst Wed Nov 21 18:56  39/1424  Mail delivery failed: ret
 N  11 Mail Delivery Syst Wed Nov 21 19:03  38/1397  Mail delivery failed: ret
& 
From: Mail Delivery System <Mailer-Daemon@jorcomp>
To: jordan@jorcomp
Subject: Mail delivery failed: returning message to sender
Date: Wed, 21 Nov 2007 18:52:38 -0800

This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  [email]kksparks@uvic.ca[/email]
    SMTP error from remote mail server after RCPT TO:<kksparks@uvic.ca>:
    host smtpx.uvic.ca [142.104.5.91]: 553 5.1.8 <kksparks@uvic.ca>... Domain of
 sender address jordan@jorcomp does not exist

------ This is a copy of the message, including all the headers. ------

Return-path: <jordan@jorcomp>
Received: from jordan by Jorcomp with local (Exim 4.67)
        (envelope-from <jordan@jorcomp>)
        id 1Iv2AS-0001re-HS
        for [email]kksparks@uvic.ca[/email]; Wed, 21 Nov 2007 18:51:52 -0800



is the error i get when i try
mail [email]kksparks@uvic.ca[/email]
(message here)

however, this seems very odd because i have recieved messages using the command line before.  I don't know what the problem is here.
anyone experienced with this process able to lend a hand?

Thanks :)

---

### Post by fastTalker on 2007-11-22
The mail server is rejecting your email because the sender address field is jordan@jorcomp.  That's not a real email address.  jorcomp is not a real domain.  So it thinks your email is not legit (spam, etc.)  mail is using your local mail server which is only setup to work locally.

---

