---
title: "Thunderbird IMAP Configuration with Comcast"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-08-03
Alright I dual-boot Windows XP and Ubuntu. I'm slowly trying to only use Ubuntu :-) 
A POP mail server downloads the e-mails onto my hard drive which I did not want, because I wanted to be able to view my e-mail from anywhere, originally from both OSs on my computer.  I decided to change to IMAP. To do that I  followed these steps.

1.Move my mail folder out out of my profile for Thunderbird.
2.Remove my account on Thunderbird.
3.Re-add my account under an IMAP account.
4.Move mail to IMAP mail folder under my Thunderbird profile.

My e-mail is there. but I am not sure what to use as an incoming server or port.

For a POP mail server I used mail.comcast.net and port 110? I believe.

For a IMAP mail server I tried using mail.comcast.net with the default port 143 and 110 and neither worked. I've looked around for the IMAP mail server to use with comcast but I cannot find it. 

One example is this site:

[http://kb.palm.com/SRVS/CGI-BIN/WEBCGI.EXE?New,Kb=PalmSupportKB,ts=Palm_External2001,Case=obj(37686](http://kb.palm.com/SRVS/CGI-BIN/WEBCGI.EXE?New,Kb=PalmSupportKB,ts=Palm_External2001,Case=obj(37686))

That site only provides an incoming and outgoing server for a POP mail server.
There are many sites that provide that as the incoming mail server to use for comcast.

The error message I receive when I try to get mail from the mail server is:

Mail server mail.comcast.net is not an IMAP4 server.

I hope Comcast supports IMAP mail accounts :-)

Edit: eh another problem. The e-mails are there but I can't view them :-(

---

### Post by charlesbrooking on 2007-08-04
> **SilverDragon said:**
> Mail server mail.comcast.net is not an IMAP4 server.

I hope Comcast supports IMAP mail accounts :-)

They might not provide IMAP, so you should check this first.

Given that IMAP means you store all your mail on their server instead of downloading it, they might only allow you to use POP to avoid having to provide hosting space.

---

### Post by SilverDragon on 2007-08-04
Well I found out the 3 types of services I use for e-mail do not provide IMAP. 
Comcast,Yahoo, and Gmail.

I remember reading in the Maximum PC magazine that you can set up an IMAP account with an AIM e-mail account, but does anyone else have any recommendations for which e-mail service to use for an IMAP account?

edit: I found on a web site that states:
"Gmail does not currently support IMAP, but the PHP IMAP functions can be used with IMAP as well as POP."

Does anyone know if that means there is a way around it to have IMAP functions, such as leaving e-mail on the server?

---

### Post by SilverDragon on 2007-08-06
Well I thought about it, and I realized it might just be easier to get the e-mails I have now downloaded back onto the server and just not use Thunderbird anymore. 

Is there a way to do this?

---

