---
title: "postfix,mysql,courier-imap, sasl and LDAP"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Peque on 2007-08-19
Well - hey Forum. 

I'm trying to set up a mailserver that have the following requirements: 

Should be able to handle virtual domains.
Should Autherize when sending mail, and when logging into the mailserver. 
Since I use a Lexcom as my server - I'm in need of running Ubuntu 6.06 LTS ! 


I have looked around and found several guide's but none of them seems to work with sasl auth or TLS? Each time I just run into that the password ain't validating - I have several times get a mailserver up and running without the Auth on SMTPD - but since I need to validate my users all over the country It's a must that the sender is autherized. Even though I can see that everything works - It's still don't get the right password - funny enough I can login and see my mail with the same password - so something is working - BUT what goes wrong in the auth of smtpd??? I can see from my mysql.log that each request are handlet correct - but still no permission to send mails. But the same password should go both ways - but at this point and 8 different guides later - I still get the same problem about not beeing able to autherize my outgoing mails with SASL or anything like it??? And I do not know what is going wrong anymore: 

I have tried these guides: 
[http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL#authmysqlrc](http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL#authmysqlrc)
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
[http://workaround.org/articles/ispmail-etch/](http://workaround.org/articles/ispmail-etch/)
[http://www.hypexr.org/linux_mail_server.php](http://www.hypexr.org/linux_mail_server.php)
[http://www.howtoforge.com/perfect_setup_ubuntu704_p5](http://www.howtoforge.com/perfect_setup_ubuntu704_p5)
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)


At the same time - I would like to get the user's to validate against an OpenLDAP that I have running on the domain - but that's later on. 

 So Is there anyone - that have a guide that works - and evt have an error case ??? 
I could post the logfiles again - but already started all over once again - for trying yet another time - So come give and good guide - that  works !

---

### Post by HermanAB on 2007-08-19
This is very hard to do.  It is the stuff of legends.  Once you figured it out, you are permitted to grow a guru beard, just like Richard Stallman.

The best documentation is on the postfix web site.

However, if you want an easy solution, go here: [http://www.citadel.org](http://www.citadel.org)

You can install a fully functional Citadel system with all you want and more in about 15 minutes, as opposed to 15 days for a postfix system.

Cheers,

Herman

---

