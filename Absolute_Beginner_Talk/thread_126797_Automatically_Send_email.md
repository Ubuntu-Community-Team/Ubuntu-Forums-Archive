---
title: "Automatically Send email"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by aujames95 on 2006-02-07
I have a script that runs and performs some simple tasks, I would to setup my system such that I can have that script send me a email when complete. Would anybody be able to give me a starting point to getting that setup?

Thanks,
JD

---

### Post by skirkpatrick on 2006-02-07
Just did a quick google, this should help:

[http://www.daniweb.com/techtalkforums/thread17751.html](http://www.daniweb.com/techtalkforums/thread17751.html)

---

### Post by aujames95 on 2006-02-07
Thank you for the reply.

I guess what I really need to do first, is configure the system to have the ability to send email, before I can actually use the example you provided. i.e do I need to set up sendmail or some equivelent.

Thanks!!

---

### Post by earobinson on 2006-02-07
very nice!

---

### Post by earobinson on 2006-02-07
I dont even have the mail command on my computer nor can I find it in the repos (dapper)

---

### Post by skirkpatrick on 2006-02-07
Yes, you'll have to install and setup sendmail if it isn't already.

Really?  I did a "man mail" and also "mail" and it's on mine.  I don't think I did anything special.

---

### Post by earobinson on 2006-02-07
could be a dapper thing

---

### Post by aujames95 on 2006-02-07
Thanks guys, do you know of any quick how-tos with regards to setting sendmail up on Ubuntu?

---

### Post by FrankTM on 2006-02-07
try install postfix

the setup should provide enough information to get you up and running

---

### Post by kosmic on 2006-02-07
Why don't you use Postfix ? it comes already with Ubuntu :)

---

### Post by Kadin2048 on 2006-02-08
[QUOTE=earobinson]I dont even have the mail command on my computer nor can I find it in the repos (dapper)[/QUOTE]

I just had this problem as well.

For some reason, the "mail" program is now called "mailx". I assume one can just install mailx, and then make a symlink called "mail" that points to "mailx", so any scripts you want to use will work.

Frankly, I think calling the program "mailx" is confusing, because a trailing-letter X generally indicates an XWindows application (even though in this case I think the name may predate XWindows). That's what confused me for a while, and caused me not to bother to check it out in the package repositories.

mailx is just a MUA though, it won't deliver the mail to the recipient's server if it's not on the local system (actually I don't think it will deliver it even if the user is on the local system). You will still need to set up a MTA like sendmail or postfix to actually have a usable setup.

Or if you just want scripts to be able to send you email, someone suggested to me that I use "msmtp." I haven't played with it at all yet, but it supposedly is a very lightweight SMTP client that does nothing but send mail.

---

### Post by ubuntumaneh on 2006-02-08
mail is in mailx package (which is weird)

apt-cache search mailx
devscripts - Scripts to make the life of a Debian Package maintainer easier
mailx - A simple mail user agent
mailutils - GNU mailutils utilities for handling mail
fetchmail - SSL enabled POP3, APOP, IMAP mail gatherer/forwarder
mush - The mail user shell

---

### Post by UphillSkier on 2006-02-13
I am having the same sort of problem.  I want to set up a cron job and have the
output mailed to me.  So I tried to make sure my local mail was working.  I installed
postfix and followed the installation instructions from the wiki at Postfix [https://wiki.ubuntu.com/Postfix]("https://wiki.ubuntu.com/Postfix")

Then I downloaded and installed mutt, but couldn't get it to work. (that is, 
I could not mail a message to mysef - It started and created a $HOME/Mail directory ok) Then I found this discussion so I downloaded and installed mailx.  But I still can't send a message to myself

```
andy@grumpy:~$ which mail
/usr/bin/mail
andy@grumpy:~$ mail
No mail for andy
andy@grumpy:~$ mail andy
Subject: testing
a line
another line
Cc:
andy@grumpy:~$ mail
No mail for andy

```

It isn't that I have the wrong host, because this doesn't work either

```
andy@grumpy:~$ mail andy@localhost.localdomain
Subject: testing
a line
two lines
Cc:
andy@grumpy:~$ mail
No mail for andy
andy@grumpy:~$

```

So I imagine I haven't got postfix set up properly.  Can anyone point to a simple getting started guide to help with this?  Or even suggest what I am doing wrong?

thanks
Andy

---

### Post by skirkpatrick on 2006-02-14
Well, on my desktop machine I tried to send an email from the command line to my normal email and it worked fine and I've never installed or configured postfix or sendmail (to my knowledge).  I had followed the 5.04 Ubuntu Guide to setup Thunderbird to get all the local email being sent to root and those messages go to [email]root@localhost.loca[/email]ldomain.

---

### Post by UphillSkier on 2006-02-14
[QUOTE=skirkpatrick]Well, on my desktop machine I tried to send an email from the command line to my normal email and it worked fine and I've never installed or configured postfix or sendmail (to my knowledge).  I had followed the 5.04 Ubuntu Guide to setup Thunderbird to get all the local email being sent to root and those messages go to [email]root@localhost.loca[/email]ldomain.[/QUOTE]


Interesting.  I installed from the 5.10 preview release and updated as required.  No trace of sendmail, postfix or mail(x) on either my office or home machines.

---

### Post by UphillSkier on 2006-02-14
[QUOTE=UphillSkier]Interesting.  I installed from the 5.10 preview release and updated as required.  No trace of sendmail, postfix or mail(x) on either my office or home machines.[/QUOTE]

My problem may be a dirty install of postfix.  I installed mailx from synaptic on my clean office machine.  It installed and configured postfix as a dependency.  Mail worked right from the command line and evolution can read the local mail if I set up a new account using "Standard Unix mbox"  as the server type.  

I plan to uninstall mailx, sendmail and postfix from my home machine, then do a clean install of mailx. 

Hope this experience helps somebody.

cheers

---

