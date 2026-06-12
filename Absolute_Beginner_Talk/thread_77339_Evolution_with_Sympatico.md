---
title: "Evolution with Sympatico"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by canadianwriterman on 2005-10-16
I'm going to try one more time to get my SMTP set up correctly on Evolution using Breezy and Sympatico high speed ISP in Canada.

I've posted many times and tried all possible combinations of settings with the help of many of you. All attempts have failed.

As a last resort, I'm looking for anyone who uses the:

smtphm.sympatico.ca

SMTP server who would share their settings with me. Many other people with different Sympatico SMTP servers have tried to help, but the settings seem to be different. For example, this server needs authentication.

Pretty please, any of you Canadian Sympatico users! Thanks.

---

### Post by Kapre on 2005-10-16
[QUOTE=canadianwriterman]I'm going to try one more time to get my SMTP set up correctly on Evolution using Breezy and Sympatico high speed ISP in Canada.

I've posted many times and tried all possible combinations of settings with the help of many of you. All attempts have failed.

As a last resort, I'm looking for anyone who uses the:

smtphm.sympatico.ca

SMTP server who would share their settings with me. Many other people with different Sympatico SMTP servers have tried to help, but the settings seem to be different. For example, this server needs authentication.

Pretty please, any of you Canadian Sympatico users! Thanks.[/QUOTE]


canadianwriter - I'm not on sympatico and is not using Evolution as my e-mail (though it is working when I use it with my ISP). I'm using Thunderbird. Can you try setting up your e-mail using Thuderbird (I think it is much easier to setup than evolution). 

Maybe the reason you're being blocked is because sympatico has a tie-up with M$N. ;)

K

---

### Post by canadianwriterman on 2005-10-16
Hi Kapre, thanks for your message. I do have Thunderbird set up, but I really like the personal information manager/address book built into Evolution as well as I like the Gnome look to it. I'll keep using Thunderbird until I can get Evolution set up.

Good observation about Sympatico and MSN... even though I'm a Sympatico user, I can't access the features on their subscriber Web site because I use Firefox!

---

### Post by lf82 on 2006-02-06
I'm with sympatico too , using a "basic" connection. ("Sympatico intermédiaire" for french folks).

I had to fiddle around a little in order to make evolution work. Here are my settings for **sending** mail:

-Server type : SMTP

-Host: smtphm.sympatico.ca

-Checked the "This server requires authentication" option

-Use secure connection (SSL) : Whenever possible

-Authentication type : "CLAIR". 
             I think this option is the french translation of "login". Anyway, if you press 
             the "Check for supported type" option, you'll end up with two choices :
             try both.

-Username : Type your complete mail adress ex : [email]john123@sympatico.ca[/email]

-Checked the Remember Password option, for convenience

**Note** : You'll be asked for your email account's password. If you don't know it, chances are you don't have a password yet. This is done through their website wich only supports IE. Call customer service if you need to. 


Sympatico's support for linux is ridiculous. They barely acknowledge the presence of alternative OS. Suffice to say I'm not renewing at the end of my contract.

And here my settings for **receiving** mail:

-Server Type : POP

-Host : pophm.sympatico.ca:995
            The *:995* extension at the end of the host's name specifies a port  
            number. pophm.sympatico.ca only accepts mail through port 995

-Username : Type your complete mail adress ex : [email]john123@sympatico.ca[/email]

-Use secure connection : Always

-Authentication type : Password

-Checked the Remember Password option, for convenience

B]Note[/B] : You'll be asked for your email account's password. If you don't know it, chances are you don't have a password yet. This is done through their website wich only supports IE. Call customer service if you need to. 

Hope this helps.

---

### Post by woodythdog on 2007-02-03
tryed all these suggestions with no luck on smtp 

here is what did work
[SIZE="4"]smtp1.sympatico.ca[/SIZE]

---

### Post by mvaranda on 2007-05-03
What worked for me for outgoing emails:

Server type: SMTP
Server: smtphm.sympatico.ca
(x) Server requires Authentication (checked)
Use Secure Connection: (TLS encryption)

Autthentication:
Type: (Login)
Username: [email]myaccount@sympatico.ca[/email]


Good luck

---

### Post by Hammystyle on 2007-07-13
> **mvaranda said:**
> What worked for me for outgoing emails:

Server type: SMTP
Server: smtphm.sympatico.ca
(x) Server requires Authentication (checked)
Use Secure Connection: (TLS encryption)

Autthentication:
Type: (Login)
Username: [email]myaccount@sympatico.ca[/email]


Good luck

Thought I would follow up on the subject.

This solution seems to be working for the server smtph.sympatico.ca using Evolution. Using No encryption or SSL encryption made me timeout when trying to send email but with TLS encryption, everything went through perfectly.

Thanks mvaranda!

---

### Post by pj12345 on 2008-06-01
Hello hello!

I used to have evolution working well with sympatico. Recently though I have become unable to send my mail using the same specifications described above. Could this be a problem with some settings on my computer or in evolution?

---

### Post by pj12345 on 2008-06-02
OK I just figured out the solution. I had to change my outgoing server to smtphm.sympatico.ca:587. I kept everything else the same.

---

