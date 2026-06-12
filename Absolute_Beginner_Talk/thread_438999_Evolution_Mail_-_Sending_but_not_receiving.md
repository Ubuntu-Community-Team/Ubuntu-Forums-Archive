---
title: "Evolution Mail - Sending but not receiving"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by SusieSA on 2007-05-10
I finally have Ubuntu up and running and I can access the internet.  I can send emails, but not receive them.

If I go straight to my ISPs mail page on the internet, I can access my email using my account name and password, but when I type these same details into the Evolution Mail Account, I am unable to receive mail.

My settings, in the Receiving Mail section of the Mail Account setup, are as follows:
Server Type: POP
Server: pop3.telkomsa.net
Username:online581921

When I try and send and receive, it asks gets through the receiving part and then pops up this error message:
-----------------------------------------------------------------------------------------------------------
Unable to connect to POP server pop3.telkomsa.net.
Error sending password: -ERR Login failed.

Please enter the POP password for online581921 on host pop3.telkomsa.net
-----------------------------------------------------------------------------------------------------------

If I type in my password again, the same error message pops up.

Is POP the same as POP3?

Is the Edit/Preferences/Mail Accounts the only place that I need to specify my email login parameters?

When I spoke to my ISP, she verified that the username and password are correct.  But she had never heard of Evolution mail and says that they don't support UBUNTU!!

What to do??? Thanks all.

---

### Post by Inxsible on 2007-05-10
> **SusieSA said:**
> I finally have Ubuntu up and running and I can access the internet. I can send emails, but not receive them.
 
If I go straight to my ISPs mail page on the internet, I can access my email using my account name and password, but when I type these same details into the Evolution Mail Account, I am unable to receive mail.
 
My settings, in the Receiving Mail section of the Mail Account setup, are as follows:
Server Type: POP
Server: pop3.telkomsa.net
Username:online581921
 
When I try and send and receive, it asks gets through the receiving part and then pops up this error message:
-----------------------------------------------------------------------------------------------------------
Unable to connect to POP server pop3.telkomsa.net.
Error sending password: -ERR Login failed.
 
Please enter the POP password for online581921 on host pop3.telkomsa.net
-----------------------------------------------------------------------------------------------------------
 
If I type in my password again, the same error message pops up.
 
Is POP the same as POP3?
 
Is the Edit/Preferences/Mail Accounts the only place that I need to specify my email login parameters?
 
When I spoke to my ISP, she verified that the username and password are correct. But she had never heard of Evolution mail and says that they don't support UBUNTU!!
 
What to do??? Thanks all.
You say that "it gets through the receiving part and then pops up this error message"
 
Have you also set up the smtp server along with your pop server ?
 
Also make sure that your email provider allows you to download all the emails or just the one that arrive from now on. There must be a setting which you can use.

---

### Post by KCormier on 2007-05-10
Call back, tell them you're using a program just like outlook, and ask them what the settings for outlook are!  :)  They should be able to help much more that way!! :)

---

### Post by SusieSA on 2007-05-10
Ah - man - sorry!!!  I typed this wrong.  Thanks for the replies.  

What I MEANT to say that the sending part is fine and then it pops up the error message when trying to receive.  Silly me.  

Sorry - I wrote this posting after trying to get this working for HOURS, so maybe my brain was a bit fuzzy.

I'm happy with the SMTP (Sending) functionality, it's the receiving that's a problem.

As for Telkom (the ISP), the username and password work in MS Outlook and also on the web when logging in directly to the Telkom webmail site.  So I don't really think the ISP can offer me any more help.

I think that there is something that I'm not setting correctly in Evolution.  

Any ideas?????

---

### Post by SusieSA on 2007-05-10
I have finally got this to work.  These are the steps I took:
1.  Took the dog for a walk on the beach
2.  Had a lovely dinner
3.  Installed Thunderbird mail with same send/receive options and IT WORKED FIRST TIME!
4.  Tried Evolution again and..... IT ALSO WORKED!!!

So now I've uninstalled Thunderbird mail and Evolution is still working.

I'm really not sure what fixed this - a clear head, a full stomach, time or something strange when Thunderbird was installed.

I wish that I had tried step 4 before 3 because this would be a more informative solution.

Thanks for your help everybody.

---

### Post by Nachoj on 2007-05-16
Hi
it's really strange. I had a similar problem, and then, out of nowhere, just write an email and it's working

I configure Evolution to use gmail with this settings: 

incoming server 
   pop.gmail.com
   SSL encryption
   Authentification Type: Password

outgoing server 
   smtp.gmail.com
   SSL
   Authentification Login
   username: <my gmail address>

---

### Post by romac on 2008-02-28
i have this same problem but i've had evolution up and running for months just fine

i haven't changed any settings whatsoever, then all of a sudden every time i start evolution i get this error on all three mail accounts, but it i just click on 'cancel all' then 'send/receive mail' it downloads my mail messages just fine. 

it still bugs the hell out of me though.

good thing i'm not a normal person with a 9-5 job - i'd never be able to deal with the continuous, long list of things i've had to fix since installing ubuntu

if i didn't hate microsoft so very much i think i'd have given up and switched back by now!

---

