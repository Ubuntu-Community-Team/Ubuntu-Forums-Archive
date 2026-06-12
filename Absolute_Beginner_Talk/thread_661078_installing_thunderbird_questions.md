---
title: "installing thunderbird questions"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by ubiubi on 2008-01-07
I'm trying to install thunderbird and it asks me if I am using 
 POP   or  IMAP

Then it asks me the name of my OUTGOING server and the name of my

INCOMING server

(I entered my hotmail address as my email address.

Where can I find the server and POP/IMAP information to complete these forms?

---

### Post by erginemr on 2008-01-07
Unfortunately neither POP, nor IMAP...

Hotmail provides web based e-mail, and AFAIK, Thunderbird does not support it out of the box.

Yet, a quick search on Google yielded the following web page, which looks promising:

[http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)

---

### Post by philinux on 2008-01-07
> **erginemr said:**
> Unfortunately neither POP, nor IMAP...

Hotmail provides web based e-mail, and AFAIK, Thunderbird does not support it out of the box.

Yet, a quick search on Google yielded the following web page, which looks promising:

[http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)

I use the webmail and hotmail addon in TB. Works a treat.

---

### Post by philinux on 2008-01-07
> **ubiubi said:**
> I'm trying to install thunderbird and it asks me if I am using 
 POP   or  IMAP

Then it asks me the name of my OUTGOING server and the name of my

INCOMING server

(I entered my hotmail address as my email address.

Where can I find the server and POP/IMAP information to complete these forms?

Normally you'd get this from your isp.

Outgoing pop eg pop.whateverisp.com

incoming smpt.whateverisp.com

---

### Post by ubiubi on 2008-01-08
Thanks everyone. I downloaded the webmail and hotmail addons but could not find the 'Tools Menu/Extensions' in  thunderbird to install them. 

the instructions on the link you gave me says


[COLOR="Red"]How to Install

   1. Right-Click the link above and choose "Save Link As..." to Download and save the file to your hard disk.
   2. In Mozilla Thunderbird, open the extension manager (Tools Menu/Extensions).
   3. Click the Install button, and locate/select the file you downloaded and click "OK".[/COLOR]




My internet provider is wanadoo.fr so I supose my outgoing would be
 POP.wanadoo.fr                  and the incoming would be 
smpt.wanadoo.fr   ?

Any comments? I'm not on my home computer at the moment but I am aware of the links above and had the problem I just mentioned last night when I triesd to install the two add ons

---

### Post by erginemr on 2008-01-08
Normally, 
```
Incoming -> pop.wanadoo.fr
Outgoing -> smtp.wanadoo.fr
```
would do, but I have checked the wanadoo.fr web page. And apparently, they have changed the domain name to orange and are suggesting existing users to promote their mail address from [email]user@wanadoo.fr[/email] to [email]user@orange.fr[/email]:

[http://assistance.orange.fr/2461.php](http://assistance.orange.fr/2461.php)

So, please first check if the above POP (to receive the email) and SMTP (to send the email) servers work. If not, try the following:
```
Incoming -> pop.orange.fr
Outgoing -> smtp.orange.fr
```

---

### Post by erginemr on 2008-01-08
> **ubiubi said:**
> Thanks everyone. I downloaded the webmail and hotmail addons but could not find the 'Tools Menu/Extensions' in  thunderbird to install them. 

the instructions on the link you gave me says
........

My internet provider is wanadoo.fr so I suppose my outgoing would be
 POP.wanadoo.fr                  and the incoming would be 
smpt.wanadoo.fr   ?

Any comments? I'm not on my home computer at the moment but I am aware of the links above and had the problem I just mentioned last night when I triesd to install the two add ons

If you are planning to connect to Wanadoo Mail only, then you don't need to download and use those two extensions, as Wanadoo (I believe) supports POP/SMTP. However, if you are also planning to use Thunderbird with Hotmail (or say, Yahoo!), then please see the attached screenshots on how to install Thunderbird extensions.

---

### Post by ubiubi on 2008-01-08
Thanks alot, erginemr for your time and trouble. I'm finally at home and when I get my 10 year old of the msn chat I'll look into it. The 'orange tip' seems obvious now but i'd forgotten all about the wanadoo changes over here. And many thanks for the screen shots. I'll keep you posted! Cheers

---

