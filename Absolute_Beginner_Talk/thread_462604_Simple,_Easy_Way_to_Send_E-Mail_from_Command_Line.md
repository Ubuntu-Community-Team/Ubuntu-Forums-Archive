---
title: "Simple, Easy Way to Send E-Mail from Command Line"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-06-02
Hello -

I run a file server at home and would like my server to email me on occasion ... so, I need a command line based way to email myself (from a cron script).  I have been doing a lot of reading on the subject and know [there are a lot of mail clients/options]("http://ubuntuforums.org/showthread.php?t=132398&highlight=ssmtp").  I've tried a number of different options (with some or no success).

But I just want to send a message.  I don't want to check mail, download mail, forward mail, use any other mail feature than outputting the contents of a text file to a mail recipient.  I really don't want to have a whole mail server running in the background just to send out five lines of text once a week.

Is there a simple, low resource, secure way to send a message from the command line ?  What is it ?  Or: can it not be done?

Thanks,
Damon

---

### Post by sandwitch on 2007-06-03
Simplest option is to have mailutils installed. You can then do things like df -h | mail [email]you@yourdomain.com[/email] -s "Diskspace on $(hostname) $(date +%Y%m%d)". This expects a simple mailserver installed offcourse. If you install exim as a forwarder to a smarthost (your isp's server) this is done in minutes.

---

### Post by thornomad on 2007-06-03
All right, I will try mailutils again and not give up so quickly; though, I thought it installed exim4 by default.  I had tried to use msmtp and was able to send email from the command line using my google smtp server ... however, I don't think it is meant to be run from the command line.  That is: I could get it to send any "message" ... just a blank e-mail.

I will play with it more.

D

---

### Post by andrew.46 on 2007-07-16
Hi,

 Might be a little much but what about mutt and ssmtp? You could modify information from this page:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 The man who wrote this page is a great guy :-)

                     Andrew

---

