---
title: "Evolution Help"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2006-02-12
Hello all,

Can I configure evolution to retrieve mails from mail servers like yahoo and others from my account? If yes, how do I know what parameters to be given while setting it up?

Thanks in advance.

Vijay

---

### Post by Ted D. on 2006-02-12
Yes, Go to GMail etc. It explains what settings are needed in various apps. It doesn't deal with Evolution exactly but there is enough info on other apps to get you going. 
Ted D.

---

### Post by Klaidas on 2006-02-12
I tried connecting evolution and gmail, I can SEND emails, but I can't get them from the GMAIL server. 
No error messages too :/

---

### Post by bastya_elvtars on 2006-02-12
GMail POP3 servrer addy: pop.gmail.com

Make sure you have SSl enabled for POP (I don't know Evolution). No secure auth!

---

### Post by cstudent on 2006-02-12
[QUOTE=Klaidas]I tried connecting evolution and gmail, I can SEND emails, but I can't get them from the GMAIL server. 
No error messages too :/[/QUOTE]


In the Evolution settings tab for Receiving Email:

Server type: POP
Server: pop.gmail.com
Username: [email]yourname@gmail.com[/email]
Use secure connection: ALWAYS
Authentication type: Password


Under Sending Mail tab:

Server type: SMTP
Server: smtp.gmail.com
Server requires authentication: checked
Use secure connection: ALWAYS
Authentication type: Plain
Username: [email]yourname@gmail.com[/email]


These are the settings I have and it all works. As far I as know, Yahoo and Hotmail do not work through Evolution. Someone who uses those services may have found a solution however.

---

### Post by Klaidas on 2006-02-12
Thanks, I'm gonna chech if my mail setting are right

---

### Post by Klaidas on 2006-02-12
Thank you, it works! :)

My mistake was that instead of [email]myname@gmail.com[/email] I used 'myname' :)

---

### Post by vijayanand_sodadasi on 2006-02-16
Thanks a lot for your replies.

Vijay

---

