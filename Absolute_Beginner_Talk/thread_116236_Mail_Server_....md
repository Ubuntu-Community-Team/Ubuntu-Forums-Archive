---
title: "Mail Server ..."
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by wannabelinuxconvert on 2006-01-12
Hi,

I'm a newbie to Linux ;) and would like to set up a web and mail server.

The web side of it I reckon I can figure out myself, but I've never set up a mail server before, let-alone one on Linux, so I'm looking for a bit of guidance.

I'm running Kubuntu on my mac-mini. I will first set up apache2, php and mysql.

I've seen a how-to on the wiki, and read a couple of how-to's I found whilst googling, but non of them covered my setup. You see, because my IP is dynamic I've had to set up an account with dyndns.org and need to know if this will affect anything, and what to do as a work around if it does. I'm also sat behind a network, so know to open port 25 on the router, set a static ip to my box and divert port 25 traffic on the router to port 25 on my box as I had to do with with port 80 for the web server stuff.

Any help would be greatly appreciated.

Cheers

Mic

---

### Post by frodon on 2006-01-12
[http://www.ubuntuforums.org/showthread.php?t=97600](http://www.ubuntuforums.org/showthread.php?t=97600)

---

### Post by wannabelinuxconvert on 2006-01-12
Thanks for the pronto repsonse ... I have seen this thread, and it may be me being blind, but does it cover the issue of using a service similar to DynDns as I can't for the life of me see it ?!

Cheers

Mic

---

### Post by JakeSpeare on 2006-01-12
DynDNS should not matter as long as you have a little client running that updates your dynamic ip to the domain name you are using.  Other than that things will work the same.  Just make sure that you use your domain name when referrring to your machine in any set up and not the actual ip it has.  To make things work easiest, set the dmz on your router to your server.  This should avoid the need to port forward.  Just make sure you have netstatted your machine and closed any ports that you dont need or want open.

---

### Post by frodon on 2006-01-12
For DynDNS i followed this way : [http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip)

---

### Post by wannabelinuxconvert on 2006-01-12
Hi guys,

Thanks all for the replies.

The reason I have concern around the dynamic IP is the main article I've been looking at is [http://www.hypexr.org/linux_mail_server.php]("http://www.hypexr.org/linux_mail_server.php") and on it is states ...

> A note for those with dynamic IP addresses: Before installing Postfix we must first consider if it will need to make use of Simple Authentication and Security Layer (SASL). If you have a dynamic IP address and are using a service like dyndns.org you will need to have Postfix send your mail through your ISP's mail server (with authentication) making use of SASL for the connection. This is because many domains that you will send email too will recognize your hostname as pointing to a dynamic IP address and send the mail back. Check if your distributions Postfix package was built with SASL support or if you are compiling Postfix from scratch add SASL with a ./configure option

Is this the case with the HOW-TO guide !? 

As on this guide it shows you setting up a file with your webproviders SMTP details, but on the HOW-TO on the Wiki it doesn't !?

> Generate the database. From /etc/postfix dir:

$ postalias aliases  

Set up smtp server and authentication for SBC mail relay. sasl_passwd:

smtp.sbc.mail.yahoo4.akadns.net    [email]my_username@sbcglobal.net[/email]:my_passw

I would follow this guide, but it's designed for ArchLinux and I'm not experienced enough to see/make any changes for the Ubuntu distribution. For sure, there may be no need to make any changes, but if the setup doesn't work when completed, it could be because I have missed a needed change but won't know where to trouble-shoot :confused: 

Cheers

Mic

---

### Post by rosschilen on 2006-01-12
Hey, I have started to follow this guide: [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/").  I think its too complicated for what I need to do. My server needs to retrieve pop email from my ISP's (road runner) server.  It needs to have webmail (squirrelmail) and have the capability for to be a smtp server for the emails it retrieved from my ISP.  Only one user/email address will be used.  Also I won't be sending emails through this server.  Should I follow this guide or is there something simpler?

---

