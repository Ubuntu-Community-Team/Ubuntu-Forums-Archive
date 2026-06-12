---
title: "Need an outgoing mail server"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-03-29
My home ISP, charter.net, upgraded their mail servers on Wednesday.  Since then, I cannot send any emails out using smtp.charter.net or mail.charter.net unless the sending address is a charter.net address.  So my business accounts cannot send emails out, only receive.  I have called customer support and when I finally got in touch with someone that would listen, they told me that I'm SOL.  They will not attemp to fix problems with other mail domains.  

So now I need an outgoing mail server.  I have 2 desktops and 3 laptops in the home network (3 XP and 2 Linux).  I don't want to have to maintain an smpt server (or fight to make it not appear as spam) so I'm looking for a mail service that also provides outgoing mail servers.  

Anyone know of anything?

I read about postfix, but I use dynamic IPs, and don't want my emails to appear as spam.  Help me please!

---

### Post by dbbolton on 2007-03-29
gmail !

---

### Post by chalex on 2007-03-29
You could sign up for a cheap hosting plan that offers mail service and use their outgoing servers. I think you can get away with ~$2/mo.

EDIT: maybe you could ask around and use a friends'?  OTOH, in my case, all outgoing mail servers available to me require authentication with a username and password, so you'd need to find a friend who runs a mail server and get him to make you an account.  Or again, you could get a pay-for mail service like pobox.com

---

### Post by halitech on 2007-03-29
> **l951b951 said:**
> My home ISP, charter.net, upgraded their mail servers on Wednesday.  Since then, I cannot send any emails out using smtp.charter.net or mail.charter.net unless the sending address is a charter.net address.  So my business accounts cannot send emails out, only receive.  I have called customer support and when I finally got in touch with someone that would listen, they told me that I'm SOL.  They will not attemp to fix problems with other mail domains.  

So now I need an outgoing mail server.  I have 2 desktops and 3 laptops in the home network (3 XP and 2 Linux).  I don't want to have to maintain an smpt server (or fight to make it not appear as spam) so I'm looking for a mail service that also provides outgoing mail servers.  

Anyone know of anything?

I read about postfix, but I use dynamic IPs, and don't want my emails to appear as spam.  Help me please!

are you paying for hosting for your business accounts or do you have a domain name already? If you have a business account and their mail servers will not allow you to send mail, then that is their problem. If you have a domain hosted somewhere for work, check with your IT department and see what mail servers you can use that are being paid for at work.

now, if you are running a domain off their service and you only pay for residential service, that isn't their problem, it's yours :(

---

### Post by Incense on 2007-03-29
I'm going to have to second Gmail. It's free, and it comes with POP and SMTP. Just sign up and use their SMTP.

---

### Post by dbbolton on 2007-03-29
> **Incense said:**
> I'm going to have to second Gmail. It's free, and it comes with POP and SMTP. Just sign up and use their SMTP.
it's been awhile since i signed up, but back in those days you needed an invitation or a mobile phone with text messaging to sign up. so [l951b951]("http://ubuntuforums.org/member.php?u=215323"), if should decide to use gmail, and need an invitation, just pm your current email adress to me.

---

### Post by l951b951 on 2007-03-30
> **dbbolton said:**
> it's been awhile since i signed up, but back in those days you needed an invitation or a mobile phone with text messaging to sign up. so [l951b951]("http://ubuntuforums.org/member.php?u=215323"), if should decide to use gmail, and need an invitation, just pm your current email adress to me.

As of recent, Gmail opened itself to the public, so no invitation is needed, but thanks for the offer.  I've had 2 gmail accounts for over a year.

My exact situation is: the domains are KW.com and AthensHomeSales.com .  KW is owned by corporate, and their instructions are to use your ISP's SMTP.  Corporate (Keller Williams Realty) has a website at that domain that they host.  At home I use charter.net and in our office the ISP is bellsouth.net .  So when I go to the office, I have to change my outgoing mail server to bellsouth's.  
Athenshomesales is the same, website is hosted, pop3 email retrieval is offerred, but not smtp.  Their instructions are to use my ISP's outgoing mail server.

I will look into POBox.com.  any other suggested services that would let me use their smtp without having to transfer my email hosting to them? 

I'm surprised I'm having such a hard time finding one online, I imagined traveling salesmen would have found a service so they can send emails regardless of the hotel's ISP.

---

