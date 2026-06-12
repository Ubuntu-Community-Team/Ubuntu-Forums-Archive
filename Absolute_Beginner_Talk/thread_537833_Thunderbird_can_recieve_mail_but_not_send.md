---
title: "Thunderbird can recieve mail but not send"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-08-29
I have two outgoing servers for my mail: one is to localhost, where YPops! relays it to my yahoo account. That works perfectly. The other is a POP/SMTP setup to my school's mail server. That doesn't. I can receive mail fine, but sending it is a no-go. I have been trying to troubleshoot for a while, and have come up with the following info:

1) The server settings are correct - I have triple checked them (and are set to the right address)
2) Various ports do nothing to relieve the problem 
3) A fresh install also does nothing: this also showed me that the second server option does not interfere with the problematic one
4) When I try to send, it attempts to connect until a server time out.
5) My firewall (as seen through firestarter) is not blocking the connection

Any other diagnostics or help are appreciated.

---

### Post by wireddad on 2007-08-29
How do you connect to the net?  For sending I have to use the smtp of my internet provider.

---

### Post by rouge568 on 2007-08-29
Via wireless. (from my neighbors) I shouldn't have to set it up via connection, though; you are probably using email set up by your ISP.

On another note, I will be getting help from school tech support when I get there. I would like to have this fixed first, however. Also, to add to the list:

6) The school server works and can otherwise send and receive mail

---

### Post by quantumcheese on 2007-08-29
Many ISPs block port 25 (default smtp port) by default except through their own smtp server.  Some ISPs will remove this block for you if you ask.

---

### Post by rsambuca on 2007-08-29
It sounds to me like you haven't got the Outgoing Server (SMTP) options set correctly.  If you open Thunderbird and go to Edit -> Account Settings -> Outgoing Server (SMTP) at the bottom.

---

### Post by rsambuca on 2007-08-29
> **rouge568 said:**
> Via wireless. (from my neighbors :)) 

That is illegal in many places.

---

### Post by kellemes on 2007-08-29
> **rsambuca said:**
> That is illegal in many places.

And it should be..

---

### Post by rouge568 on 2007-08-29
I am not using port 25, though I have tried it. I am using port 465, which is the Thunderbird default. Yes, I am sure that I have my SMTP setting right.
(edit: ooops! accidental double-post)

---

### Post by rouge568 on 2007-08-29
I am not using port 25, though I have tried it. I am using port 465, which is the Thunderbird default. Yes, I am sure that I have my SMTP setting right.

---

### Post by tagginannie on 2007-08-29
> **rouge568 said:**
> I have two outgoing servers for my mail: one is to localhost, where YPops! relays it to my yahoo account. That works perfectly. The other is a POP/SMTP setup to my school's mail server. That doesn't. I can receive mail fine, but sending it is a no-go. I have been trying to troubleshoot for a while, and have come up with the following info:

1) The server settings are correct - I have triple checked them (and are set to the right address)
2) Various ports do nothing to relieve the problem 
3) A fresh install also does nothing: this also showed me that the second server option does not interfere with the problematic one
4) When I try to send, it attempts to connect until a server time out.
5) My firewall (as seen through firestarter) is not blocking the connection

Any other diagnostics or help are appreciated.




You could try ports 26 or 587  but some ISP's are starting to block the latter one now because of Spammers. OR, you could open Gmail account. Gmail has a nice feature that lets you send mail from any of your other email accounts and your mail will look like it came from your Yahoo account or from your school email address or any other email address that you have. 

One questions why are you using "YPops" ?? you can get free POP service from Yahoo! if you open an account outside of the U.S.

---

### Post by rouge568 on 2007-08-29
Sorry - clarification. I am not having any issues with my yahoo account - it is the other that is giving me trouble. I use ypops because i want to keep my current address, and yahoo isn't letting me use POP.

---

### Post by stevebakerj on 2007-08-29
> **rouge568 said:**
> I am not using port 25, though I have tried it. I am using port 465, which is the Thunderbird default. Yes, I am sure that I have my SMTP setting right.

You might have your smtp settings right, but is it your neighbors ISP's smtp server you are using to send? Most if not all ISP's only allow you to use their smtp server to send.

It is also illegal in the UK to use someones else's connection as recently published in most of the national papers, unless of course you have there permission then they could be breaking the law by letting you use their connection without informing their ISP.

---

### Post by irish_flu on 2007-08-29
Your school's SMTP server probably is not set up to "relay" messages sent from outside the school network (for security reasons); the SMTP server at your ISP will be able to pass any mail originating on their network, regardless of what the account domain is.

Are you set up to authenticate to the school's SMTP server?  If so, that will likely negate what I said.

---

### Post by rouge568 on 2007-08-29
As I am not yet as school, most likely not. You're probably right about that: I will wait to try on their network when I get there.

---

