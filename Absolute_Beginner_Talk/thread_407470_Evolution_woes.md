---
title: "Evolution woes"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-04-12
Hi,
I recently posted about receiving errors when trying to send mail, and was told that the error was primarily due to issues with Yahoo's servers... however, I just tried to send mail to a non-Yahoo account, and immediately on clicking send received this:
```
Error while performing operation. 
RCPT TO <mailbox@cbq.org.au> failed: 
Requested action not taken: mailbox name not allowed
```

Same error as the Yahoo thing. My account set-up is:
[IMG]http://www.tightbytes.com/images/ubuntu/EvoProb1.jpg[/IMG]

Oh, and logging Evolution activity yielded this right around the error:
> < b462aba0 >
Thread b58d7ba0 >
CamelFolder:get_message('Outbox', '8') =
class: CamelMimeMessage
mime-type: text/plain
content class: CamelDataWrapper
content mime-type: text/plain
< b58d7ba0 >
POP3_STREAM_LINE(56): '+OK <23128.1176377120@pop06.prod.mesa1.secureserver.net>'
POP3_STREAM_WRITE(6):
CAPA


POP3_STREAM_LINE(24): '-ERR authorization first'
POP3_STREAM_WRITE(27):
USER [email]robyn@tightbytes.com[/email]


POP3_STREAM_LINE(4): '+OK '
Got + response
POP3_STREAM_WRITE(14):
PASS xxxxxxxx
POP3_STREAM_LINE(4): '+OK '
Got + response
POP3_STREAM_WRITE(6):
CAPA


CamelException.setv(0xb58d73fc, 2, 'RCPT TO <mailbox@cbq.org.au> failed: Requested action not taken: mailbox name not allowed')
POP3_STREAM_LINE(18): '-ERR unimplemented'
POP3_STREAM_WRITE(8):
UIDL 1


POP3_STREAM_LINE(59): '+OK 1 1173521355.886434.smtp06.prod.mesa1.secure.0005950384'
Got + response
POP3_STREAM_WRITE(6):
LIST


POP3_STREAM_LINE(4): '+OK '
Any idea what I've done wrong?
Cheers

---

### Post by mohjlir on 2007-04-12
I'm not sure if this will help you, but have you tried unchecking 'server uses authentication'? Are you trying to send mail to an address that definitely exists?

---

### Post by antoz on 2007-04-12
I am not sure but I think the user name is wrong for sending mail. Check with your server for mail set up; as far as I know sending mail is done through your internet service provider. This is the way my mailbox is set up, it does not really matter what email adress you are showing (in fact you can have several only one needs to be default) but the actual sending is done through your ISP.

---

### Post by Robynsveil on 2007-04-12
> **antoz said:**
> I am not sure but I think the user name is wrong for sending mail. Check with your server for mail set up; as far as I know sending mail is done through your internet service provider. This is the way my mailbox is set up, it does not really matter what email adress you are showing (in fact you can have several only one needs to be default) but the actual sending is done through your ISP.
I have come to the conclusion that I have not told the entire story, here... and that's what the problem is. I live in Australia, we have Telstra Cable... so our ISP is Bigpond. My email address is part of a GoDaddy website account in the States.
I basically set up the account like I would have in Outlook (where it worked fine), following this page:
[http://products.secureserver.net/email/email_evolution.htm]("http://products.secureserver.net/email/email_evolution.htm")
...so, as you can see, all the settings are right based on this help file. However, it doesn't take into account the situation where the ISP is different from the web (and email) host. Anyone from Oz have any ideas? How did *you* set up your email with Bigpond?
Oh, and btw, I changed the Authentication type to 'Login' (mistake I caught *after* I did the screen-shot above) - same error persists...

---

### Post by ajgreeny on 2007-04-12
If you know the name of the smtp server of the ISP that you use to get on to the web, enter that in the server name where you've got smtp.secureserver.net showing and it should be possible to send mail from any username account.  It's the server that is important.

As an example, I have two email addresses for different ISPs here in the UK, one with *freeserve* (Orange) and another with *onetel,* but both will send messages if I use the freeserve smtp server, as that is the ISP with whom I log on to the net.  If I try to send onetel messages with the onetel server I get error messages and cannot send anything.

---

### Post by antoz on 2007-04-12
You should be able to set it up exaclty the same way as in outlook. 
I receive all my mail through my own website but to send  it has to be my service provider SMPT (mail.optusnet.com.au) That is for both Outlook and Evolution in which case you would have to send yours through Bigpond.
Whatever email address you show in your idendity this is what the receiver will see regardless who you sent it with. I hope this is of some help, I am sure you will figure it out eventually.A

---

### Post by esodin on 2007-04-12
Maybe I can help. I also use Telstra and had a similar problem when I moved in January. I used to have Cable but had to switch to ADSL2 (very fast by the way - measuring 21Mb down consistently).

After I had installed my computer I found that I could not send my mail using smtp.bizmail.yahoo.com as I had before. It turned out that Telstra has stared to implement a policy where they do not allow relays to "foreign" SMTP servers. While this had not been implemented for my cable hook-up in January it was implemented for the new ADSL2 service. I contacted Bigpond and they told me they would implement it through out over time.

The fix
Your Bigpond account came with an email address and access to one or more smtp servers (mine used to be smtp.bigpond.net now it's mail.bigpond.com) Set the smtp server in Evolution to mail.bigpond.com (You should not have to authenticate but if you do use your Bigpond username and password). 

Good luck!

---

### Post by antoz on 2007-04-12
This is exacltly the way I had to set up with Optus.

Leave authentication "PLAIN" check remember password and enter your username for Bigpond, the first time you sent an email it will most likely ask for the password.

---

### Post by Robynsveil on 2007-04-13
Esodin and Antoz, thanks heaps \\:D/ works a treat! I don't have to authenticate (at least, so it would appear, at this point - we'll see). Anyway, thanks again...

---

### Post by esodin on 2007-04-14
> **Robynsveil said:**
> Esodin and Antoz, thanks heaps \\:D/ works a treat! I don't have to authenticate (at least, so it would appear, at this point - we'll see). Anyway, thanks again...

You should be fine w/o authentication as long as you connect through Bigpond. You might need to authenticate if you were to hook up through a different ISP (taking your PC to a friends house etc.)

Glad to be of help :D

---

### Post by antoz on 2007-04-14
> **Robynsveil said:**
> Esodin and Antoz, thanks heaps \\:D/ works a treat! I don't have to authenticate (at least, so it would appear, at this point - we'll see). Anyway, thanks again...

Great to hear you got it sorted and glad I could help. I had heaps of help from this forum for various problems so it was good to give something back, cheers,A

---

### Post by antony_ec on 2008-03-03
I know this thread has had it's problem answered but just thought I'd add to it with some additional info...

I had exactly the same problem as mentioned here in that Evolution kept failing when trying to send email giving the message RCPT: <email address> mailbox name not allowed. Incidently I also use godaddy (smtpout.secureserver.net)

After reading this thread I worked out that my ISP has done exactly the same as Bigpond, which is to block users from accessing foreign SMTP relays - nice of them to tell me they've done this!!!

The following URL:
[http://www.123internetdesigns.com/faq/2006/08/list-of-isps-outgoing-smtp-servers.htm](http://www.123internetdesigns.com/faq/2006/08/list-of-isps-outgoing-smtp-servers.htm)

may be of use as it lists all the outgoing SMTP servers used by ISPs - as mentioned above, I didn't need to use authentication, probably as i'm 'onnet' to the ISP.

---

### Post by aallison05 on 2008-04-19
I was also having similar problems using GoDaddy's SMTP relay and my ISP, Suddenlink.  I changed the server name in Evolution to smtpout.secureserver.net:80 and everything works fine.

---

