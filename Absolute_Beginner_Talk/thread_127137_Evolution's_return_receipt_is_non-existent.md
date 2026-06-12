---
title: "Evolution's return receipt is non-existent?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by user_of_gnomes on 2006-02-08
This has been bothering me for quite a while, and it does not seem like the Evolution support page is of any use at the moment. 

I can have other people request a return receipt from me, but I can't request a return receipt from other people.  I have sent out a few E-mails and never got a reply. I do not know whether this is because they have chosen *not* to reply or simply because the E-mail never arrived. A return receipt will help me sleep better at night. 

Is there a plug-in I need to install or perhaps an option I overlooked? 

Thanks in advance!

---

### Post by nocturn on 2006-02-08
I haven't checked recently, but in the past they refused to implement this because their is no standard for it (there are actually a couple of headers that trigger it).

---

### Post by user_of_gnomes on 2006-02-08
[QUOTE=nocturn]I haven't checked recently, but in the past they refused to implement this because their is no standard for it (there are actually a couple of headers that trigger it).[/QUOTE]

Hello, Nocturn.

What do you mean when you say "*There are actually a couple of headers that trigger it*"?

---

### Post by digitalmouse on 2006-05-17
[QUOTE=UbuntuRaptor]What do you mean when you say "*There are actually a couple of headers that trigger it*"?[/QUOTE]

I can answer that one I think.   In the standards that cover what is allowed in email headers (where the To, From, Subject, and other related info resides above the actual text content of the email), there seems to be several ways to send a 'return-receipt' request to the receiver of the email.

Having worked with email routines in PHP a lot, I know that programmatically adding a header to outgoing email that reads "Return-Receipt-To:" followed by the email address I want to use to get the receipt (usually the same as the sender) seems to work for most of the popular email clients out there.  Your mileage may vary.

Maybe, *just maybe*, you could embed an RR header into your email in Evolution, but I cannot think of a way to do that at the moment.

It is a shame that Evolution does not include the ability to send RR's.  Maybe they will have a change of heart on the future.  Even though there may be different ways of marking a RR email, the possibilities are few and could be solved with a little bit of smart programming I feel.

The alternative is to stick with something like the latest Thunderbird.

---

### Post by cstudent on 2006-05-17
[QUOTE=UbuntuRaptor]This has been bothering me for quite a while, and it does not seem like the Evolution support page is of any use at the moment. 

I can have other people request a return receipt from me, but I can't request a return receipt from other people.  I have sent out a few E-mails and never got a reply. I do not know whether this is because they have chosen *not* to reply or simply because the E-mail never arrived. A return receipt will help me sleep better at night. 

Is there a plug-in I need to install or perhaps an option I overlooked? 

Thanks in advance![/QUOTE]


When composing an email message look under the Insert menu. At the bottom is the option to request a return receipt.


cstudent

---

### Post by user_of_gnomes on 2006-05-17
Heck, you're right! Thanks for digging up this thread, Digital and thanks for the solution Cstudent. :D

---

### Post by digitalmouse on 2006-05-17
heh- i've been using Evolution for about 6 months, and i never noticed that!

thanks cstudent!

---

