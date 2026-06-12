---
title: "Email Server configuration"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by ambre on 2008-01-20
This is my first post so please excuse my inexperience.

I want to set up Ubuntu as an e-mail server for the family.  We all have our own computers, running WINXP, different e-mail addresses and different ISP's.  I have followed the howto to set up the 'Perfect Server 7.10' and everything works (now that I have set a static IP address on the LINUX box and removed Network Manager) except that non of us can get MS Outlook to access the pop3 server. Outgoing test messages do get sent.

I have searched the forums for answers but as yet nothing I have tried makes it work.  As a complete newby to LINUX I am struggling to find configuration files, log files, etc. and would appreciate any step by step assistance to resolve this impass.

My responses might be slow but I will respond.

Thank you.

---

### Post by HermanAB on 2008-01-20
Citadel is the easiest mail system to install on Linux: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

See all the threads on Citadel in the Servers an Security forum.

Cheers,

Herman

---

### Post by blueridgedog on 2008-01-20
Perhaps to help myself and others understand what could be working and not working, could you give an overview of what software packages you installed to create your server?  What are you using for an MTA and what are you using to provide mailbox access, a POP server?

Also, when you attempt to connect, are there specific errors you can add?

---

### Post by ambre on 2008-01-21
Herman,

Thanks for your suggestion, but at this time I would prefer to resolve my existing problems rather than install new software.

---

### Post by hyper_ch on 2008-01-21
> **blueridgedog said:**
> Perhaps to help myself and others understand what could be working and not working, could you give an overview of what software packages you installed to create your server?  What are you using for an MTA and what are you using to provide mailbox access, a POP server?

Also, when you attempt to connect, are there specific errors you can add?

Well, first we need to know what's working and what is not working. How your whole system is setup... what guide you did follow and to what extend, what is the configuration of your mail clients....

---

### Post by ambre on 2008-01-21
Hi blueridgedog,

I have basically followed [http://www.howtoforge.com/perfect_server_ubuntu7.10]("http://www.howtoforge.com/perfect_server_ubuntu7.10") to set up my server.  I have not installed ISPConfig.

I am only interested in using the LINUX box as an email server at this time so I am not sure how much of this is working correctly.

What I do know is when I try a test message from any WINXP computer using the LINUX box as the mail server I get a fatal error that tells me Outlook is unable to connect to the incoming mail server (POP3).  However, the test message does get sent.

I suspect some sort of authentication error, but I am only guessing and I do not know how to troubleshoot the problem.

Any assistance would be greatly appreciated.

---

### Post by hyper_ch on 2008-01-22
unable to connect doesn't mean that much...


how is the account setup? How is smtp setup? Are you sure you have setup a pop3 server and not a imap one?

---

### Post by HermanAB on 2008-01-22
Hmm, a mail system consists of many protocols executed by many separate servers.  The receive and transmit process is completely independent and can even run on different machines.  The situation is further complicated by ISPs discouraging home users from running mail servers, in a somewhat misguided attempt to reduce spam and increase revenue.

A typical home system cannot directly send and receive mail, since the ISP typically blocks incoming communication on port 25 and only allows outgoing communication on that port to their own mail server.  So, in a home system, you have to use your ISP mail server, unless you pay them extra money for a 'server' account.

On a low cost home account, to send mail from a mail client (Outlook, Thunderbird) the client connects on port 25 to the ISP mail server.  If you run your own Mail Transport Agent (MTA) (Postfix, Qmail, Citadel), then you have to tell this MTA to relay outgoing mail via the ISP mail server.

Incoming mail is received by the ISP mail server and delivered to mailboxes - one per user.  Home users can then use a mail client to fetch the mail using POP3 or IMAP protocols.  You could also use a program called 'fetchmail' (together with procmail) to get mail from several mailboxes and deliver it to local mailboxes.  Citadel has a fetchmail feature built in and could be used as a home mail server without having to bother with fetchmail and procmail.

Sooooo, to make a long story short, you could painstakingly build a simple home mail server from postfix, fetchmail, procmail, apache, dovecot, amavisd-new, spam assassin, clamav, dcc, razor and squirrel mail (or roundcube).  Doing so, will take you at least 2 weeks of full time effort (if you are new to Linux, then it could take much longer), but it will be a very educational experience.  

Alternatively, you can install Citadel and have it all done in about 20 minutes using Easy Install. (If you like to tinker and learn something, then you can use Queezy Install for the debug version, but this is not recommended for freshmen).

Your choice.

Cheers,

Herman

---

### Post by hyper_ch on 2008-01-22
> **HermanAB said:**
> A typical home system cannot directly send and receive mail, since the ISP typically blocks incoming communication on port 25 and only allows outgoing communication on that port to their own mail server.  So, in a home system, you have to use your ISP mail server, unless you pay them extra money for a 'server' account.
That depends pretty much on your ISP. There was a long time ago when it was here the same. Meanwhile cable providers do not block anything anymore. So I could easily setup my server at home also.

> **HermanAB said:**
> On a low cost home account, to send mail from a mail client (Outlook, Thunderbird) the client connects on port 25 to the ISP mail server.  If you run your own Mail Transport Agent (MTA) (Postfix, Qmail, Citadel), then you have to tell this MTA to relay outgoing mail via the ISP mail server.
If I could only relay my outgoing mail trough my ISP I would have quite a few issues. I have two servers rented and I'm exclusively sending through them. With SPF setup on my servers I would have troubles sending any mails to someone whose server do enforce SPF policies. Furthermore you have many mail providers that let you use POP3/IMAP & SMTP. I tend to think a isp can't afford anymore to "outcast" such users.

Besides, if he setup the server in his lan for testing then ISP policies won't apply for lan stuff. Problem is I still have no clue what his setup is like.

---

### Post by ambre on 2008-01-22
Hi guys,

Let me give you a bit of background.

I used to have a pice of Windows software from Software602 called LAN Suite.  This was free for a 5 user home system (it is now chargeable) and this is what I used as my email server.  It had been running for years on what is now the LINUX box until the hard disk crashed and had to be replaced.  I could configure user's email accounts in LAN Suite and periodically it would collect our mail from our ISPs using POP3 and store it locally.  MS Outlook would then collect mail from LAN Suite using POP3 and send outgoing mail to LAN Suite using SMTP which would be relayed to our ISP's.  LAN Suite authenticated users to avoid open relay senarios.

As I said earlier, LAN Suite is no longer free. As I don't have the license key any more to reinstall the software I thought I would investigate LINUX.  When I saw the 'Perfect Server' howto I thought this was what I needed and decided to give it a shot.

If I am on the wrong track here please let me know.  However, if this server setup will do what LAN Suite used to do I would prefer to persevere with it and learn more about LINUX and internet mail systems at the same time.  Citadel seems to be the easy way out, but for the moment I would like to consider it a future option.

What can I use and where do I look to see what is happening on the LINUX box when MS Outlook is trying to establish a POP3 connection?  In particular, how would a WINXP user get authenticated?

It is so frustrating.  I know what I want to investigate but I don't know how to do it. ARGH!

Thanks for your interest.

---

### Post by dysolve on 2008-01-22
you need to setup something like ispconfig to enable the pop3 part of linux as such.. Did you buy a domain or do you want to use the isp you have pop3 mail accounts and just have your sever download (relay) them for you?

---

### Post by ambre on 2008-01-22
Hi dysolve,

I do not own a domain name.  We all have different ISPs (compuserve, btconnect, vodafoneemail) and email addresses but I have found that if I routed everything through my ISP using my POP3 account all the emails would get delivered.

---

### Post by drhiii on 2008-01-23
I hope I don't get slammed for adding to this thread, but it is applicable....

Am also looking to set up a simple mail server.  Running Ubuntu Server v7.10.  Went through an installation for Postfix/Dovecot, etc....   Postfix appears to be working fine.  Sending email out with no problem.  Got to Dovecot and installation broke.  Cannot uninstall, reinstall, clean, remove, anything.  Getting broken dependencies.  Dunno if just replacing the /etc/postfix/postfix.conf file will work (made a run at it but it didn't).

Placing the latest pass at dovecot install below.  But my question is... anyone drill into how to fix dovecot, or.... recommend an easy Mail server program with pop3, that also defends against spam and virii?  Everything was going swimmingly until Dovecot broke and I can't break out of the remove/install circling.  

Help?





Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dovecot-pop3d
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
1 not fully installed or removed.
Need to get 588kB of archives.
After unpacking 963kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main dovecot-pop3d 1:1.0.5-1ubuntu2.1 [588kB]
Fetched 588kB in 1s (297kB/s)         
Selecting previously deselected package dovecot-pop3d.
(Reading database ... 199736 files and directories currently installed.)
Unpacking dovecot-pop3d (from .../dovecot-pop3d_1%3a1.0.5-1ubuntu2.1_i386.deb) ...
Setting up dovecot-common (1:1.0.5-1ubuntu2.1) ...
Not replacing deleted config file /etc/dovecot/dovecot-ldap.conf
chmod: cannot access `/etc/dovecot/dovecot-ldap.conf': No such file or directory
dpkg: error processing dovecot-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.0.5-1ubuntu2.1); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-common
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drhiii on 2008-01-23
Also, I am now getting the following request to insert a CD:

Need to get 0B/175kB of archives.
After unpacking 291kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter


Things kinda deteriorating... and I was SO close to getting the server the way I needed it.

Help?

---

### Post by hyper_ch on 2008-01-23
uncomment the cd in your sources.list

---

### Post by ambre on 2008-01-23
Hi guys,

I am happy to say that my problem is now sorted and my email server is working as I expected it to.

For anyone who may be following this thread the solution was that courier-pop had not installed.  I traced this by using 'netstat -l (lower case L) | grep tcp' to list the sockets that were listening and found no reference to pop3.  After installing courier-pop and doing some configuration to ensure courier and postfix knew where to find the user 'mail directory' everything fell into place.  LINUX is now collecting our mail from various ISPs at regular intervals (fetchmail and cron), storing it locally and MS Outlook picks it up from LINUX when we use our WINXP machines - GREAT and all for free!

Like all newbies I have a very steep learning curve.  My advice would be to persevere - it's a real buzz when things start working.

Bye for now.

---

### Post by hyper_ch on 2008-01-23
well, getting an email server installed, configured and running is somewhat challenging... once you've done it 2-3 times it gets a lot easier.

---

### Post by zazuge on 2008-03-02
Well you're a lucky one
I wasted 4 weeks to setup fetchmail and postfix properly
so could you post here how you did it ? , so the rest of us can benefit from your exprerience.

---

