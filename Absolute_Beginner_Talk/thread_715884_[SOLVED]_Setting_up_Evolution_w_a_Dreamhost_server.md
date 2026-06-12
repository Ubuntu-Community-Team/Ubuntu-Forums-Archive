---
title: "[SOLVED] Setting up Evolution w/ a Dreamhost server email blues"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by SloYerRoll on 2008-03-05
Title says it all. 
Is there anyone that knows of documentation on how to set up a Dreamhost email account w/ Evolution?

It uses Pop protocol w. is about as easy as it gets, but Evolution asks for some info and I'm not positive that I'm giving it the right info. 

I've even tried to set up a gmail account, but I haven't Googled that to figure it out yet. It's my dreamhost account that's a pressing issue for me. 

Cheers,

---

### Post by saj0577 on 2008-03-05
Could you please give more details of what information you think is wrong, and what information you are submitting.

Saj

---

### Post by jseiser on 2008-03-05
alright Im just going out on a limb here.  This is the info you normally need to set up a pop3 mail in thunderbird/outlook express etc.  This might not help you, but it might so ill post.

> This is from dream hosts website.

Both your incoming and outgoing mail servers are just

mail.example.com

Where example.com  is replaced by your domain you host with us.

email - [email]youremail@address.com[/email]
account name - [email]youremail@address.com[/email]
server type - POP3
incoming server - mail.YOURDOMAIN.com
outgoing server - mail.YOURDOMAIN.com

i would also tell it to use smtp authentication, so you will be able to actually send mail out.

> This is from dreamhosts website as well
NOTE.. you must set your username for the outgoing SMTP server (in Netscape for example under "Outgoing Mail Server User Name) to be the same as your incoming mail server username. It will then ask you for your password the first time you send mail. We use Authenticated SMTP.

So you need to tell your client to use the same log in as your incoming server, I dont know if that login will be your email address, or a special username you set up with dreamhost, I would email them, or if they have a message board, post and ask what that should be, maybe someone on here can help with that info.  

Also, a lot of ISP's block port 25 for other mail servers, you then need to tell your mail program to use a diff port, like, 587.  or, you can use your ISP's outgoing mail server, then adjust your settings as such.

---

### Post by SloYerRoll on 2008-03-05
Thanks for your replies. 
I think I'm getting hung up on the security and authentication types. 

I understand simple pop and IMAP mail protocols. So I know what data to put where. I'm close to positive all this stems from me not picking the right security type. 

@js: You said to use SMTP authentication. But I don't see that option. Is this just called something else?

It gives three options for the secure connection:
No encryption 
TLS encryption
SSL encryption

Then the Authentication types:
Password
APOP
Login
NTLM
GSSAPI
DIGEST-MD5
CRAM-MD5

---

### Post by SloYerRoll on 2008-03-05
It seems a bit odd. But beyond login credentials, there is no security. I stumbled over this by using the "set up dreamhost w/ Outlook Express" and adjusting for Evolution. 

I'm all set up!

Thanks you very much for your time though! 

Is there a way to "close" a thread so ppl know not to come looking in here anymore?

---

### Post by saj0577 on 2008-03-05
Mark it as solved. :)

Saj

---

