---
title: "Calling Evolution-2.2 via cron"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by JoshWilson on 2005-08-12
Hello all!  N00b Wilson here...

I've setup a desktop with Ubuntu 5.0.4 and am running Evolution to connect to my Microsoft Exchange environment here at our office.  The system that I've installed Ubuntu on is our Mail distribution server that parses through alert e-mails etc...and diverts them to the appropriate personnel.

**PROBLEM**
My problem is that when I execute /usr/bin/evolution-2.2 from a cron instance the application never comes up.  If I execute that same command from my login shell it runs just fine.

I'm assuming that I need to remedy this I need to use the --display or --screen flags for evolution to get the program running correctly but I'm not sure how those flags work.

Can someone please tell me how to get /usr/bin/evolution-2.2 to execute successfully from a cronjob and run on the console's GUI in Ubuntu?

Any help is appreciated!

---

### Post by KingBahamut on 2005-08-12
Why do you want to run Evolution through Cron? 

Mebbe this is a slightly off question.

---

### Post by JoshWilson on 2005-08-12
Because on this system it is required that Evolution be running to process the enormous amount of e-mails our administrative inbox receives.  If it stops running or if the system gets booted, e-mails start stacking up in our admin inbox.

This is the reason I have to get it to "Check" for evolution every minute.

I finally got it to run in cron but I first had to edit the /etc/gdm/gdm.conf file, changing the "DisallowTCP=True" line to "DisallowTCP=false".  Then I rebooted the system and added the following line in cron just to see if it would run:

* * * * * /usr/bin/evolution-2.2 --display=10.15.3.59:0 & 2>/dev/null

That seemed to execute evolution and bring it up on my console, however if I enter the same information into my perl script and then change my cron line to the following...nothing happens.  I see it run perl script but the app doesn't come up.

# Cron Entry
* * * * * /usr/local/bin/evolution-check.pl


# Content of evolution-check.pl
#!/usr/bin/perl
open(SCAN, "ps -ef |grep evolution-2.2 |head -1 |gawk '{print \$8}' |");
$RESULT=<SCAN>;
chomp($RESULT);
close(SCAN);

open(LOG, "> /root/test2");
print LOG ("RESULT is: $RESULT\n");
close(LOG);

if ($RESULT eq "evolution-2.2")
        {
        print("It's runnin' already runnin' you big dummy!!!\n");
        goto EOF;
        }
else
        {
        print("Starting the Evolution application now...\n");
        system("/usr/bin/evolution-2.2 --display:10.15.3.59:0 \& 2>/dev/null");
        }

EOF:

---

### Post by KingBahamut on 2005-08-12
Time to consider Postfix or Qmail.....just kidding. 

I thought the primary element of Exchange was for it to run in Realtime all the time. Wasnt so much a matter of having the system check email all the time or sort. Unless your running that server as pop or forcing delivery to local folders rather than having the server depend on status of the delivery. Im totally unfamiliar with MSExchange , so I cant supply a valid answer to that.

I think the more valid point that comes to mind here is management of incoming electronic messages, alot more than whether or not Evolution runs as a Cron job. I cant validly see why youd want to run Evolution as a cronjob. If your concerned about a user getting booted or forcing a restart or something, set it up in the session list.

---

### Post by JoshWilson on 2005-08-12
Do you mean like have Evolution run on login?  How do I do that because that would be perfect.

Evolution could probably run forever on Linux because the OS is so darn stable.  I didn't know how to set it up to begin running on login, so I tried to combat that with a script that would check it every minute.

If you could tell me how to initiate the program at login, that'd work better because then I could totally avoid all these issues.

Thanks in advance KingBahamut  - Final Fantasy fan eh?

---

### Post by KingBahamut on 2005-08-12
[QUOTE=JoshWilson]Do you mean like have Evolution run on login?  How do I do that because that would be perfect.

Evolution could probably run forever on Linux because the OS is so darn stable.  I didn't know how to set it up to begin running on login, so I tried to combat that with a script that would check it every minute.

If you could tell me how to initiate the program at login, that'd work better because then I could totally avoid all these issues.

Thanks in advance KingBahamut  - Final Fantasy fan eh?[/QUOTE]
 Bahamut - Forgotten Realms, God of All dragons, Unwitting Husband to Tiamat, Queen of All dragons..... I have an odd dragon fetish, you need to see the My Ubuntu Datacenter post in Community chat to get it. 

[http://ubuntuforums.org/showthread.php?t=55871](http://ubuntuforums.org/showthread.php?t=55871)

---

### Post by KingBahamut on 2005-08-12
Go System -> Preferences -> Sessions , and mill around in there, youll find what you need to force it on startup.

---

