---
title: "*nix Spam Filter Server Solution?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by zacdl on 2007-08-06
Basically I am running a Windows network, but spam is becoming a problem.

We own a domain and use Exchange, so obviously all our email is controlled by the Windows server here.

However, I would like to install a *nix server that would accept all the incoming mail, filter it, and pass it on to the Exchange server. It would basically be transparent.

What exists out there? I would prefer if it was a GUI interface, and although I can poke around command line fairly well in *nix, I would rather have a more simple solution.

Edit- another thing I thought of, is there anyway for it to learn what is spam and what isn't (or is what will be suggested good enough to not worry about) by looking at, "Hey, this person emails this address frequently- I'll put them on a whitelist."

---

### Post by hyper_ch on 2007-08-06
well, spamassissin bundled with postgrey on a postfix server with uce restrictions would be my go....
Spamassassin has bayesian filters that can learn from ham and spam.... but if you are looking for a blacklist/whitelist solution, tmda could be worth looking at.

---

### Post by zacdl on 2007-08-06
So this would take all mail from *@domain.com just like my Exchange server does now (I would obviously change the port forward to a diff IP to accomplish this)?
Then it would FW to an Exchange server, and the Exchange server would never know the incoming mail is being filtered?

---

### Post by hyper_ch on 2007-08-06
well, spamassassin does filter messages according to certain rules and applies a scoring system.... then the email will be tagged and actually delivered...
So basically you can point all incoming emails to the linux server, have them processed and then forwarded to the actual exchange server...

The baysian filter is a probability method that's also available within spamassassin....  you will point out what is good email (=ham) and what is bad email (=spam) and it will then start also applying its rules to spamassassin... the more mail you process as good or bad the better the filter will become....

Greylisting is another approach based on the theory that spammers want to send out as much email as possible and hence can't afford too large mail queues... greylisting is fully RFC conform and works like this:
(1) an email arrives at the server
(2) the server checks the sending server - if it is ok, it will deliver the email to the "mailbox" or forward it or whatever you want it to do
(3) if it's not ok it will reply to the sending server "try again later"
(4) the sending server tries again to send the same email over time (I set my "timeout" to 15min), once that timeout limit has reached, your server will then accept the email and whitelist the sending server for some time (I think I set 7 days)
The assumption is that spammers rather do not try to have an email sent to a specific server but drop it from their mail queue.

Postfix UCE stuff: Postfix can be tuned to filter a rather large amount of email. you can make use of RBLs (Realtime Blackhole Lists) and also other stuff. Have a look here: [http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt](http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt)

And then finally you have stuff like TMDA - this operates on a whitelisting system. If a new email address arrives at the server, TMDA checks the whitelist, if the email address if found there, it will be forwarded, then checks the blacklist, if the email address is there it will be deleted and if it's on neither list, it will be greyed. The mailserver sends then out an email to the sender to which the sender has to reply (sort of "hey, I'm a human"). Once the sender replied, the email address is whitelisted and next time the email will be delivered automatically. There are tools out there that ask the user to go to a website and enter some code and stuff.... [http://tmda.net/](http://tmda.net/)
there are other systems like tmda but that's just the one I know.

But then, filtering spam is a real art to which I have not much deep insight... I just use greylisting, spamassassin with bayes and the postfix UCE stuff...

---

### Post by zacdl on 2007-08-06
So, since spamassassin uses user input to improve spam filters (we get much of the same things, obviously from different addresses and such though), how would that work? If it is just FW all email to the Exchange server that it deems good- how are the users training it?

So greylisting is based on the theory that spammers will send out emails one right after the other? Hence, if they send out two within 15 minutes, it gets blocked?
Wouldn't legit servers try to resend their mail as well, though?

Something like TDMA would work great to whitelist stuff (or blacklist recurring addresses, but like I said before- they change often). I know this might be getting too advanced, but how do I have it check with Exchange to know who is legit? I just hate to have to add users to both AD as well as the Linux mail filter when a new user comes along.

Edit- what Distro do you recommend for this? I perfer GUI-driven... Kubuntu looks nice but as far as I can tell it is mainly geared towards a workstation environment?

Thanks!

---

### Post by hyper_ch on 2007-08-06
normal servers try to resend up to 7 days... spammers won't do that because their queue will build up and in the end nothing will be sent out... no emails being sent - no money made...

Well, this is all done on the linux server... the linux server will then just forward the filtered emails to the exchange server...

spamassassin has default rules which can be applied to every email and also the ham and spam can be globally... 

regarding the distro, I'd go either for a BSD or Debian.... I wouldn't use a gui... a gui is not needed at all, it will just use up resources which will otherwise be available to the server to accomplish its work... and all those stuff is configured by config files...

---

### Post by zacdl on 2007-08-06
> **hyper_ch said:**
> normal servers try to resend up to 7 days... spammers won't do that because their queue will build up and in the end nothing will be sent out... no emails being sent - no money made...
OK so any legit server won't be affected? Just some spam emails might slip through once in a while?


Regarding the filter, how is it sent back out? Does outgoing mail go through the Linux server as well (First through Exchange though)?
My thinking- does it eventually learn that all outgoing messages to certain frequent addresses, are legit?

---

### Post by hyper_ch on 2007-08-06
well, outgoing messages will not be filtere, only incoming... there's also ways you can auto-whitelist certain stuff that after-checks are being skipped... as said, you need to do some reading on those stuff first before you will all comprehend it.

---

