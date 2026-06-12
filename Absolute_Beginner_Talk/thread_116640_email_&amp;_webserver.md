---
title: "email &amp; webserver"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-01-13
What is the best way to configure this setup please;

Dynamic IP
Ubuntu PC which will be on 24/7

3 PCs in the house where we all share the same email. The inbound emails can be [email]anything@example.com[/email] and they all get picked up by Outlook as the same. If I got people to send then [email]anything_1@example.com[/email], [email]anything_2@example.com[/email] and [email]anything_3@example.com[/email] to diferentiate between the 3 PCs, how could Ubuntu sort these and deliver to the correct mailbox on each PC?

Outbound emails would still go from each PC.


Many thanks.

---

### Post by bscbrit on 2006-01-14
The mailserver part of the question is quite easily solved using procmail.

procmail allows incoming addresses to be 'rewritten' - an email addressed to [email]anything_1@example.com[/email] can be resent to [email]user1@example.com[/email].

Try man procmail for more info. procmail is simple when you know how to use it (isn't everything!) but at first look it seems quite complicated.  Persevere with it though, and your efforts will be rewarded.

---

### Post by bscbrit on 2006-01-14
Sorry, I forgot to comment on the first part of your question.

First of all, I am making some assumptions - although your username is My-dial-up you will not really be using a dial-up for 24/7 operation will you?  If you are, you must have friends in your local telecom company!  

And now some questions please. Are you using your planned mail server for internet access now, or are you accessing this forum using another machine or different operating system?  And will your users be on a local network or do you want them to have access to their mail accounts over the internet?  Anything is possible but there are security implications (and therefore significantly more configuration required) if you want your users to have internet access.

Try the following links for more ideas, but don't hesitate to come back here with specific questions:

[http://www.emailman.com/unix/servers.html](http://www.emailman.com/unix/servers.html)

[http://www.siliconvalleyccie.com/linux-hn/sendmail.htm](http://www.siliconvalleyccie.com/linux-hn/sendmail.htm)

[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)

[http://sbserv.stahl.bau.tu-bs.de/~hildeb/postfix/](http://sbserv.stahl.bau.tu-bs.de/~hildeb/postfix/)

My own mail server uses fetchmail, postfix, procmail, spamassassin and clamav.  However, (as I have just type elsewhere on another thread - [http://ubuntuforums.org/showthread.php?t=116684)](http://ubuntuforums.org/showthread.php?t=116684)), it is always best to install the mail server in stages rather than trying to get everything working at once.

---

### Post by hen3rz on 2006-01-14
> procmail allows incoming addresses to be 'rewritten' - an email addressed to [email]anything_1@example.com[/email] can be resent to [email]user1@example.com[/email].
Can u explain how this is done I'm very interested and im new to linux. so far i have done a make and have installed procmail but im not sure where to go from here.

I was thinking i could have (anything)@blahblah.com forwarded to [email]me@gmail.com[/email]. How would i go about doing this with procmail?

I would appreciate any help.

Thank you.

---

### Post by bscbrit on 2006-01-14
Procmail uses a file containing a set of 'rules' which tell the program what to do.  Each email is scanned and procmail can be directed to search the headers, the text, addresses (or anything for that matter) and, when certain patterns are found, it can be directed to carry out specific actions.  You need to Google for procmail rules or simply look at the "man procmail" at the commandline to start to get a feel for what it possible.
As I said, the syntax for the rules looks difficult at first but there is plenty of advice on the internet regarding how to write them.

As an example, here is one rule that checks for mail addressed to [email]anyone_1@example.com[/email] and then redirects it to another email address.  The final address can be a 'real' email address or simply a user on a specific machine.

```

:0
* ^To: anyone_1@example.com
! user1@this_machine

```

You could easily modify the '!' line to be '! [email]me@gmail.com[/email]' in your specific example.

I cannot really offer to write a whole series of rules to meet your particular needs but if you search the internet ('procmail rules'  brought up the links at the end of this reply, plus hundreds of others) then you will soon get the hang of it.

[http://www.unixgeeks.org/security/newbie/unix/procmail/procmail-example.html](http://www.unixgeeks.org/security/newbie/unix/procmail/procmail-example.html)
[http://www.math.ohio-state.edu/support/procmail/](http://www.math.ohio-state.edu/support/procmail/)
[http://tux.oclug.on.ca/pipermail/oclug/2004-March/037769.html](http://tux.oclug.on.ca/pipermail/oclug/2004-March/037769.html)

HTH

---

### Post by My-dial-up on 2006-01-14
Many thanks for the time taken out to reply to my query, Bscbrit.

I will look at Procmail and get back to you.

The 3 PCs currently run XP as that's the OS the family knows best. We could have individual web emails, but it's easier if we all have the same @example.com, but with diferent prefix. I know this can be done in XP, but I wanted to migrate everyone over to Linux during the course of the next year. All three PCs are linked via a broadband router to the Internet/Intranet, but accessing their email over the internet isn't important. I was after inbound emails to be redirected to their own PC, but they could still send outbound emails from their own PC.

It would be handy for me though, to be able to send/receive emails from my Ubuntu PC.

As a sub-note, I also wanted to install Apache and Webmin !!

In what order would you recommend package installation, please?

Many thanks.

---

### Post by bscbrit on 2006-01-14
What you are trying to achieve is fairly easy to set up.  It doesn't matter what OS the various family members are using - they will simply be accessing a POP server (or IMAP server - the choice is yours) and they will see little difference from accessing their existing server outside on the internet.  Well, it should be a lot quicker but they still might not notice.

Basically, the setup that I use works as follows:

Fetchmail collects the mail from each of the existing email accounts that the family members have e.g. gmail, yahoo, your_domain or whatever.  It is set to check periodically for new mail (my interval is every 10 minutes but you decide).  It then sorts the incoming mail into each users' mailbox on the mail server.

Procmail can also be used on the server to sort mail, trap spam or whatever.

Spamassassin and clamav sit on the server and check every item of email entering my system.  The users rarely see any spam (less than 1% actually gets through the server, but this is invariably caught by each individuals spam checker built into their own computer.  This is because the server musn't lose mail and so will always err on the side of safety and pass spam that is borderline.  However, each user is able to set much more rigorous spam tests because they know what emails they want to see.)  Clamav does the same for viruses.  Of course, currently the viruses have absolutely no effect on the linux systems but I do not want to be responsible for unknowningly forwarding a virus to a windows user.  In your case, where the family will be staying with windows, clamav is a very useful step.

Each family member collects their email using whatever program they do now; Outlook, Thunderbird, Evolution.  But they do not log on to their original site, they now log on to your email server where their de-spammed and de-virused emails are waiting for them.  Sending emails to each other on your internal network is trivial and for sending emails elsewhere you can either let each family member send them as they do now, or you can also have them send them by the server so that you can scan them with clamav on the way out as well.  This is handy in case a virus has reached their computer via http or from a disk or usb memory pen.

The easiest way to do this is to set up fetchmail and your email server.  Family members will not really notice any difference.

Once you have the basic setup working, you can then add spamassassin and clamav one at a time.  The order depends on which presents to you the biggest problem - spam or viruses.

The is no direct conflict when setting up apache and/or webmin but I would recommend that you only do one thing at a time.  If something stops working at least you know where to look for the cause of the problem.  If you are playing with your http server, your mail server and a couple of other programs it can be very frustrating when something stops working and you haven't got a clue where to begin.

Good Luck - I will keep an eye out for your progress!  And you can always come back if you have any specific problems.

---

### Post by bscbrit on 2006-01-14
I forgot to mention - my mail server is a PII running at 233MHz and it copes with the task easily.  It is set up as a server with no GUI installed and when I want to work on it I log on using SSH and sit at my main box.  Never throw anything away - it can always be pressed into service somewhere or other.....

---

### Post by My-dial-up on 2006-01-16
Fetchmail was easy to set up via fetchmailconf.

A couple of questions though;

1) When you use fetchmail to collect emails from various accounts, where does it store the files? Does it setup diferent directories for each account?

2) I setup Postfix via [http://ubuntuforums.org/showthread.php?t=69337&highlight=Postfix+SMTP-AUTH](http://ubuntuforums.org/showthread.php?t=69337&highlight=Postfix+SMTP-AUTH) and it seems to work, though I don't know what I was doing. Does this create the mystical MX record?

3) In Procmail, do I need to set up the diferent email directories myself?

4) In OE would I need to set the POP.example.com to POP.ubuntu-hostname?

Thanks for the help.

---

### Post by bscbrit on 2006-01-16
You need to set up each user area on your server.  You do not need to allow users to log in to the server as users (although they will 'log in' to access their mail using POP or IMAP) .  Create each new user in turn on your server using the 'adduser' command.  

fetchmail can be directed to place mail in a specific users location similar to the following example:

```

poll pop3.uklinux.net with proto POP3 user 'username' there with password 'mypassword' is 'localuser1' here options fetchall
poll pop.imail.ru with proto POP3 user 'anotherusername' there with password 'differentpassword' is 'localuser2' here options fetchall

```

If you are using DynDNS then your MX record is maitained by them I think, but I do not know because I do not use it.

The procmail accounts are the same accounts as you created above using 'adduser'.

There are as many different ways of setting this up as there are people wanting to do it.  Be careful of mixing your advice from different well intentioned advisors.  Search the web for 'email server howto', find an example that you can understand, and implement it on your system.  You can look at others but do not try to mix and match until you know what you are doing.  It is not difficult but it is easy to confuse yourself (been there, done that, got the T shirt....)

---

### Post by My-dial-up on 2006-01-17
I was thinking, doesn't the installation of the email server software scream out for an 'Automatix' style of install? Looking around these forums, the option to setup ones' own email/web server seems to be the most common questions. It's only a thought as I continue to battle through my own installation, and it seemed a logical development to the ongoing move from XP to Ubuntu/Linux.

---

### Post by bscbrit on 2006-01-17
No, I don't think that I agree.  The configuration of a mail server is too variable unless you want to follow the Windows route of 'we will set up what we want, not what the user might want'.  Do you want to use postfix or sendmail? Or exim or squirrel? Which antivirus do you want installed?  Do you want spam checking?  Do you want to use blacklists, whitelists, greylists?  Each program will have its advocates, some will perform better in some areas than in others, some are optimised for speed, or security.  Do you want POP servers or IMAP? etc etc etc

But I do not have a strong view on this.  I don't want to attract a series of responses from thread readers as to why configuration X is better than configuration Y unless their contribution helps _you_ to set up _your_ mail server.

And for me, at any rate, some of the enjoyment is learning how things work and setting it up myself.  I get no pleasure from watching an automated install program do its stuff, and I certainly don't learn very much from it. :D 

I'm sure that something could be done under automatix but, even if it was, I probably wouldn't be using it.

---

### Post by My-dial-up on 2006-01-29
So, 1 week on & 3 formats later;

Fetchmail works (but not with Gmail)
Postfix works with only slight 'out-of-the-box' modification
Procmail seemes to work.

My problem is Courier-imap, I cannot access the IMAP folders from the XP PC in Outlook Express - I keep getting timeout errors.
Do I set the Root folder path to the username I'm after? e.g. ~dad

---

### Post by bscbrit on 2006-01-29
Well done on getting so far in only a week!

However, I'm casting my mind back to some dim and distant recollection that XP in particular does something unusual with usernames and passwords i.e. it does not do what every other OS does.  Its way past my bedtime but I couldn't resist answering your thread.  Let me sleep on it and I will try to remember what the solution is. :D

---

### Post by bscbrit on 2006-01-29
I'm not quite sure what you mean by your question of setting the Root folder path.  But an IMAP server is designed to be connected to by any network, so if your other IMAP accounts are working then the anomaly would appear to be in the XP box.  Have you tried accessing your IMAP server from an account on the server itself? - that would prove the IMAP configuration but not suffer from any networking problems.  Then, if that is successful, try accessing IMAP over a network using 2 linux accounts if possible.  Finally, do it from the XP account and you should be able to narrow down the possible problem areas.

---

### Post by My-dial-up on 2006-01-29
Got Courier working by adding the ubuntu ip to ADDRESS= in imapd.conf

Next problem, cannot install spamassassin - apt-get says it's not a package. . . .

---

### Post by My-dial-up on 2006-01-30
OK, alterered my sources.list to resolve spamassassin.

Next,

as a /etc/procmailrc trial I've added the rule

:0
* ^To: [email]dad@example.com[/email]
! me@localhost

to test if inbound email with fetchmail called [email]dad@example.com[/email] is redirected to the user 'me'

But Postfix says, <me@localhost.localdomain> :mail forwarding loop for [email]me@localhost.loca[/email]ldomain

Have I somehow set up an infinite loop? and if, how do I redirect inbound emails?

---

### Post by bscbrit on 2006-01-31
Where have you set this particular procmail rule?  If it is in your own user procmail file then 'Yes, you have created an infinite loop'.  For example, if the email user 'me@localhost.localdomain' is on the same computer as the server, then any emails sent to it will re-enter the server's procmail chain and go around and around.  But if you have 2 computers, let say 'server' and 'other' you could redirect your mail from the server to [email]me@other.loca[/email]ldomain. (At least I think that's what I mean....!)

---

### Post by My-dial-up on 2006-01-31
Only one Ubuntu PC; I understand now about my infinite loop. Will have a look at it with a fresh mind and get back to you.

Thanks for all the help so far!

---

### Post by My-dial-up on 2006-02-02
Ok, going fantastic here! Procmail is very flexible and I'm getting more impressed by Ubuntu / Linux daily.

Anyway, I use postfix smtp as a relay to my isp because I don't have a static IP. Can I send outgoing mail via postfix/procmail so I can scan for outgoing spam/viruses? (just in case the family have brought any home via PenDrives)

I've looked at 'sender_canonical' but not sure if I'm barking up the wrong tree.

Update:
I can get the function 'sender_canonical' to work, but the outgoing email is not passing through procmail. Do I have to use a diferent program? Procmail processes inbound email, but I assume outgoing mail from my XP PC is inbound into Ubuntu?

---

### Post by bscbrit on 2006-02-03
You can use postfix to scan both incoming and outgoing mail for viruses and/or spam.  I cannot remember the site that I discovered that detailed it all, but I recall that I found it by Googling for 'postfix spamassassin clam'.  I suppose you could prefix your search with 'ubuntu' to see if that gives you a better result.  Of course, the configuration of postfix, spamassassin and clamav is distribution agnostic so any site that provides the information that you need should be suitable. 

 Its impressive what you have achieved in the few weeks that this thread has been running and I hope that you are enjoying the 'learning experience' that goes with setting up your own server.  I still get a very satisfied feeling when I see my incoming mail sorted, cleaned and well organised.

Did you resolve your incoming mail redirection problem?  As I recall (I must dig out my procmail book again!) it is possible to redirect mail to a specified directory rather than to another email address.  That way, it doesn't create an infinite loop.  Having now written that I cannot remember how it is done so I _will_ have to go looking for my book.  Thats one of the problems of age - I learn something then a month or two later I've forgotten most of it!

Good luck.

---

### Post by My-dial-up on 2006-02-05
Pleased with myself so far, though the learning curve has been steep to say the least!

Procmail redirection:
This re-directs inbound email to the localuser 'me' with the X-LOOP addidtion checking if we've already passed this way before.

:0
* ^To: [email]me@example.com[/email]
* !^X-Loop: no-loops-please
        | formail -A "X-LOOP: no-loops-please" | \
                 $SENDMAIL -oi me@localhost

I must say that my initial impression of Procmail was 'fear', but now I think it is a wonderful piece of software with an amazing amount of flexibility. I feel it it one of those things which you could spend hours tinkering with!!!

---

### Post by My-dial-up on 2006-02-05
All the googled replies I can find are related to fixed IPs & MX records, can you remember how to use procmail via smtp/postfix?

---

### Post by bscbrit on 2006-02-05
I think most (all?) of what you need is in these links,  Fingers crossed!

[http://www.howtoforge.com/howto_spamassassin_clamav_procmail](http://www.howtoforge.com/howto_spamassassin_clamav_procmail)

[http://www.falkotimme.com/howtos/spamassassin_clamav_procmail/index.php](http://www.falkotimme.com/howtos/spamassassin_clamav_procmail/index.php)

[http://www.mjhall.org/email.html](http://www.mjhall.org/email.html)

---

### Post by My-dial-up on 2006-02-05
What I was after was being able to scan all outgoing Internet emails. Is this possible with Ubuntu? I've read many pages explaining how to modify sendmail.cf, but Ubuntu doesn't implement sendmail.cf or many of its' cmd line parameters.

Any idea?

---

### Post by bscbrit on 2006-02-05
Yes it can - but I'm scratching my head trying to remember how.....

And here's another link for your previous question:

[http://ezine.daemonnews.org/200309/postfix-spamassassin.html](http://ezine.daemonnews.org/200309/postfix-spamassassin.html)

---

### Post by bscbrit on 2006-02-05
Try this for starters, about a quarter way down the page..

[http://www.kobitosan.net/postfix/origdocs/install-sav-en.html](http://www.kobitosan.net/postfix/origdocs/install-sav-en.html)

Outgoing mail can be piped through a scanning filter but I haven't got access to my notes or my server at this moment, so I cannot recall exactly how I set it up.  I've put it on my things to remember/dig out/relearn so I'll try to get back to you on this.  ;)

---

### Post by bscbrit on 2006-02-05
Yes, that's it,  The information that you need is partly in my link a couple of posts back today. I redirect outgoing mail to port 10025 (or thereabouts) and it sends it onwards via smtp.

---

### Post by My-dial-up on 2006-02-05
sockstat isn't part of the Ubuntu cmd set;

Issue these commands: 

	# postfix reload
	# sockstat -l4 | grep 25
	root     master     24727 11 tcp4   *:25                  *:*
	root     master     24727 75 tcp4   127.0.0.1:10025       *:*

Postfix should be listening on two ports now - 25 and 10025. Check to ensure it's connecting to those ports: 

	# telnet localhost 25
	Trying 127.0.0.1...
	Connected to localhost.
	Escape character is '^]'.
	220 idealan.pl ESMTP Postfix
	^]
	telnet> quit
	Connection closed.
	
	# telnet localhost 10025
	Trying 127.0.0.1...
	Connected to localhost.
	Escape character is '^]'.
	220 idealan.pl ESMTP Postfix
	^]
	telnet> quit
	Connection closed.

---

### Post by My-dial-up on 2006-02-06
I can get amavisd-new to work with 10024/25 but not procmail. Is there a simple line to add in master.cf to send the outbound relay email through procmail?

---

### Post by bscbrit on 2006-02-07
Scratching head again.....

Its not so much a problem as 'sending' mail to procmail as telling procmail to receive it.  The data is sucked in on, say, port 10025, processed and pushed out on another port (mine is 10026) if I recall correctly.  Another program (procmail) must be told to 'listen' on this port.  I'll have to go and do some more googling/reading to find out the definitive answer. :D

---

### Post by My-dial-up on 2006-02-08
Got this working thanks by altering the master.cf to point to diferent ports.

I'm going to reformat at the weekend and see if I can do it all in one session!!

---

### Post by My-dial-up on 2006-02-08
Clamav doesn't seem to be scanning local inbound email, when I run 'dpkg-reconfigure clamav-base' it asks for a TCP port and defaults to 3310, should I change this to 25? It does scan outbound relay mail though!

Feb  8 16:39:41 localhost amavis[6649]: (06649-01) Clam Antivirus-clamd: Can't connect to UNIX socket /var/run/clamav/clamd.ctl: No such file or directory, retrying (2)
Feb  8 16:39:47 localhost amavis[6649]: (06649-01) Clam Antivirus-clamd av-scanv-scanner FAILED: Too many retries to talk to /var/run/clamav/clamd.ctl (Can't connect to UNIX socket /var/run/clamav/clamd.ctl: No such file or directory) at (eval 42) line 180.
Feb  8 16:39:47 localhost amavis[6649]: (06649-01) WARN: all primary virus scanners failed, considering backups

---

### Post by bscbrit on 2006-02-08
Its getting to the stage where I cannot provide much useful advice because I have little visibility of your precise configuration.  What with procmail, postfix, clamav, fetchmail (and spamassassin?), there are so many possible configurations that I am unable to contribute much to problem solving. :D  :D  :D 

I'm still interested in how you are getting on but I feel that my contribution (which was never much, anyway) is fading away to cheering from the sideline!

---

