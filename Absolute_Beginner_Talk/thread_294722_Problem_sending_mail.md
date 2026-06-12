---
title: "Problem sending mail"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Harry_Callahan on 2006-11-07
Hello to all,

I'm having a problem sending mail with Edgy 10.06. I have no problem recieving mail, just sending. My provider uses a simple smtp connection(no ssl, no username\password authentification): out.myprovider as smtp server. I can recieve mail without problems from Win XP Outlook. I get no error messages from Evolution and Thunderbird, when I click "send" button I see the mail for a few seconds in the "Outbox" and when I find the mail in the "Sent" box, but the mail is not recieved by the recipent.

Now here's what is driving me nuts: If I forward that mail from the "Sent" box, the recipent recieves the mail....

This happens in Evolution and Thunderbird, I have no problems(using same configuration) from MS Outlook

Anyone experience the same problem?

Thanks for your help!

---

### Post by LadyDoor on 2006-11-07
It's possible that your client isn't yet properly set up for smtp.
First, I'd make sure that an SMTP client is installed...

```

$ sudo aptitude install msmtp

```

(you may need to enable universe). Then go into the settings for your
client and make sure that they comply with the instructions set by
your provider (generally they will have instructions for configuring
graphical mail clients).

I hope this is helpful and not just telling you stuff you already
know...

Good luck!
--Door

---

### Post by Harry_Callahan on 2006-11-07
Thanks for your reply, but still no luck. As I sad before the configuration is very very simple, no problems under MS Outlook(my smtp server doesn't use ssl or authentification). I don't want to say something silly, but is it possible that my provider filters mail sent from mail clients different from Outlook 2003/Express or Netscape Mail 7.2???? I found on another forum a problem like this on Debian and this person had the same provider as mine, he solved it by using Thunderbird, I tried Thunderbird but nothing

Regards

---

