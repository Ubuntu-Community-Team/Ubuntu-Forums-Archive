---
title: "hotmail plus and evolution"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by cheetah_thompson on 2008-01-06
I'm new to Linux/Ubuntu as of yesterday. I am trying to get Evolution configured to download email from my Hotmail Plus account. 

A few months back Microsoft allowed pop access to hotmail plus accounts. But I have been unsuccessful getting these settings to work and wondered if anyone else knew what I was doing wrong. The error message I get is:

When trying to receive mail the error is:

"Error While Fetching Mail
Failed to read a valid greeting from POP server pop3.live.com"

When trying to send mail the error is:
"Error while performing operation
MAIL FROM command failed: Must issue a STARTTLS command first"

-----------------------------------------------------------------------------------
Here is a summary of the information I have set under Account Editor:
-----------------------------------------------------------------------------------

[Identity]
Name: [email]myemailaddress@hotmail.com[/email]
Full Name: (my full name)
Email Address: [email]myemailaddress@hotmail.com[/email]

[Receiving Email]
Server Type: POP
Server: pop3.live.com:995
Username: [email]myemailaddress@hotmail.com[/email]
Use secure connection: No encryption
Authentication Type: Password
Remember password

[Receiving Options]
Automatically check for new messages every 10 minutes

[Sending Email]
Server Type: SMTP
Server: smtp.live.com:25
Server requires authentication
Use Secure Connection: No encryption
Type: PLAIN
Remember password
Username: [email]myemailaddress@hotmail.com[/email]

[Defaults]

[Security]
(Nothing set)

Thanks in advance.

---

### Post by blueridgedog on 2008-01-06
Try it without the @hotmail.com part in your username under the sending and receiving sections.

---

### Post by dcstar on 2008-01-06
> **cheetah_thompson said:**
> I'm new to Linux/Ubuntu as of yesterday. I am trying to get Evolution configured to download email from my Hotmail Plus account. 
.........
Is this any use:

[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

---

### Post by jken146 on 2008-01-06
> **cheetah_thompson said:**
> I'm new to Linux/Ubuntu as of yesterday. I am trying to get Evolution configured to download email from my Hotmail Plus account. 

A few months back Microsoft allowed pop access to hotmail plus accounts. But I have been unsuccessful getting these settings to work and wondered if anyone else knew what I was doing wrong. The error message I get is:

When trying to receive mail the error is:

"Error While Fetching Mail
Failed to read a valid greeting from POP server pop3.live.com"

When trying to send mail the error is:
"Error while performing operation
MAIL FROM command failed: Must issue a STARTTLS command first"

-----------------------------------------------------------------------------------
Here is a summary of the information I have set under Account Editor:
-----------------------------------------------------------------------------------

[Identity]
Name: [email]myemailaddress@hotmail.com[/email]
Full Name: (my full name)
Email Address: [email]myemailaddress@hotmail.com[/email]

[Receiving Email]
Server Type: POP
Server: pop3.live.com:995
Username: [email]myemailaddress@hotmail.com[/email]
Use secure connection: No encryption
Authentication Type: Password
Remember password

[Receiving Options]
Automatically check for new messages every 10 minutes

[Sending Email]
Server Type: SMTP
Server: smtp.live.com:25
Server requires authentication
Use Secure Connection: No encryption
Type: PLAIN
Remember password
Username: [email]myemailaddress@hotmail.com[/email]

[Defaults]

[Security]
(Nothing set)

Thanks in advance.

The error message you get and the settings you gave suggest to me that you need to choose TLS encryption.

---

### Post by sooperspook on 2008-02-19
I'm having the same exact problem.

Anyone have any luck fixing it?

---

