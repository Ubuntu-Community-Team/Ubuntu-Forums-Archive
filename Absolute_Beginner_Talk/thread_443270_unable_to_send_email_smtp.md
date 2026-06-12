---
title: "unable to send email smtp"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by mikeymouse on 2007-05-14
I have already submitted this in the general help but I could not get any response, here's hoping for the beginners group.
I cannot send mail using evolution or thunderbird . I can receive mail but cannot send.
When i try to send it says 'connection to smtp server failed', actually I get the same error message even when not online and try to send email.
Does anyone know what is required to be able to send email using a dialup connection?
My configuration of smtp is correct, as i have setup many systems to send email. It is only in Ubuntu that i have this problem..
Any and all help would be appreciated.
thanks mikeymouse

---

### Post by heimo on 2007-05-14
This is not exactly Absolute Beginner stuff, so you earn couple Guru points by debugging your smtp this way. Try telnetting to the smtp server and talking smtp to it by yourself. Type:
```
telnet smtp.example.com 25
```where smtp.example.com is your ISPs smtp server (or what-ever smtp server you should be using to send mail)

You should get something like: ```
Trying 192.168.0.1...
Connected to smtp.example.com.
Escape character is '^]'.
220 smtp.example.com ESMTP Postfix

```If that works, you can try giving it:
```
helo example.com
```And it should greet you with something like:
```
250 smtp.example.com
```Quit the connection with
```
quit
```Does it work?

---

### Post by darkworld on 2007-05-14
I tried it just out of curiosity and it didnt work. But my smtp does work. 

is the helo a typo? theres no man for it? if its hello which i suspect then im missing a package. Interesting stuff though.

---

### Post by heimo on 2007-05-14
> **darkworld said:**
> I tried it just out of curiosity and it didnt work. But my smtp does work. 

is the helo a typo? theres no man for it? if its hello which i suspect then im missing a package. Interesting stuff though.

No that's helo with one L (ehlo should work too). And it's not command line command, but a SMTP command that you send through telnet to SMTP server. Were you able to establish connection to your smtp server? Can you ping it? (ping smtp.example.com)

---

### Post by darkworld on 2007-05-14
> **heimo said:**
> No that's helo with one L (ehlo should work too). And it's not command line command, but a SMTP command that you send through telnet to SMTP server. Were you able to establish connection to your smtp server? Can you ping it? (ping smtp.example.com)

Connected to smtp.ntlworld.com.
Escape character is '^]'.
220 ESMTP server ready
helo ntlworld.com
250 aamtaout03-winn.ispmail.ntl.com
quit
221 aamtaout03-winn.ispmail.ntl.com ESMTP server closing connection
Connection closed by foreign host.

yes that worked the problem i had was that i wasnt root on the command line, doh! something else ive learned.

---

### Post by heimo on 2007-05-14
Strange. It shouldn't require root rights. Could you retry as a normal user? If that doesn't work, maybe we have a clue to the real problem. At least we now know that network connection to your smtp server works.

What's the error message (if any) that you get when trying to send mail from email program? Have you tried other programs (thunderbird/evolution...)?

EDIT: I mixed you two, darkworld and mikeymouse.

---

### Post by mikeymouse on 2007-05-14
Yes i can ping my smtp server.
 The trouble is the email programs do not connect to the smtp server. 
 
thanks mikeymouse

---

### Post by heimo on 2007-05-14
> **mikeymouse said:**
> Yes i can ping my smtp server.
 The trouble is the email programs do not connect to the smtp server. 
 
thanks mikeymouse

Oh. I see now that I mixed darkworld and you mikeymouse. Could you also try the telnetting to smtp trick? And how about other mail clients?

---

### Post by darkworld on 2007-05-14
> **mikeymouse said:**
> Yes i can ping my smtp server.
 The trouble is the email programs do not connect to the smtp server. 
 
thanks mikeymouse

surely this is a setting problem especially if you can hit the server from command line. Cant be a corrupt package if you have tried others. the only other thing I can think of is firewall rules? but hey im a newbie too!

---

