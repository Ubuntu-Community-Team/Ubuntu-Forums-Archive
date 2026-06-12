---
title: "Cannot Send Email"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by cazmatazzz on 2007-12-25
HI. 

Recently installed xubuntu, got everything working except for the fact that I am not able to send ANY emails. 

I have three different accounts, [email]xxx@zonnet.nl[/email], [email]xxx@hotmail.com[/email] and [email]xxx@gmail.com[/email] all of which are able to receive email in three different programs (evolution, kmail and thunderbird) but none of them are able to send emails. i know for sure that my hotmail and gmail accounts are correctly configured. for the zonnet account i am not 100% sure. nevertheless i cannot get any email account to send an email. 

can somebody please help me? I have tried almost everything for two days and cannot seem to find an answer. 

this tells me the port is working:

charlotte@charlotte:~$ telnet smtp.xs4all.nl 25
Trying 194.109.6.51...
Connected to smtp.xs4all.nl.
Escape character is '^]'.
220 smtp-vbr7.xs4all.nl ESMTP Sendmail 8.13.8/8.13.8; Tue, 25 Dec 2007 13:59:09 +0100 (CET)

---

### Post by Phurious on 2007-12-25
Have you tried switching the SMTP server you are using?  Try using gmail's SMTP; just remember it requires you to login to send mail.

---

### Post by cazmatazzz on 2007-12-25
for gmail i used the gmail smtp with login (with full username and password) for hotmail i used the special settings (smtp 127.0.0.1:2500 and special hotway settings) for the zonnet account i did use the xs4all.nl smtp server.

---

### Post by lswest on 2007-12-25
both hotmail and gmail need the security protocol (SSL) enabled for the mail out server, if that isnt enabled then enable it now, otherwise make sure the logins are carried over from the download server.  otherwise im not sure what could be wrong, did you get any kind of error when it tries to send?  (btw, after writing an email it gets put in your mail out folder, where you then have to manually choose "send/receive" for it to send.)

---

### Post by cazmatazzz on 2007-12-25
i have enabled ssl (with correct ports, ie in thunderbird i enabled ssl for outgoing server with port   465) then i get an error messag sying that the connection with smtp server gmail failed, that the server may be offline or incorrectly configured. 

however, i also hooked up my laptop which runs on ubuntu, installed thunderbird and added the gmail account. on my laptop it works fine, it can send and receive without any error messages. on the other computer (where i used exactly the same settings, which is hooked onto the same wired network) it can still only receive mail but not send it.

---

### Post by cazmatazzz on 2007-12-25
well somehow gmail works now! so thanks everyone! i dont exactly know what i've done but the gmail account is sufficient...

---

### Post by thiebaude on 2007-12-25
Please mark your post as Solved.Have a nice holiday.

---

### Post by jbalazs on 2007-12-25
I have the same problem to set up gmail in evolution when I sign up 
under sanding emails server type I selected  SMTP but 

What do you write in under server configuration Server:  ???

---

