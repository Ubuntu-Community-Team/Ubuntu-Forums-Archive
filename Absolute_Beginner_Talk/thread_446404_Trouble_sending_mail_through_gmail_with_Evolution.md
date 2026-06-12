---
title: "Trouble sending mail through gmail with Evolution"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by eatlotsoffruits on 2007-05-16
Newbe here with a problem sending mail through my gmail using Evolution.

I've set it to receive mail just fine but every time i try to send mail I get this warning:
"Error while performing operation.
MAIL FROM command failed: Must issue a STARTTLS command first 26sm3413623wra"

i've tried using the gmail smtp server for outgoing mail.  that didn't work.
my ISP is comcast and i've tried to use them as my smtp server.  I've tried every combination i can think of or that i've found through google: mail.comcast.net, mail.ma.comcast.net (i'm in massachusetts), mail.comcast.com, etc, and none of them work.

Anyone else have this problem and/or have a solution?

---

### Post by newlinux on 2007-05-16
The following settings work for me:
[LIST]
[*]server type: SMTP
[*]smtp.gmail.com
[*]Have "Server Requires Authentication" checked
[*]Using SSL encryption
[*]Authentication type: PLAIN
[*]full email address as username.
[/LIST]

---

### Post by Austin_KW on 2007-05-16
or as above using the secure port/
smtp.gmail.com:465

---

### Post by eatlotsoffruits on 2007-05-16
Thanks for the attempt, newlinux, but that didn't work either.

Could this simply be an issue with Evolution?  Or would i have the same problem if i were to switch to Thunderbird?

---

### Post by eatlotsoffruits on 2007-05-16
Thanks to you, too, Austin_KW, but that's not working either.

---

### Post by newlinux on 2007-05-16
probably not a problem with evolution, as that's what I'm using. What version are you using? Have you been able to send email with gmail from another client?

---

### Post by wormser on 2007-05-16
I think with gmail you have to enable smtp.  Take a look around the account preferences in gmail.

---

### Post by Austin_KW on 2007-05-16
or try 
smtp.gmail.com:587

---

### Post by eatlotsoffruits on 2007-05-16
I'm running Evolution 2.10.1 and running Ubuntu 7.04 Feisty Fawn.  Just installed it yesterday. I've never tried to use another program like Outlook (when i was on windows) or Thunderbird to handle mail but thought I would give it a shot.

I couldn't find anything in the gmail preferences about enabling smtp.  Out of curiosity i checked out their instructions for setting up other clients and all of them say to use "smtp.gmail.com" as the smtp server, but that's no good for me.

---

### Post by eatlotsoffruits on 2007-05-18
Anyone else have any ideas on what could be wrong and/or specifically what that error message i get is trying to say?

Thanks for the attempts up to now.  I know it seems like this is a simple problem with an easy fix, but nothing's working for me.  Is anyone else having this problem with gmail, Evolution, or Comcast?

---

### Post by Austin_KW on 2007-05-18
maybe you isp is blocking access

try making a connection using 'telnet address port'
telnet smtp.gmail.com 25
or
telnet smtp.gmail.com 587
or
telnet smtp.gmail.com 465

do any of these connect?

edit; BTW, I mean try using telnet from the command line/ terminal

---

### Post by eatlotsoffruits on 2007-05-18
it seems to work....pardon my ignorance but i'm not sure what should happen when it works.  here's a copy and paste from my terminal window:

telnet smtp.gmail.com 587

Trying 66.249.83.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP h9sm2470772wxd

and then i have a blinking cursor afterward.  but when i put "smtp.gmail.com:587" as my smtp server, it's still rejecting my attempts to send mail.  does that give you any more information?

---

### Post by eatlotsoffruits on 2007-05-22
I went ahead and installed Thunderbird 2.0 and set it up to work with my gmail.  no problems whatsoever when i use the setup newlinux suggested:

Server Type: smtp
smtp.gmail.com
check box "Server Requires Authentication"
use SSL encryption
Authentication Type; Plain
full email address as username
"remember my password" checked.

So now i can send and receive mail from my desktop.  Thanks, everyone, for your help!

before i check this as "resolved," i'd still rather use Evolution since it will sync with my Palm Pilot (am i mistaken in thinking that Thunderbird doesn't have a calendar, reminder list, memo pad, etc?).  Given that i've gotten email to work fine with Thunderbird and given all of the previous posts about Evolution, does anyone now have any more clues as to what i could do to fix Evolution?

---

### Post by Prisma on 2007-06-13
I just want to add that the posts on this thread helped me to solve this issue. You have to anable pop3 in your gmail account and in the smtp preferences on evolution make sure that you have typed your full account name in username (for example: [email]jonhdoe@gmail.com[/email])

---

### Post by QwUo173Hy on 2007-06-14
I also can not send mail anymore with Evolution. It has been working fine for  the last few months since I installed Feisty Fawn. As of about midnight tonight, I can not send mail through my google account.

I tried the telnet trick and it worked. I also checked my settings but I knew they were correct as I had to do a lot of reading to set up Evolution in the first place.

I have had this problem with Evolution on Edgy as well and changing client solved the problem (Thundebird / Claws mail).

If things haven't improved by tomorrow, I may change clients and file a bug report. But as someone already said - I like Evolutions interface above all the others and would rather not change.

---

### Post by QwUo173Hy on 2007-06-14
Turns out to be a Gmail issue. They won't let you send mails containing .exe files. I was sending a zip file but there was an exe in there I didn't know about.

---

### Post by J-P on 2007-06-16
hey, 

I'm having the same problem with Evolution (i think). I'm also having the same error with Thunderbird. Identical settings work on my windows box under thunderbird and outlook.

telnet connects.

I have tried all settings listed in this thread so far. I take it the difference between googlemail / gmail is irrelevant as both seem to come up with the same error.

"Unable to connect to POP server pop.gmail.com.
Error sending password: -ERR [AUTH] Username and password not accepted.

Please enter the POP password for [email]johndoe@gmail.com[/email] on host pop.gmail.com"

POP is enabled under the gmail account in question. I've tried pop settings specifying ports and plain jane. Neither work.

Am I being dumb and missing something really stupid?

//Edit : Now, I KNOW this is a problem with gmail. I have tried this on my laptop running the same latest versions of ubuntu + evolution. My other gmail account logs in no problem, on both machines. I've tried changing the password for the obstinate account.

Anyone have any clue how to get this working?
//Edit

---

### Post by 11touche on 2007-08-04
I had problems with SMTP on gMail, but the trick given here to put smtp.gmail.com:465, server require authentication, SSL encryption, type PLAIN, and full e-mail adress as username worked right away for me.

---

### Post by Kapitän Rotbart on 2008-02-13
Well, Newlinux's post helped me getting Gmail in Evil-ution to work :P

I just had to do Edit>Preferences, then under the Mail Accounts section, edit the existing account and under the "Sending Email" tab, all I had to do was select "SSL Encription" for using a secure connection under "Security". If you can read emails in Evil-ution but not send 'em, there's a huge probability that this would be the only thing to configure in order to get it to work.

---

