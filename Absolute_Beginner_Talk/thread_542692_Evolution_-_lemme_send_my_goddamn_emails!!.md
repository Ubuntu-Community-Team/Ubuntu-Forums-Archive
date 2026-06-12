---
title: "Evolution - lemme send my goddamn emails!!"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by razorednight on 2007-09-04
Just lately, Evolution won't let me send emails (thru googlemail's server).. I can receive the mails sent to me. But I can't send anythingto help, it seems..  It all worked before, to very recently.

Can anyone please suggest how to fix it?

I'm using Ubuntu.

---

### Post by mlentink on 2007-09-04
Your ISP has not, by any chance, recently decided to block port 25? There is an increasing amount of ISP that prevent any port 25 activity other that their own mailserver and their own accounts. Try sending mail through your ISP's SMTP server.

---

### Post by razorednight on 2007-09-04
Unfortunatelt my "isp" is mt cellphone service provider, so the obly way I can send emails thru them is by using  evolution mail.  How can I discover if my "isp" has stopped port 25.

Any ideas?

---

### Post by monsieurdozier on 2007-09-04
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

I believe this should let you see if Port 25 is open.

Monsieur Dozier

---

### Post by mlentink on 2007-09-04
Has your cellphone provider supplied you with server details? Did they give you an email-account? If so, they must have supplied you with the details of their SMTP-server. You can use any email program to send emails, such as evolution, thunderbird, pine, mutt and a host of others, but each of these will need to be supplied with the name of a smtp-server.

---

### Post by razorednight on 2007-09-04
I checked Port 25 on [www.canyouseeme.org](www.canyouseeme.org) and got reply "Couldn't see your service on Port 25 (reason: connection died out)".  Does this mean my ISP has started blocking Port 25 then?  I used to be able to send email through Evolution, SMTP, for my gmail account.  So they've recently blocked my Port 25?  Is there a solution?

BTW mlentik: about my other post - I kinda forgot I'd done this one.  *shame*

---

### Post by razorednight on 2007-09-05
On further investigation, it can't be that they have blocked my port 25 to stop me running a stmp server.  It's a stmp client i am running - sending email out of evolution by stmp, which gmail then receive.  The no-ip "solutions" mentioned at [www.canyouseeme.org](www.canyouseeme.org) are for people who want to run their own email servers from home, or who want to run a web server from home.

Please, has anyone got any idea how I can once again send my email, via smtp, thru gmail?  Is there anyone here who at the present time can send email, from evolution, thru a gmail account, to other people?

HELP!!!

---

### Post by timdoc1 on 2007-09-06
Just an FYI..

I am using Suse on my laptop (with Evolution).  I can recieve pop from Comcast, but can not send via smtp (smtp.comcast.net).  The 'help' desk , I use that term loosely lol, said to check that I am using port 25, otherwise authentication is required.  On the other hand the Prepared Comcast Info  -http://www.comcast.net/help/faq/index.jsp?faq=EmailOutlook_Express17739&CM.src=esupm

spells out different ports.  Since I can't seem to find these settings in Evolution, I am stuck.

---

### Post by victor9098 on 2007-09-07
Hi All,

The exact same problem has happened to me, started about 2 weeks ago. Used to be able to send no problem.

I logged it as a bug on launchpad but got a telling off! That is was not a bug and my settings were wrong. I had not altered them and I have tried every "how-to" I can get my hands on.

Is there anyone out there with a solution to this??? Please no more links to "how-to" sites! I am sick of having to navigate to gmail just to send an email.

Evolution is by far the best email/contacts/calendar for the Ubuntu OS, I do not want to give it up over this.

Any help would be much appreciated.

---

### Post by victor9098 on 2007-09-07
OK....

Maybe I got lucky...have a look here:

[http://ubuntuforums.org/showthread.php?t=342779&highlight=Evolution+Gmail+smtp](http://ubuntuforums.org/showthread.php?t=342779&highlight=Evolution+Gmail+smtp)

I have just tried inputing the values listed. Now I just need someone to send an email to :)

---

### Post by timdoc1 on 2007-09-24
Anyone with Comcast specific help?

---

### Post by HermanAB on 2007-09-24
You can test a mail server using telnet:
$ telnet mail2.aeronetworks.ca 25

My server also listens on port 2525 to get round these ISP blocks:
$ telnet mail2.aeronetworks.ca 2525

If you receive the banner then obviously you can connect to the server.  If nothing happens, then your ISP or another intervening firewall (maybe your own) is blocking the port.  

Like this:
[herman@odin ~]$ telnet mail2.aeronetworks.ca 25
Trying 142.59.19.120...
Connected to mail2.aeronetworks.ca (142.59.19.120).
Escape character is '^]'.
^]
telnet> q
Connection closed.

Using my server above you can quickly see whether port 25 is blocked or whether it is another problem.  (You won't be able to forward mail through my server, since it needs authentication!)

You can figure out where a connection is blocked by using 'traceroute', which is a kind of improved 'ping'.

Cheers,

H

---

