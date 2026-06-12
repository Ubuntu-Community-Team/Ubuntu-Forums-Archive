---
title: "AIM account does not work in Gaim and Kopete!!! Why?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by ksamvel on 2007-03-16
Hi,

I know that this is a common problem and lots of posts are related to the problems met in using [COLOR="Red"]**AIM**[/COLOR] accounts in Gaim but I can not still find a solution even after couple of days spent on surfing Internet in hope to resolve current issue.

So, the situation is that I have opened an AIM account in the beginning of the week. Can connect to AIM using AOL web-site and their Express page. Password is 8 characters long and works fine.

Now I create account in GAIM that represents AIM. Try to connect - input password - and get error that my information 'login/password' is incorrect.

I have also tried to add account in Kopete but but the same behavior.

All my co-workers can connect from office to AIM without any problems using GAIM and linux distributions. They use default settings like:

    server: login.oscar.aol.com
    port   : 5190

Moreover GAIM uses the same server : port in order to connect to ICQ and I am not experiencing any problems. Only with AIM account. Thus I would assume there is definitely something wrong with AIM and most probably my OS setup.

So, people, please help me. This is getting extremely annoying to me. Suggestions?

Samvel

P.S. Upgrade to GAIM beta6 didn't help.

---

### Post by dbbolton on 2007-03-16
do you have "use AIM proxy server" checked ? 

what do you have selected under "Proxy Options" ?

---

### Post by ksamvel on 2007-03-16
Yes, '***Always Use ICQ/AIM proxy***' is [COLOR="Red"]**checked**[/COLOR].

**[COLOR="Red"]Proxy type[/COLOR]** is: ***Use Global Proxy Settings***

---

### Post by dbbolton on 2007-03-17
uncheck the AIM proxy, and then on the drop-down bar select "do not use any proxy" or whatever it says.

i'm not sure if that will do it, but it's worth a shot

---

### Post by ksamvel on 2007-03-17
That didn't help. I have tried all possible combinations but nothing changes. All the time the same output is gotten:

Incorrect login/password.

What else can be cause of this problem?

---

### Post by ksamvel on 2007-03-22
So, any other ideas?

---

### Post by ceeg on 2007-03-22
I don't know the answer to your issue, but perhaps as a temporary solution you can use [http://www.meebo.com](http://www.meebo.com)

I use it all the time now, instead of a software IM solution.

---

### Post by ksamvel on 2007-03-22
> **ceeg said:**
> I don't know the answer to your issue, but perhaps as a temporary solution you can use [http://www.meebo.com](http://www.meebo.com)

I use it all the time now, instead of a software IM solution.

Thanks for advice but that is not way out :). All my other contacts are already in GAIM with support for Jabber, ICQ accounts that can be connected simultaneously.

---

### Post by Zzl1xndd on 2007-03-22
What format are you putting your screen name in as? I know its a basic question but it was a common problem when I worked for AOL

---

### Post by ksamvel on 2007-03-22
> **tweakedenigma said:**
> What format are you putting your screen name in as? I know its a basic question but it was a common problem when I worked for AOL

I didn't understand your question about format. What do you mean? It is a plain text, like:

   Myaccount

Is there any special option here?

---

### Post by Zzl1xndd on 2007-03-22
I mean are you putting in:

"Username@aim.com" or just "Username"

---

### Post by plainjane on 2007-03-22
When I was first trying to sign into Gaim I got the same error message you are receiving.  I dont' know if this is relevent, but on my Aim password I have a symbol at the end, such as %.  When signing into Gaim, I had to leave this off.  Then it worked fine.  Strange.  Hope you get it up and running soon.

---

### Post by ksamvel on 2007-03-22
> **tweakedenigma said:**
> I mean are you putting in:

"Username@aim.com" or just "Username"

Ok, here are my tries:

1. **Username without '@aim.com'**. I get an error saying '***[COLOR="Red"]Invalid password[/COLOR]***'

2. ***Username with '@aim.com'***. Another error message appears: ***[COLOR="Red"]Invalid username[/COLOR]***

So, I'd assume after all that Username should be put without postfix with *@aim.com*

---

### Post by ksamvel on 2007-03-22
> **plainjane said:**
> When I was first trying to sign into Gaim I got the same error message you are receiving.  I dont' know if this is relevent, but on my Aim password I have a symbol at the end, such as %.  When signing into Gaim, I had to leave this off.  Then it worked fine.  Strange.  Hope you get it up and running soon.

:) My password consists of letters (Upper/Lower Cases) and Digits. So there is nothing in there that may cause that kind of error.

---

### Post by Zzl1xndd on 2007-03-22
your right it should just be "username" although it sounds like it is connecting to the server by what your saying I would have to assume that there is some type of password issue. Could you try logging on to Aim.com changing your password to something basic all lower case and trying to sign in again?

---

