---
title: "Forwarding Hotmail to GMail"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by guitarmaniac on 2007-02-22
I've just realised that I've been depending on a Microsoft program and would like to remedy this problem :razz: 
I tried to switch to gmail a few months back and didnt get anywhere because everyone sent all their emails to my hotmail account.
I also use the MSN feature in gaim.
Rather than change all my subscriptions and telling my friends to use my gmail account, I thought I might be able to forward my emails to my GMail account.
Is there a way of doing this?

---

### Post by nickoli_02 on 2007-02-22
There is.... but I haven't attempted it so, not sure :)

---

### Post by fusiachi on 2007-02-22
I think it requires a third-party program?

I'd go cold turkey.

---

### Post by guitarmaniac on 2007-02-22
there is a program called GetMail, but I'm fairly sure its windows only.
I would install a 3rd party program if absolutely necessary, if there was a linux version that is, no WINE stuff thanks. :P

---

### Post by nanotube on 2007-02-22
the answer:
[http://www.freepops.org/en/](http://www.freepops.org/en/)

:)

---

### Post by fusiachi on 2007-02-22
There are a few linux solutions to pull hotmail to a client like Evolution.

Set the outgoing server to gmail, and you're in business.


Edit: Beat to the punch.  Gotta improve the Dvorak typing.

---

### Post by guitarmaniac on 2007-02-22
OK, I've installed freepops but i have NO IDEA how to use it.
Please remeber, I've used Hotmail all my life, so there has been no need for me to learn anything about email clients like evolution or thunderbird.
Once I get Hotmail to forward my emails to GMail, I might get Thunderbird or Evolution to download my emails from GMail, depending on if I could be bothered.

---

### Post by nanotube on 2007-02-22
they've got some good docs in the documentation section. e.g., this nice tutorial:
[http://www.freepops.org/en/tutorial/index.shtml](http://www.freepops.org/en/tutorial/index.shtml)

what freepops does is allow you to pretend like you have pop access to your webmail - so that you can receive it directly in thunderbird or evolution, e.g. once you have it on your hd that way, you can either choose to have it autoforwarded to gmail, or just keep it in your mail client. 

setting gmail to work with a local client is much easier, since they actually give you real pop server access. :)

---

### Post by guitarmaniac on 2007-02-23
ok I read that tutorial but it doesnt seem to work (they used a different version of thunderbird as well so that didnt help :P).
heres what i did:

open up thunderbird
edit > account settings
add account
select email account
Your Name: Luke
Email Address: [email]luke.bennett@hotmail.com[/email]
Incoming Server Type: POP
Incoming Server: localhost
Incoming User Name: [email]luke.bennett@hotmail.com[/email]
Account Name: Luke

then I go to Get Mail and type in my password, click OK and then I get the error: Sending of password did not succeed. Mail server localhost responded: NETWORK ERROR

what did I do wrong?

By the way how will this tie in with my GMail account? I don't quite understand :confused:

---

### Post by nanotube on 2007-02-23
did you actually start the freepops service before trying that?

also, it doesn't tie in to your gmail account - it gets email to your local email client. then, if you really want to, you can set up forwarding using the email client. but that's a separate step. first step is to get the email coming to your local hd.

---

### Post by ganiawg on 2007-02-23
Hotmail --> Gmail and Yahoo --> Gmail here:
[http://forums.slickdeals.net/showthread.php?p=5025617]("http://forums.slickdeals.net/showthread.php?p=5025617")

---

### Post by guitarmaniac on 2007-02-23
im guessing freepops doesnt have a gui right?
so just run ```
freepopsd
``` AND THEN use Thunderbird? Is that correct?

---

### Post by nanotube on 2007-02-24
> **guitarmaniac said:**
> im guessing freepops doesnt have a gui right?
so just run ```
freepopsd
``` AND THEN use Thunderbird? Is that correct?

yea, freepops is a daemon that runs in the bg, so just start it, and then use t-bird.

---

### Post by guitarmaniac on 2007-02-26
ok, my problem is the OUTGOING server I think.
I set it to localhost, what should I set it to?

---

### Post by nanotube on 2007-02-26
> **guitarmaniac said:**
> ok, my problem is the OUTGOING server I think.
I set it to localhost, what should I set it to?

the outgoing (smtp) server is just for /sending/ mail, not receiving it. have you successfully received email?

just to summarize the freepops instructions, you should set up your t-bird to use "localhost" as the pop server, with port 2000, and use your full email "username@hotmail.com" as username, and your password as your password, of course. :)

for sending (smtp) you could just use gmail's outgoing smtp server (some instructions: [http://lifehacker.com/software/email-apps/how-to-use-gmail-as-your-smtp-server-111166.php](http://lifehacker.com/software/email-apps/how-to-use-gmail-as-your-smtp-server-111166.php))
or you could use your ISP's smtp server as well.

---

### Post by guitarmaniac on 2007-02-27
well I'm stumped!
Unless I'm meant to write something other than the word localhost as my INCOMING server, but thats what it said to write in the tutorial.
Has anyone successfully set up a hotmail account to run through Thunderbird with freepops?

---

### Post by konst88 on 2007-02-27
I think you should configure you gmail account, to accept mails from hotmail, if you know their POP3.
Then it is very easy to configure thunderbird to use gmail.
[https://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=21288](https://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=21288)

---

### Post by nanotube on 2007-02-28
> **guitarmaniac said:**
> well I'm stumped!
Unless I'm meant to write something other than the word localhost as my INCOMING server, but thats what it said to write in the tutorial.
Has anyone successfully set up a hotmail account to run through Thunderbird with freepops?

i just got it to work myself.
you set localhost AND set port to 2000, and also i had to download the latest hotmail.lua plugin, from here:
[http://freepops.cvs.sourceforge.net/*checkout*/freepops/freepops/src/lua/hotmail.lua?revision=1.67](http://freepops.cvs.sourceforge.net/*checkout*/freepops/freepops/src/lua/hotmail.lua?revision=1.67)
and place it instead of the old one, into /usr/share/freepops/lua/

also, i installed the latest freepops using the ubuntu debs from here: [http://cybertech.altervista.org/en/freepops.php](http://cybertech.altervista.org/en/freepops.php) (version 0.0.99), the one from the repositories was old (i'm using dapper).

hope that helps.

---

### Post by guitarmaniac on 2007-02-28
you know what it was?
I was using the beta version of Windows Live Mail which technically isnt hotmail!
It's ALWAYS something simple isnt it?
Reverted back to hotmail and now everything works fine.

---

### Post by nanotube on 2007-02-28
> **guitarmaniac said:**
> you know what it was?
I was using the beta version of Windows Live Mail which technically isnt hotmail!
It's ALWAYS something simple isnt it?
Reverted back to hotmail and now everything works fine.

hehe, glad it all worked out in the end. :)

now you can send email to all your friends to use your gmail account, and set your "reply to" header to gmail, and eventually, people will stop mailing your hotmail account. ;)

---

### Post by guitarmaniac on 2007-03-01
well if that happens then I'll have set set up my gmail to Thunderbird as well...
Can I merge my two accounts so that all my mail from bother addresses are in the same folders in TBird?

---

### Post by nanotube on 2007-03-01
well, the good part about gmail is that they give you pop server access (just have to enable it in preferences), so there's no need to go through freepops for that.

if you want everything to show up in one folder, then just use the 'global inbox' in thunderbird. that would shove everything into the same inbox. 

though i personally prefer to keep things in their own inboxes. seems neater that way. :)

---

