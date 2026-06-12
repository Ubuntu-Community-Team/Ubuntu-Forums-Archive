---
title: "Easiest Email Server?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-03-27
Which email server in the Ubuntu server repository would you recommend for a Linux newbie? I have a small classroom where we teach <10 users how to use email. I'd like to get a server set up locally here so we don't have to rely on the city servers.

Thanks for any advice.

Gary

---

### Post by Kobalt on 2007-03-27
I'd say postfix, but you've got alternatives...
Here is some info : [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by lamalex on 2007-03-27
zimbra is very easy to set up. very easy and very powerful.

EDIT: nm i didnt realize you said in repo. zimbra is not in repo.

---

### Post by Gary Nored on 2007-03-27
Thanks for the link to the Postfix documents. They suggest installing many services like authentication, encryption, etc.,  that I don't see a need for in my classroom. Do you think Postfix will work without SMTP-AUTH and TLS or do I need to install all of this stuff?

Thanks again,

Gary

---

### Post by Mr. C. on 2007-03-27
You will not need SMTH AUTH for your local users.  AUTH/TLS is advantageous for remote users.

Are you planning on sending email outbound ?  Your school's or city's firewall may prevent that by blocking outbound port 25.  You'll have to investigate that.

If this is for local LAN email, you will like not have trouble.

MrC

---

### Post by Gary Nored on 2007-03-28
Thanks for the help. I've got Postfix installed -- now just have to learn how to use it.

We will not be allowing any mail to leave the room, so no auth for me. Whee!

Gary

---

### Post by Gina on 2007-03-28
Evolution - already installed :)  Nice and simple but it works fine. :)

---

### Post by brennydoogles on 2007-03-28
> **Gary Nored said:**
> 

We will not be allowing any mail to leave the room, so no auth for me. Whee!

Gary

LOL. That quote just made you my new hero. Hope everything works out well for you!!

---

