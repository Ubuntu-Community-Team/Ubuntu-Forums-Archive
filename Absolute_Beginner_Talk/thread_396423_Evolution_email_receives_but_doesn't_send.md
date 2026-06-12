---
title: "Evolution email receives but doesn't send"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-29
Just for your info this is on edgy 6.10
Since I've got the internet working I thought I would try evolution email. I am pretty
sure I have the setting the same as my outlook was setup. For receiving it is POP3
and for sending it it SMTP. Seems like there are always problems with email, even with
windows outlook express.

Evolution just shows POP I don't know if that is the same as POP3 ???
But I CAN receive emails.

But I cannot send them apparently. At least I can't send one to myself or anyone else.
It is set to SMTP.
The box is not checked for: Server requires authentication. I've tried both ways so I don't
think it's that.
My outlook is not checked for authentication.

I'm kind of at a loss at this point.
thanks

---

### Post by Gina on 2007-03-29
Evolution works fine for me in Dapper 6.06.  For receiving I get several options (12 in fact, including POP and IMAP)  and two (SMTP and Sendmail) for sending.

---

### Post by linuxjerk on 2007-03-29
Those options seem about the same form me. I just can't seem to send email.
Is the POP3 different than POP? But pop is for receiving right?
SMTP is sending?
Or is it just my screwy provider?

---

### Post by linuxjerk on 2007-03-29
My providers address for sending is formatted in outlook express like this. I won't put in the actual name.:) 

SMTP.Domain_name.com 

Does this look correct for evolution setup?

---

### Post by Gina on 2007-03-29
OK except that your server might want SMTP in lower case ie. **smtp.domain.com**

---

### Post by Woody@N87 on 2007-03-29
It looks correct to me and if it worked with your outlook you would think it would work with Evolution.  Some ISP's suggest that SMTP will work better if you direct to a particular port, such as smtp.ispname.com:587.  I know mine is set up that way for AOL and I think 1and1.com requires the same thing.  Maybe you can locate a port number for your isp's smtp connection on their site ?  Just an idea.

---

### Post by drmbogo on 2007-03-29
Just a Thought: I had the same problem when I assumed the my providers send url was smtp.(provider).net.
In fact, it is mail.(provider).net! Nothing on the providers website mentioned this, I found it by googling: "smtp, (provider)"; top 'o the list was a site that showed many providers' smtp addresses (sorry, I dont have the url for that site in front of me :)
dB

---

### Post by linuxjerk on 2007-03-29
Sorry I mistyped that in the posting. It is entered into the account in lower case.
Well outlook doesn't require a port address but I could look into that. :confused:

---

