---
title: "Exchange email in Ubuntu?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-04-08
Greetings,

Just installed Ubuntu and all is well :)  However, I have a Microsoft Exchange email address that syncs with my Blackberry in windows through Microsoft Outlook.  It works really well and keeps my calendar, address book, etc all in sync.  I can't seem to get it to work with Evolution.  Is this not supported?  Is there any other app I can use other than Evolution so everything syncs?  For the record, my blackberry syncs over-the-air and not with a cable (which is how I'd like for it to stay ideally).

Thanks in advance for any help!

Chris Farrugia

---

### Post by siciliancasanova on 2007-04-09
I know Thunderbird uses PalmSync but can only exchange the address book though.  No calendar or anything else.  I'm not sure about Sunbird.  I only know this because I use Thunderbird, I haven't actually synchronized anything with Ubuntu yet.

---

### Post by jbiskupiak on 2007-04-09
What version of Ubuntu are you using?  I had the same problem with Evolution using Dapper Drake.  If you upgrade to Edgy Eft, Evolution works with the Exchange server (at least this is what worked for me).

---

### Post by jbiskupiak on 2007-04-09
You may also need to edit the sources.list file in /etc/apt.  Email me if you need help.

---

### Post by chrisf79 on 2007-04-09
> **jbiskupiak said:**
> What version of Ubuntu are you using?  I had the same problem with Evolution using Dapper Drake.  If you upgrade to Edgy Eft, Evolution works with the Exchange server (at least this is what worked for me).

I just installed 6.10 and couldn't seem to get it to work.  I have the Exchange part of Evolution installed (verified in Synaptic) and it just doesn't seem to pull the email in.  When I type in my password, it just tends to freeze, then about 15 seconds later, it says it can't retrieve anything.

For my OWA, do I just put in the URL I use to access my account over the web?  [https://exchange.usa.net](https://exchange.usa.net) ?

Thanks!

---

### Post by jbiskupiak on 2007-04-09
For OWA, just enter your URL into the browser and you should be good to go.  

To get Evolution to work:

Add the 3 files from Ubuntu Main section to your source.list (see below) 
# Ubuntu Main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse

 
 These addresses came from the following web site:
[http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)
 
After you have updated your sources.list; Perform an apt-get update then search/install Evolution.

This should get your Evolution up and talking with the Exchange Server assuming you have set up the account correctly in Evolution.

---

