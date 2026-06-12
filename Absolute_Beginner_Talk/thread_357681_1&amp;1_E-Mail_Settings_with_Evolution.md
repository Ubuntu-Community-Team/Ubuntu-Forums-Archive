---
title: "1&amp;1 E-Mail Settings with Evolution"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by pcflunkies on 2007-02-09
Has anyone had any luck getting Evolution to "Send" e-mail via a 1&1 Hosting?

Here are my settings:

SMTP - for Server Type
smtp.1and1.com is the server name
Server requires Authentication is Checked (although I have Tried Unchecked)
"No Encryption" is what is set
Authentication  after Check for Supported Types, Plain and Login are the only two available, and I have tried both
I have also tried both my email address as my user name and the xxxxxxxx-username 

Although nothing seams to work. I do have a different Email account setup to a different Hosting company that works with no problems. What am I doing wrong on the 1&1?


Here is the error that I am getting:

Error while performing operation.

MAIL FROM command failed: Service not available, closing transmission channelError while performing operation.

---

### Post by shareMenaPeace on 2007-02-09
> **pcflunkies said:**
> Error while performing operation.

MAIL FROM command failed: Service not available, closing transmission channelError while performing operation.

Maybe the SMTP server is offline?

---

### Post by pcflunkies on 2007-02-09
I am able to send with the same account via outlook and a different computer.

---

### Post by DJ_Peng on 2007-02-10
Are you using just your username or the full email addy? I was able to send SMTP from Thunderbird with just the username but when I tried checking my POP3 mail I had to use the full addy. You may also want to try using the alternate port 587. That's what I have working in Thunderbird.

---

### Post by pcflunkies on 2007-02-10
I have tried both, the xxxxxxx-usename and [email]username@domain.com[/email] with out any difference, although if I try the wrong user name or the wrong password (example  domain_name.com and password) It continues to say "Unable to authenticate to SMTP server. Bad authentication response from server."

What is frustrating, is that I have looked all over and can't find even a partial list of the error messages and specific causes for each, so I can trouble shoot this problem a little better.

I might have to try ThunderBird. I have always been a MS fan, untill recently, but my stadagy has always been why install other software when there is already somthing there that can do it, if I just learn it. so I have never had any problems. I am was trying to start off with what is supposed to work, so I don't cause any more problems, untill I learn it. I just keep running into problems

How can I get and view the source code so perhaps I can figure out what the cause of the fault is?

---

### Post by DJ_Peng on 2007-02-10
Thunderbird doesn't have a full calendar applet yet, but hey're working on it with Lightning, part of the [Calendar project](http://www.mozilla.org/projects/calendar/). I'd try it except it can't sync to a PDA yet, which is a deal breaker for me. Otherwise I'm loving Thunderbird, and when Thunderbird 2 comes out I think you'll love it even more.

---

### Post by pcflunkies on 2007-02-10
In my case I use the Calendar almost as much as I send and receive email (quite often), so that is a definate down side for me. As you said I also plan on using my PDA but I haven't gotten that far yet.

---

### Post by laytek on 2007-02-23
Hi pcflunkies,

I am having trouble sending email to my 1 & 1 account also.
> **pcflunkies said:**
> Has anyone had any luck getting Evolution to "Send" e-mail via a 1&1 Hosting?

Here are my settings:

SMTP - for Server Type
smtp.1and1.com is the server name
Server requires Authentication is Checked (although I have Tried Unchecked)
"No Encryption" is what is set
Authentication  after Check for Supported Types, Plain and Login are the only two available, and I have tried both
I have also tried both my email address as my user name and the xxxxxxxx-username 

Although nothing seams to work. I do have a different Email account setup to a different Hosting company that works with no problems. What am I doing wrong on the 1&1?


Here is the error that I am getting:

Error while performing operation.

MAIL FROM command failed: Service not available, closing transmission channelError while performing operation.

In my configuration, I have two different e-mail accounts. My DEFAULT account is a bellsouth.net address. When I create a new message and select my 1&1 account in the FROM line, and then try to send it, I have noticed that the send/receive mail window that opens indicates that Evolution is trying to send the new message to smtp.BELLSOUTH.NET, not smtp.1AND1.COM. I have checked the 1AND1.COM account configuration several times. I believe this is a bug with EVOLUTION not properly picking up the correct configuration.

Has anyone else seen this problem? :confused: 

LayTek

---

