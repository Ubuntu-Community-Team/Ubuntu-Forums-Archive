---
title: "Evolution Email Confusion"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by croxi on 2007-05-02
I  have been trying for a few days now to get my emails sent using Evolution but to no avail. 
I have been told to try and reinstall Evolution, without success with sending or receiving emails. 

I then tried the following :-

I started with configuring the email servers like this:-

Identity - required info - name (my name) 
email - (my email)@hotmail.com

optional info
tick in "make this my default account"
reply to -  (my email)@hotmail.com
organisation - (no org input here)
signature - (my name)

REQUIRED EMAIL

Server - POP  - (I don't know if this is correct for hotmail accounts)
Config - POP3.hotmail.com  - (entered exactly as stated)
Username - (my email)@hotmail.com  

SSL encryption 

My question is if this is all that's necessary to get my damned emails sent off?

---

### Post by mejy on 2007-05-02
Hotmail doesn't support POP3 - it's now purely webmail based unless you get the paid version to prevent spam (supposedly), and I believe they're phasing even that out too.  You can either use thunderbird with the hotmail extension, use firefox or get a gmail account (or similar).

---

### Post by Seisen on 2007-05-02
Or you can get a yahoo email account and use ypops. Somebody finally made .deb file for it and it works perfectly,

[http://www.geocities.com/t_skariah/ypops/]("http://www.geocities.com/t_skariah/ypops/")

---

### Post by croxi on 2007-05-02
ok, so it doesn't use POP3, my question is - what DOES it use in order to get my hotmail account working with Evolution? 

I don't want to sit here filing through all the things that Hotmail DOESN'T use, because that's counterproductive, I need clear instructions on how to configure Evolution so that it DOES actually end up working pretty soon.

---

### Post by Seisen on 2007-05-02
Try this 

[http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html]("http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html")

---

### Post by canadianwriterman on 2007-05-02
I think what we're saying is that Hotmail will NOT work with Evolution.

---

### Post by croxi on 2007-05-02
I have also tried getting Thunderbird working too, its just as bad as Hotmail, so what can I do to fix it?

I keep getting broken pipes everywhere...

---

### Post by compiledkernel on 2007-05-02
Unless you pay for provided support via MSN (which some here would consider evil in nature) you cannot POP off a Hotmail account. Seemingly even that is not likely in certain cases. Research suggests that using WebDAV would make hotmail use possible, but I dont believe that will work for you, and ultimately if it did, would never be able to take advantage of the Calendering and scheduling aspects of Evolution in concert with the email aspect. 

Citing Wikipedia on the concept 

> It is in principle possible to check one's own e-mail using the WebDAV protocol (an extension of HTML), using Microsoft Outlook and Outlook Express on PC, Microsoft Entourage on Mac, or an extension for Mozilla Thunderbird.[6] But while this service was free for a number of years, Microsoft announced on September 27, 2004 that they were making it a subscription-only service for new users immediately and existing users from April 2005. However, some (not all) existing users are still able to access their Hotmail accounts via this protocol for free as of April 2007. It is unclear if or when Microsoft will revoke this feature as many users rely on this function.

---

### Post by mejy on 2007-05-02
> **croxi said:**
> ok, so it doesn't use POP3, my question is - what DOES it use in order to get my hotmail account working with Evolution? 

I don't want to sit here filing through all the things that Hotmail DOESN'T use, because that's counterproductive, I need clear instructions on how to configure Evolution so that it DOES actually end up working pretty soon.

The point is that we can't give you 'clear instructions' because hotmail 'DOESN'T' work with evolution.  The only methods are hackish and unreliable, so you should either get a different email account or use the hotmail web interface.

---

### Post by jpatton on 2007-05-02
> **croxi said:**
> I  have been trying for a few days now to get my emails sent using Evolution but to no avail. 
I have been told to try and reinstall Evolution, without success with sending or receiving emails. 

I then tried the following :-

I started with configuring the email servers like this:-

Identity - required info - name (my name) 
email - (my email)@hotmail.com

optional info
tick in "make this my default account"
reply to -  (my email)@hotmail.com
organisation - (no org input here)
signature - (my name)

REQUIRED EMAIL

Server - POP  - (I don't know if this is correct for hotmail accounts)
Config - POP3.hotmail.com  - (entered exactly as stated)
Username - (my email)@hotmail.com  

SSL encryption 

My question is if this is all that's necessary to get my damned emails sent off?

the last i checked you can use fetchmail to grab hotmail  accounts, but i believe it required some tweaking, or there was something similar to fetchmail that did that. it's been like early last year i think that i futzed with that.

i'll see if i can find what i was doing then, if i find it i'll repost here.

---

### Post by jpatton on 2007-05-02
Ok I just found this online, [http://www.catb.org/~esr/fetchmail/fetchmail-FAQ.html#I5](http://www.catb.org/~esr/fetchmail/fetchmail-FAQ.html#I5) I believe i used hotwayd, but the link on that page isn't working so try this one. [http://sourceforge.net/projects/hotwayd/](http://sourceforge.net/projects/hotwayd/)

---

### Post by Seisen on 2007-05-02
Did the link I provided work for you or is it unresolved still?

---

### Post by jpatton on 2007-05-02
> **Seisen said:**
> Did the link I provided work for you or is it unresolved still?

geez, sorry i missed your second link, didn't even know hotway was available via apt-get :)

---

### Post by croxi on 2007-05-04
I tried your response to my problem, I´ve been trying to sort it for a while, but nothing is working. 

I posted a gripe about Gmail working on my UBUNTU 7.04 laptop but the fact that thunderbird and Evolution don't, its just frustrating...

---

### Post by cpdave on 2007-05-04
try this link: -

[http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html]("http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html")

worked a treat for me.

- CPDave

---

### Post by croxi on 2007-05-08
well, thanks everyone for helping out. I feel better for knowing that there is so much info out there that can help people like me who really don't have much computing knowledge. 

thanks again.

---

### Post by Fonon on 2007-12-02
> **cpdave said:**
> try this link: -

[http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html]("http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html")

worked a treat for me.

- CPDave

I tried that, but it failed to work.  Evolution complains about how it fails to fetch the email.  It failed to read a valid greeting at server 127.0.0.1

Anyhelp?

---

