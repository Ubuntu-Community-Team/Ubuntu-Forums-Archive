---
title: "Evolution configuration problems"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-22
I have configured Evolution as my e-mail client, but cannot receive or send e-mail. Errors included below. Any help is appreciated.  I received the following errors... ** Error while performing operation.  RCPT TO  failed: Requested action not taken: mailbox name not allowed**  AND...  **Unable to connect to POP server mail.vistasense.com. Error sending password: -ERR authorization failed  Please enter the POP password for randy.bradshaw on host mail.vistasense.com**  Should I use IMAP instead of POP3?  I also attached a screen shot.  Randy

---

### Post by ymp77 on 2007-08-01
did somebody resolve this problem? plz help

---

### Post by crazypiglady on 2007-08-01
Make sure the mailto and from addresses are the same.  The problem I had (producing the exact error messsage as rbradshaws screenshot) was that I didn&#8217;t have pop3 and SMTP access from my webmail. I ended up sending mail through a different provider (bluebottle) that allowed SMTP. Basically its not evolution that's the problem it&#8217;s the provider that wants people using it to see its web page (and advertising space).  

Solution: to start with make sure your provider allows pop3/SMTP access (check their site) 
Then, using edit/ preferences/ edit account, make sure your email address on the identity tab matches the server and username on the sending email tab. This should work, I&#8217;m pretty sure the server and username on the receiving (POP)  mail doesn't need to match but for a test you could make all the mentions of servers match. I currently use one webmail account (which people know me by) to receive mail and bluebottle.com (which will allow SMTP) to send mail. This isn't ideal as my outgoing mail has a different address  -  but it works. Let me know if this helps. A more ideal solution would be to change my account and have people know me at bluebottle.com 

Ps I am assuming you&#8217;ve tried the password endless times.

---

