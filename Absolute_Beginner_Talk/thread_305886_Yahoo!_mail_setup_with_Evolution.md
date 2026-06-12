---
title: "Yahoo! mail setup with Evolution"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2006-11-24
i have a yahoo account for my primary mail, i am completely new to linux, i just configured my wireless card (wmp54g) and got conky working but now it flashes on boot and disappears until i shut down the computer, but thats off-topic

can somebody help me set up my yahoo account to use evolution? i'll be honest, you'll probably have to hold my hand through it

thank you

---

### Post by verby on 2006-11-24
i'm not sure if you can... unless you have a premium account (pay). the same is with hotmail. to access your mail (pop fwd) only gmail allows it. anyone? correct me if i'm wrong.

---

### Post by adam.tropics on 2006-11-24
yes you can...hang on.!

---

### Post by adam.tropics on 2006-11-24
1. Go to Edit menu in Evolution and open Preferences.
2. Under Mail accounts, click 'add an account'
3. Follow the guide through. The servers are pop.mail.yahoo.com and smtp.mail.yahoo.com:587
4. On 'receiving email' you want 'no encryption'...and authentication type 'Password'..'Check for supported types'
5. On 'sending mail' choose 'no encryption', 'authentication type' PLAIN 'check for supported types'

and that's about it. Works for me anyhow!


ps. keep going with conky...it rocks!

---

### Post by livinginx on 2006-11-24
Do you have yahoo premium, or they allowing POP access to all accounts now?

---

### Post by adam.tropics on 2006-11-24
All accounts I believe....I don't pay for it anyway, if that's what you mean.

Also, my account is Australian, ie .com.au but it doesn't matter if I collect and send mail through .com servers or .com.au servers, it works either way, hence my assumption that it should be fine for any Yahoo account.

---

### Post by marx2k on 2006-11-24
Looks like Yahoo charges for this service in the states: 

Mail Plus

Get personalized spam filtering with SpamGuard Plus, 2GB storage, 20MB message size, no graphical ads, POP access and forwarding, and more great features for just $19.99/year - that's less than $2/month.

They used to allow it here but then they made it a pay service. :-?

---

### Post by adam.tropics on 2006-11-24
What do you get with [this link?]("http://advision.webevents.yahoo.com/mailbeta/")

---

### Post by gentlemanmasher on 2006-11-24
I have yahoo and gmail set up with evolution (though I use thunderbird primarily).  You do have to get the premium to forward your mail.  Go to yahoo and check there help menu.  Type in POP 3 and it will give you a list of email client (outlook,thunderbird,etc.).  This will tell you what you need to put into evolution to gain access.  

Thunderbird has less problems for me than evolution,plus yahoo and gmail have the walkthroughs.

---

### Post by eneth80 on 2006-12-11
> **adam.tropics said:**
> 1. Go to Edit menu in Evolution and open Preferences.
2. Under Mail accounts, click 'add an account'
3. Follow the guide through. The servers are pop.mail.yahoo.com and smtp.mail.yahoo.com:587
4. On 'receiving email' you want 'no encryption'...and authentication type 'Password'..'Check for supported types'
5. On 'sending mail' choose 'no encryption', 'authentication type' PLAIN 'check for supported types'

and that's about it. Works for me anyhow!


ps. keep going with conky...it rocks!



Hi,
I followed your instructions for my yahoo email account, putting the servers you wrote. It does not work. it gives me: 
"Evolution error 
Error hile performing operation
Welcome response error: Connection reset by peer"
And isn't it possible to have an Imap server for yahoo?
thanks
eneth80

---

### Post by AmandaKerik on 2007-02-02
I'd like to point out that if you use Thunderbird you can use an add-on that will let you download your yahoo messages (and others like hotmail, AOL, etc).

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

Be sure to follow the steps - set up the add-on's ports before the e-mail account's ports.

---

### Post by NewOldTimer on 2007-02-02
Newbie here, take with a grain of salt, I have yahoo premium and had to use smtp.sbcglobal.yahoo.com  and  pop.sbcglobal.yahoo.com... just set it up in evolution this morning. If this doesn't do it it for you re-read first 2 words of my post

rest of adam.tropics lines where the same for me

---

### Post by l951b951 on 2007-02-02
I can't remember the program, but on my windows machine I have a program that behaves like a pop3 server.  it downloads my mail from yahoo through an html interface (i think) and then i set my pop server for yahoo to local host.  there's one called ypops and there's another one called popfile or something like that.  I'm sorry I can't help more than that.
I would hope there is an analogous program for linux.  
If you find one, post it.

**Edit:**
Google to the rescue: 
> What seems to me a technically better solution is YPOPs, which functions as an incoming mail server on your local machine, so configuring mail clients to work with it should be easier.  YPOPs has pre-compiled verions for Windows, Mac OS, Solaris, and Linux-based systems.  If you're lucky, you may find someone has created a package for your GNU/Linux distribution.
  [http://computerclub.cex.com.au/node/21](http://computerclub.cex.com.au/node/21)

---

### Post by AmandaKerik on 2007-02-03
Webmail works the same way (basically) except it's Thunderbird only....

Ypops is hard to get onto Ubuntu, from what I've read - some odd / hard to find dependencies.

---

### Post by victorbrca on 2007-02-07
> **eneth80 said:**
> Hi,
I followed your instructions for my yahoo email account, putting the servers you wrote. It does not work. it gives me: 
"Evolution error 
Error hile performing operation
Welcome response error: Connection reset by peer"
And isn't it possible to have an Imap server for yahoo?
thanks
eneth80

I don't know if you are still having problems with this, but looks like you chose "IMAP" instead of "POP" on your "Receiving e-mail" tab. IMAP is a different type of service which is not provided by Yahoo.

Another thing to be cleared (that I also was not sure before) is that Yahoo is providing POP for the free accounts as well, however you need to go to "Options" on yahoo mail site (within your account) and enable it, otherwise it will not work.

Just make ur configuration look like these 2x pics and you should be fine:

**SMTP**
[[IMG]http://img252.imageshack.us/img252/8785/smtpvg7.th.png[/IMG]](http://img252.imageshack.us/my.php?image=smtpvg7.png)

**POP**
[[IMG]http://img408.imageshack.us/img408/377/popma9.th.png[/IMG]](http://img408.imageshack.us/my.php?image=popma9.png)



Vic.

---

### Post by McAbre on 2007-02-21
> **victorbrca said:**
> Another thing to be cleared (that I also was not sure before) is that Yahoo is providing POP for the free accounts as well, 

Vic.

My free Yahoo account says this at the options (POP & Forwarding) :

 Upgrade to Mail Plus  so you can:

    * download your Yahoo! Mail in an email client, such as Outlook
    * forward your Yahoo! Mail to a different address

I also want to find a dockapplet or something to tell me about arrived mail, But as of now, I'm relying on Gaim to do that.:/

---

### Post by AmandaKerik on 2007-02-21
> **McAbre said:**
> My free Yahoo account says this at the options (POP & Forwarding) :

 Upgrade to Mail Plus  so you can:

    * download your Yahoo! Mail in an email client, such as Outlook
    * forward your Yahoo! Mail to a different address

I also want to find a dockapplet or something to tell me about arrived mail, But as of now, I'm relying on Gaim to do that.:/

The lack of POP3 access on the free accounts is WHY this extension / add-on was created. You don't need to do anything in your Yahoo Mail account to get this add-on to work... 

With one exception - if you want it to grab ALL of your e-mails (backing them up, for example) you need to go into Yahoo Mail and mark them all unread / new.
Then in the settings for the add-on, you tell it to only grab the new / unread messages.

I also recommend changing Thunderbird's time out to 300 seconds (5 minutes) - this allows it to grab literally hundreds of e-mails at a time.

As for the notification issue - I just leave Thunderbird running and let the system beep when there's new mail. You might want to put it on your second desktop if you don't like task bar clutter.

You may end up with the occational duplicate e-mail - especially when changing settings. I recommend the "Remove Duplicate Messages 0.1.02" add-on / extension. It's found here:
[https://addons.mozilla.org/thunderbird/956/](https://addons.mozilla.org/thunderbird/956/)

Here's my Thunderbird stats:

Application: Mozilla-Thunderbird 1.5.0.9 (2007010421)
Operating System: Linux (x86-gcc3)

- English (GB) Language Pack 1.5.0.2
- Remove Duplicate Messages 0.1.02
- Adblock Plus 0.7.2.4
- WebMail - Yahoo 1.1.15
- WebMail 1.0.15
- Stylish 0.4
- Restart Thunderbird 0.9
- Thunderbird Message Filter Import/Export 1.0
- Attachment Sizes 0.0.5
- QuickFolders 0.3
- FoxyTunes 2.2.5
- Adblock Plus: Element Hiding Helper 1.0
- Extension List Dumper 1.8.0

Let me know if there's anything else you need help with by posting your question in this thread - I'm always watching it.

---

### Post by tskariah on 2007-04-08
To access Yahoo emails with Evolution or other email clients, you could use YPOPS!. The debian package for Ubuntu is available here: [ypops_0.8.8-1_i386.deb]("http://www.geocities.com/t_skariah/ypops/")

---

### Post by eneth80 on 2007-06-15
"Another thing to be cleared (that I also was not sure before) is that Yahoo is providing POP for the free accounts as well, however you need to go to "Options" on yahoo mail site (within your account) and enable it, otherwise it will not work."

Yes Sir, I still have the same problem.
This means that I have to pay a yearly fee to get the POP and forwarding thing?
now I try again with Ypop . 
regards,
ale

---

### Post by AmandaKerik on 2007-06-15
Hi, you came here to read this reply... now scroll up and read the last few entries... especially mine.

---

### Post by eneth80 on 2007-06-15
ok so I cannot have yahoo! mail give me the pop service for free. at this point I would like to use ypops. what should I do after the installation? I would like to have Gnubiff or Evolution notify me. 
Thanks
ale

---

### Post by zzztownsend on 2007-06-15
Hi folks

I use the yahoo mail service in the UK (free version as in free beer :P ) 
Under options I can select for my account to be accessible as POP / SMTP
Links on the page describe how to configure Outlook which work equally with Evolution

Hope this helps someone even if it doesn't sound from the postings above like it is applicable in USA.

Cheers

Matt

---

### Post by forestpixie on 2007-06-15
Certainly helped me - never ever managed to get it to work anywhere else! 

:)

---

### Post by rfurman24 on 2007-06-15
Freepops is another. I use it with thunderbird. I could help set it up if interested.

---

### Post by loell on 2007-06-16
ypops deb

[http://www.geocities.com/t_skariah/ypops/index.html](http://www.geocities.com/t_skariah/ypops/index.html)

---

### Post by amlucent23 on 2007-07-29
Has anyone successfully set up ypops with evolution? I cant get it to download mail. I suspect it is the server timeout (as it advises to increase duration in the email clients preferences. However, I can not find this option anywhere in evolution. :(

can anyone find and submit a how to?

---

### Post by Chymera on 2007-07-30
free yahoo mail provides POP acces, you get everything under options.

the servers are of the form:
pop.mail.yahoo.<whatever your regional code your address gas com/de/au/us>
smtp.mail.yahoo.<whatever your regional code your address gas com/de/au/us>

---

### Post by youbecha on 2007-07-31
Apparently the US version of yahoo is different...

This is what I get when I click on the POP link...

> We Apologize
The service you are requesting is not currently for sale.
We apologize for the inconvenience.



I ended up installing Wine...and loading ypops with that...

BTW (Evolution) for POP authentication it is "password"...for SMTP it is "login"

---

### Post by Chymera on 2007-08-01
you may be right, i only tried with .de, .es, .com, .com.au, and .co.uk... However, I dont see why yahoo would discriminate against americans :P 

The pop link you are talking about is actually named "POP Access and Forwarding" and is in the second column under ->Options ... right?

---

### Post by sidcypher on 2007-12-13
That is correct all you Worldly Ubuntu Users, in the States, POP access is a pay service. It has been that way for about 5-6 years now.

I have gotten the newest ypops installed and running, however evolution is encountering a error much like the first post had, input/output....

I even tried installing Thunderbird, but it won't let you select localhost as your server, comes up with "please enter valid domain," something like that...

So although I didn't want to use webmail, cause I was spoiled on windows with ypops...I downloaded that...Can't get it working either, when I try to download the yahoo plugin for it tells me it is a invalid package file.

Go figure...Does anyone in the States have evolution working with ypops? Cause I didn't like Thunderbird on Windows, don't like it on Unbuntu...

Thx
Cypher

---

### Post by bhold on 2007-12-13
Well I am not an expert on this but did look into it very briefly - was told by someone who knows about  this  that I would need to pay yahoo for pop access, but could get it for free from google. (This is in the U.S.)

So my current plan, when I get around to using evolution, would be one of the following...
1. Switch completely to google mail, or
2. Forward my yahoo mail to google mail, or
3. Pay for yahoo extended mail service or whatever they call it

Just passing along what I was told, I have not gotten this working yet.

---

### Post by victorbrca on 2007-12-14
My working configuration...


[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/yahoo-mail/yahoo1.png[/IMG]


[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/yahoo-mail/yahoo2.png[/IMG]


[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/yahoo-mail/yahoo3.png[/IMG]


Vic.

---

### Post by Beaker Boy on 2008-02-14
Hi, Numpty Noob here again!  I've been following this thread through and there seems to be a lot of conflicting advice. I suppose I'm asking can we connect to our free Yahoo Mail accounts in the UK (mine is a ***@yahoo.com) using Evolution? And if so what are the recieving and sending servers?  Any help is much appreciated.

Beaker Boy

---

### Post by anandbabu20 on 2008-02-16
Yahoo! plus is a must for fetching through evolution. And we have pay for it too. It is better to switch to gmail. If you have a Plus account in yahoo, the steps described in earlier posts will work fine.

---

### Post by victorbrca on 2008-02-21
I've heard that depending on location, YahooMail does not offer pop accessing on the free version of their email. You could try changing your account to yahoo.ca for example. The free version does allow you to use pop.


Vic.

---

