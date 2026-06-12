---
title: "Send Ip on startup"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-19
Hi there, i'm at a university, and my ip address changes very frequently, this makes it hard to remote desktop.  Would there be a way to send my ip to a certain machine every time i boot up?  Or to an email address?
I suppose emailing an ip on startup would be kind of hard to do, but maybe a script to ping a machine, that will block the ping, therefore showing up in firestarter, or somethign along those lines?  Basically i just want a record of what my ip changes to on bootup, but at a different machine.

Any ideas/suggestions?

---

### Post by llamakc on 2007-11-19
Simple. What IP is changing on you? The wireless or the wired one? Show the output of `ifconfig` from a terminal and tell us which one you want emailed.

---

### Post by llamakc on 2007-11-19
For example, I'm wired, and it is ALWAYS eth0 that I connect with. eth0 ALWAYS is the first entry on my box returned by `ifconfig`.

This works perfectly for MY setup. I'd need details about yours to modify it.

```
 ifconfig | awk '{print  $2}' | head -2 | tail -1 | sed 's/addr://' | mail -s "MY IP" me@somewhere.com

```

I'm sure somebody smarter than me will come by and have a more elegant method, but this DOES work. I would then make a script out of it and put it in rc.local.

---

### Post by jordank on 2007-11-19
Yeah, i'm wired, eth0
here's the results from ifconfig:

kristie@Sparktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:74:B7:51  
          inet addr:142.104.164.73  Bcast:142.104.164.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe74:b751/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:955771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:51779 txqueuelen:1000 
          RX bytes:254157096 (242.3 MB)  TX bytes:20043658 (19.1 MB)
          Interrupt:22 


The inet addr: is what i would like to have emailed on startup each time on startup.  But that would require some sort of email script on startup, which is probably harder than i would imagine.  How would i get this system up and running.

---

### Post by llamakc on 2007-11-19
My example works perfectly for you then. Cut/paste what I have into the terminal but CHANGE the email address to YOURS. Hit enter. That's all one long line you enter in.

Make sure it works and then we'll turn it into a script and drop it into rc.local (if you want it every time you boot up).

---

### Post by jordank on 2007-11-19
your code that you have there, how does it email you? You have a command called "mail", but what does it use to do that, and do you see it happen on startup, or does it happen in the behind-the-scenes?  Also, is that a bash script that you have stored somewhere, or how do you implement it to happen every time?

---

### Post by MegaJim on 2007-11-19
I think this is perhaps what you are looking for:  [http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)

You can then access your computer through a domain name, or DNS query it to find out its IP.

---

### Post by Dr Small on 2007-11-19
> **llamakc said:**
> My example works perfectly for you then. Cut/paste what I have into the terminal but CHANGE the email address to YOURS. Hit enter. That's all one long line you enter in.

Make sure it works and then we'll turn it into a script and drop it into rc.local (if you want it every time you boot up).
Doesn't that only work if he has a MTA ?

---

### Post by llamakc on 2007-11-19
> **jordank said:**
> your code that you have there, how does it email you? You have a command called "mail", but what does it use to do that, and do you see it happen on startup, or does it happen in the behind-the-scenes?  Also, is that a bash script that you have stored somewhere, or how do you implement it to happen every time?

The command "mail" that I use is provided by the package "mailx" that you would install from Synaptic or apt-get. It does the work for you. 

It JUST works.

What I posted was a BASH one-liner, but making it a script is simple. I don't use it because I don't need it, but if I were to need one, I would either just have a script I called at random for when I needed it, or I would either run it at login or at boot. The decision is really up to you.

EDIT: the suggestion above may be better for you. This is just the way that I would do it.

---

### Post by llamakc on 2007-11-19
> **Dr Small said:**
> Doesn't that only work if he has a MTA ?

```

  apt-cache show mailx
Package: mailx
Priority: optional
Section: mail
Installed-Size: 292
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Robert Luberda <robert@debian.org>
Architecture: i386
Version: 1:8.1.2-0.20070424cvs-1
Provides: mail-reader
Depends: libc6 (>= 2.5-5), liblockfile1 (>= 1.0), exim4 | mail-transport-agent, base-files (>= 2.2.0)
Conflicts: suidmanager (<< 0.52)
Filename: pool/main/m/mailx/mailx_8.1.2-0.20070424cvs-1_i386.deb
Size: 156318
MD5sum: b225a5e150de6e6a745d8641636089c2
SHA1: 892c69a750dd33a8148467787d529f4d9e92d0c9
SHA256: 6ac8e3faf83516ce8ef57cf3797dda385669c6f60284d0a2aee36dac0f5967ee
Description: A simple mail user agent
 mailx is the traditional command-line-mode mail user agent.
 Even if you don't use it it may be required by other programs.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: mail-server

```

mailx provides that functionality even if you're not running an MTA.

---

### Post by jordank on 2007-11-19
k. couple questions.  What is a dns query and what is an MTA?

---

### Post by llamakc on 2007-11-19
I may have mispoke: I have both "mailx" and "mailutils" installed and they both provide /usr/bin/mail.

Either way I believe it works sans a full-blown PostFix or Exim4 install.

---

### Post by Dr Small on 2007-11-19
> **llamakc said:**
> I may have mispoke: I have both "mailx" and "mailutils" installed and they both provide /usr/bin/mail.

Either way I believe it works sans a full-blown PostFix or Exim4 install.
ah, ok.

---

### Post by jordank on 2007-11-19
kristie@Sparktop:~$ ifconfig | awk '{print  $2}' | head -2 | tail -1 | sed 's/addr://' | mail -s "MY IP" [email]jordler@hotmail.com[/email]

that didn't appear to send anything, although i'm still waiting, maybe, but nothing yet.

---

### Post by llamakc on 2007-11-19
Did you install "mailx" or "mailutils" yet?

I sent you two also to show that it works.

---

### Post by jordank on 2007-11-19
So yeah, after given sufficient time, it didn't send me anything to my address.  I'm installing mailutils right now.  What would you suggest i do from here?

---

### Post by jordank on 2007-11-19
yeah. i installed both.

---

### Post by llamakc on 2007-11-19
Well I DID send you it twice, so check your hotmail spam also.

After installing 'mailx' do this as a test:

```

echo "asdf" | mail kristie

```

You should have mail on the local system now. You can check it by typing simply "mail" by itself on the command line.

It will look SOMETHING like this:

```

ken@llamakc 07:25:33:~$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/ken": 3 messages 2 new
    1 MAILER-DAEMON@lla  Tue Jun 19 07:17   13/638   DON'T DELETE THIS MESSAGE -
>N  2 root@llamakc.org   Mon Nov 19 19:23   53/3975  November 70% OFF
 N  3 ken@llamakc.org    Mon Nov 19 19:25   17/608   
& 

```

If you hit the NUMBER in front of the email, it will show the email.

You can exit "mail" by typing CTRL-d

---

### Post by jordank on 2007-11-19
check it out. It doesnt seem to support remote domains.

kristie@Sparktop:~$ mail
"/var/mail/kristie": 2 messages 2 new
>N   1 Mail Delivery Syst Mon Nov 19 17:14  36/1245  Mail delivery failed: ret
 N   2 Mail Delivery Syst Mon Nov 19 17:24  37/1282  Mail delivery failed: ret
& 1
From: Mail Delivery System <Mailer-Daemon@sparktop>
To: kristie@sparktop
Subject: Mail delivery failed: returning message to sender
Date: Mon, 19 Nov 2007 17:14:52 -0800

This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  [email]jordler@hotmail.com[/email]
    Mailing to remote domains not supported

------ This is a copy of the message, including all the headers. ------

Return-path: <kristie@sparktop>
Received: from kristie by Sparktop with local (Exim 4.67)
        (envelope-from <kristie@sparktop>)
        id 1IuHhU-0002bu-Kp
        for [email]jordler@hotmail.com[/email]; Mon, 19 Nov 2007 17:14:52 -0800
To: [email]jordler@hotmail.com[/email]
Subject: MY IP
Message-Id: <E1IuHhU-0002bu-Kp@Sparktop>
From: Kristie Sparksman <kristie@sparktop>
Date: Mon, 19 Nov 2007 17:14:52 -0800

142.104.164.73

---

### Post by jordank on 2007-11-19
I dont really understand how mail software can claim to not support remote domains. What's the purpose of mailing yourself the ip address?

---

### Post by Dr Small on 2007-11-19
Hotmail probably is not supporting it.
If I use sendmail and send to hackermail.com, their server rejects it because it is an unqualified domain, whereas if I send it to my parents mail server, it accepts it, because it's server does not have that restriction.

Dr Small

---

### Post by llamakc on 2007-11-19
Then I have sorely given you a non-working bad option. My apologies. 

> **MegaJim said:**
> I think this is perhaps what you are looking for:  [http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)

You can then access your computer through a domain name, or DNS query it to find out its IP.

May very well be your best option.

You can install the client from inside of Ubuntu in Synaptic or with apt-get. It's called "ddclient".

My apologies.

---

### Post by Dr Small on 2007-11-19
> **llamakc said:**
> Then I have sorely given you a non-working bad option. My apologies. 



May very well be your best option.

You can install the client from inside of Ubuntu in Synaptic or with apt-get. It's called "ddclient".

My apologies.
I would still like to try this out myself ;)

---

### Post by jordank on 2007-11-19
Ahh, really?  Do you think that's what the problem is?  What could i send it to to see if the command is actually working, and that it's not a syntax error of some kind.  Why wouldn't hotmail support it.  What would be an alternative to using hotmail?

---

### Post by llamakc on 2007-11-19
> **jordank said:**
> Ahh, really?  Do you think that's what the problem is?  What could i send it to to see if the command is actually working, and that it's not a syntax error of some kind.  Why wouldn't hotmail support it.  What would be an alternative to using hotmail?

I sent it to myself @ gmail and the email showed up.

---

### Post by Dr Small on 2007-11-19
Hotmail would possibly not support it, like hackermail, because it is an Unqualified Domain sending the email, so it is being rejected by the server. As for an alternative, I have no clue. It was by my lucky stars that I found out my parents mail server worked.

---

### Post by jordank on 2007-11-19
so theoretically that would mean gmail accounts do work. I'll try making a gmail account, try sending it to that instead. If that doesn't support it, then it's something client side, and i'm going to need your help :)

---

### Post by Dr Small on 2007-11-19
> **jordank said:**
> so theoretically that would mean gmail accounts do work. I'll try making a gmail account, try sending it to that instead. If that doesn't support it, then it's something client side, and i'm going to need your help :)
Of course :D
If llamakc got it to work, surely another person can get it to work also ;)

---

### Post by jordank on 2007-11-19
kristie@Sparktop:~$  ifconfig | awk '{print  $2}' | head -2 | tail -1 | sed 's/addr://' | mail -s "MY IP" [email]jordler0@gmail.com[/email]


still didn't appear to send anything.  I would think it would be in my inbox by now.
So what could the problem be?

---

### Post by llamakc on 2007-11-19
It very well could be that I run a mail server and I was VERY wrong about mailx and mailutil. 

If that is the case, you can choose to install a lightweight MTA (mail transport agent) from the repositories. 

BTW, when you installed 'mailx' and 'mailutils' did it ONLY install those two packages? Do you remember?

One such MTA is called masqmail. If I understand it correctly it would allow you to send mail from your machine.

---

### Post by Dr Small on 2007-11-19
Try running "mail" now, and see if there were any error emails sent back to your server.
Ah, I forget how to check to see if you still have mail in que (however you spell it).

---

### Post by llamakc on 2007-11-19
mailq

will check for mail not sent yet.

---

### Post by jordank on 2007-11-19
yeah, i believe it only installed those two packages.  Is an mta absolutely required?

---

### Post by jordank on 2007-11-19
kristie@Sparktop:~$ mailq
exim: permission denied
kristie@Sparktop:~$ sudo mailq
kristie@Sparktop:~$ 

doesnt seem to do anything.

---

### Post by jordank on 2007-11-19
kristie@Sparktop:~$ mail
"/var/mail/kristie": 4 messages 2 new
 R   1 Mail Delivery Syst Mon Nov 19 17:14  39/1290  Mail delivery failed: ret
 R   2 Mail Delivery Syst Mon Nov 19 17:24  39/1302  Mail delivery failed: ret
>N   3 Kristie Sparksman  Mon Nov 19 17:32  14/465   Kristie Sparksman
 N   4 Mail Delivery Syst Mon Nov 19 17:46  37/1278  Mail delivery failed: ret
&

---

### Post by llamakc on 2007-11-19
So it installed exim (which is a MTA). Do this:

```

dpkg -l | grep exim

```

And let us see what packages are installed.

---

### Post by jordank on 2007-11-19
kristie@Sparktop:~$ dpkg -l | grep exim
ii  exim4                                      4.67-5build1                         meta-package to ease Exim MTA (v4) installat
ii  exim4-base                                 4.67-5build1                         support files for all Exim MTA (v4) packages
ii  exim4-config                               4.67-5build1                         configuration for the Exim MTA (v4)
ii  exim4-daemon-light                         4.67-5build1                         lightweight Exim MTA (v4) daemon
kristie@Sparktop:~$

---

### Post by jordank on 2007-11-19
lightweight exim mta... don't i have an mta?
Bah. why doesn't this work?

---

### Post by jordank on 2007-11-19
Hrmm. would you mind letting me try sending something to your gmail account, just as a test run. that would confirm that it's my end.

---

### Post by jordank on 2007-11-19
What else do you have installed that lets you send mail from your command line that i dont?   nothing was received from gmail or hotmail when i tried sending there. anyone have any answers?

---

### Post by Dr Small on 2007-11-19
I use sendmail for php, but that isn't really what you want to use...

---

### Post by jordank on 2007-11-19
well, i dont really care what i use, i just want a script that sends my ip to a certain email address on startup.  Could i use that application to do that?

---

### Post by Dr Small on 2007-11-19
Yeah, probably, but it would require php5 and sendmail and dependencies, etc, etc, etc...
I'm going to try the former method and see if it works for me first, though.

Dr Small

---

### Post by jordank on 2007-11-19
Alright, please let me know how that goes.

another problem i remembered, was that oddly enough, my internet isnt established for about 3 minutes after booting up. I'm not sure why, that's just how the campus internet is here.  In my script i would need to have a 3 minute pause before it executed the send.  Is this also doable?

---

### Post by Dr Small on 2007-11-19
It didn't work for me either, with mailx and mailutils.
I checked my inbox, and no emails, checked mailq, and no messages to be queued....

---

### Post by jordank on 2007-11-19
it sounds like it needs some sort of plugin to be able to send to remote domains.  Should i make a new thread regarding mailx?

---

### Post by jordank on 2007-11-20
can someone explain what a DNS query is? There was a post earlier saying i may need this?

---

### Post by llamakc on 2007-11-20
How do you have exim configured? 

Run

sudo dpkg-reconfigure exim

and it gives you a few options on HOW you want to set up your machine.

---

### Post by jordank on 2007-11-20
kristie@Sparktop:~$ sudo dpkg-reconfigure exim
Package `exim' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: exim is not installed


is that the problem there?

---

### Post by llamakc on 2007-11-20
My bad. I meant

```

sudo dpkg-reconfigure exim4

```

---

### Post by jordank on 2007-11-20
Reconfigure exim4-config instead of this package                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Exim4 has its configuration factored out into a dedicated package,        &#9474;  
 &#9474; exim4-config. To reconfigure Exim4, use 'dpkg-reconfigure exim4-config'. 

is what i get when i run sudo dpkg-reconfigure exim4

so when i do dpkg-reconfigure exim4-config
i get:

&#9508; Mail Server configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Please select the mail server configuration type that best meets your     &#9474;  
 &#9474; needs.                                                                    &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Systems with dynamic IP addresses, including dialup systems, should       &#9474;  
 &#9474; generally be configured to send outgoing mail to another machine, called  &#9474;  
 &#9474; a 'smarthost' for delivery because many receiving systems on the          &#9474;  
 &#9474; Internet block incoming mail from dynamic IP addresses as spam            &#9474;  
 &#9474; protection.                                                               &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; A system with a dynamic IP address can receive its own mail, or local     &#9474;  
 &#9474; delivery can be disabled entirely (except mail for root and postmaster).  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>   


so i press okay, and it gives me a screen:


 Mail Server configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;    
   &#9474; General type of mail configuration:                                   &#9474;    
   &#9474;                                                                       &#9474;    
   &#9474;     internet site; mail is sent and received directly using SMTP      &#9474;    
   &#9474;     mail sent by smarthost; received via SMTP or fetchmail            &#9474;    
   &#9474;     mail sent by smarthost; no local mail                             &#9474;    
   &#9474;     local delivery only; not on a network                             &#9474;    
   &#9474;     no configuration at this time                                     &#9474;    
   &#9474;                                                                       &#9474;    
   &#9474;                                                                       &#9474;    
   &#9474;                  <Ok>                      <Cancel>         


with local delivery only; not on a network highlighted by default.  I'm assuming this means i'm using this setting.
Should this be changed?

---

### Post by jordank on 2007-11-20
okay so i went through the configuration, and got everything set up. I can now send emails, and your first line of code that you gave me works!

How do i implement this to happen on startup?
And is there a way for me to make it happen like 3 minutes after startup, because it takes a little while to establish an internet connection? like is there pause command i can run before the entire line of code you gave me?

:) happy the email portion is actually working!

---

### Post by jordank on 2007-11-20
also, how do the mail command work?
I know that i type:
mail [email]example@example.com[/email]

and it lets me start writing my message, but what do i press when i'm done?  There's like no send option.  How do i tell it i'm finished writing my message?

---

### Post by llamakc on 2007-11-20
I believe you hit CTRL-D

I hope somebody comes by and shows you how to make it a script. I'm on my way out of town and will be away from the tubes and internets.

Good luck.

---

### Post by jordank on 2007-11-20
alright, thanks anyways :)

---

### Post by Dr Small on 2007-11-20
Write a bash script with your command in it:
```
#!/bin/bash
ifconfig | awk '{print $2}' | head -2 | tail -1 | sed 's/addr://' | mail -s "MY IP" jordler@hotmail.com
```

Drop it, let's say (for example) in your Home Folder. You can place it anywhere on your system though. 
Give it executable permissions:
```
chmod +x mailip
```

Then let's make a symbolic link from this file to init.d:
```

sudo ln -s /home/drsmall/mailip /etc/init.d/mailip
```
Then run:
```
update-rc.d mailip defaults
```

By the way, could you please explain how you got it to work?
I have mailutils installed with exim4 and have run dpkg-reconfigure exim4-config and yet do not seem to see how to send mail. It spits out no errors, but I receive no emails either.

Yet another edit:
Here is one of my emails in /var/mail/drsmall:
> From MAILER-DAEMON Tue Nov 20 17:09:50 2007
Return-path: <>
Envelope-to: drsmall@darkghost
Delivery-date: Tue, 20 Nov 2007 17:09:50 -0500
Received: from Debian-exim by darkghost with local (Exim 4.63)
	id 1IubHy-0002gG-HR
	for drsmall@darkghost; Tue, 20 Nov 2007 17:09:50 -0500
X-Failed-Recipients: [email]xoxox@xoxoxo.com[/email]
Auto-Submitted: auto-replied
From: Mail Delivery System <Mailer-Daemon@darkghost>
To: drsmall@darkghost
Subject: Mail delivery failed: returning message to sender
Message-Id: <E1IubHy-0002gG-HR@darkghost>
Date: Tue, 20 Nov 2007 17:09:50 -0500

This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  [email]xoxox@xoxoxxo.com[/email]
    Mailing to remote domains not supported
How would I enable mailing to remote domains ?

Dr Small

---

### Post by jordank on 2007-11-20
Alright, well i'm not exactly understanding the script you posted, and i also need to add a pause part to the script that waits 3 minutes before executing the whole thing.

As for getting it to work, you just needed to type:
sudo dpkg-reconfigure exim4-config

from there, it should give you a sequence of steps to go through.  Most of the default settings are good enough, so you can pretty much just press "enter" to go through most of the steps.
However, i found the most important step was i think the first one.
When you are prompted:

general type of mail configuration

choose the first option, the one starting with "internet site"

Then from there, just go through the steps, read and hit enter for the rest of the steps i believe. configure as need be. but i think the most important was the first step i mentioned above.
Give that a try.

---

### Post by jordank on 2007-11-20
reading through the script it's making a bit more sense, still a little fuzzy, but yeah, still the same question with the pause, but i think i'm understanding more now.

---

### Post by Dr Small on 2007-11-20
I'll explain the script, but I have no idea how to make it pause. Your network device SHOULD be started at bootup, so it's odd that it has a 3 minute delay...

Anyhow,
The bash script. Save it as "mailip", and make sure this is the contents of it:
```
#!/bin/bash
ifconfig | awk '{print $2}' | head -2 | tail -1 | sed 's/addr://' | mail -s "MY IP" jordler@hotmail.com
```

Basically, we have to call a shell, and in this instance, we are calling /bin/bash. The rest of it is the command to send you the IP to your email address. Save this file (in your home folder, preferably) and give it executable permissions (meaning it can now be executed).
```
chmod +x mailip
```

Now we want to add it to startup, so we make a symbolic link from mailip to /etc/init.d/mailip:
```
sudo ln -s /home/drsmall/mailip /etc/init.d/mailip
```
(Of course, change 'drsmall' to your username, otherwise it won't work).

Now we are actually going to add it to the update.rcd startup, so it will be executed at startup:
```
update-rc.d mailip defaults
```

And like I said, I don't know how to make it have a 3 minute delay at startup, so I can not help you out there, but I thought I would take the time and explain what all of those commands do, as to enlighten you on that matter :)

Dr Small

---

### Post by MegaJim on 2007-11-20
You can just use sleep

```
sleep 180
```

---

### Post by Dr Small on 2007-11-20
> **MegaJim said:**
> You can just use sleep

```
sleep 180
```
I learn something new every day :D
That should do the trick, if nothing else will :)

*Dr Small adds sleep to his command list!

---

### Post by jordank on 2007-11-20
so i would put that infront of my whole line? or what?

Would it be:

sleep 180 | (rest of command here) ?

---

### Post by MegaJim on 2007-11-20
Put it after the line that declares the shell, but before the command you want to run

---

### Post by Dr Small on 2007-11-20
Example:
```
#!/bin/bash
sleep 180
ifconfig | awk '{print $2}' | head -2 | tail -1 | sed 's/addr://' | mail -s "MY IP" jordler@hotmail.com
```

---

### Post by jordank on 2007-11-20
hey, should the mailip file be saved as .sh?

like open up a text editor, save it as mailip.sh?

What's the process for that?

---

### Post by Dr Small on 2007-11-20
You can save it for mailip.sh, but it makes not matter.
You would just have to go back and edit everything where it says mailip and change your shell in the script to sh instead of Bash, but why go through all of that when you could just name it mailip ?

---

### Post by MegaJim on 2007-11-20
or simply

```
mv mailip mailip.sh
```

---

### Post by Dr Small on 2007-11-20
But just in general, the "mailip" file should be saved with the name of "mailip".

---

### Post by jordank on 2007-11-20
okay, i just used mailip, but i'd rather put it in the .gnome folder, just so it's out of view.

[email]kristie@Sparktop:~/.gnom[/email]e$ chmod +x mailip
[email]kristie@Sparktop:~/.gnom[/email]e$ sudo ln -s /home/.gnome/mailip /etc/init.d/mailip
[email]kristie@Sparktop:~/.gnom[/email]e$ update-rc.d mailip defaults
update-rc.d: /etc/init.d/mailip: file does not exist


what was the problem?

---

### Post by Dr Small on 2007-11-20
You made a symbolic link that goes nowhere.
Look, I'm sure you placed mailip in "/home/kristie/.gnome/" instead of /home/.gnome/

Dr Small

---

### Post by jordank on 2007-11-20
urgh.
there must be something wrong.

kristie@Sparktop:~$ cd .gnome
[email]kristie@Sparktop:~/.gnom[/email]e$ chmod +x mailip
[email]kristie@Sparktop:~/.gnom[/email]e$ sudo ln -s /home/kristie/.gnome/mailip /etc/init.d/mailip
[sudo] password for kristie:
ln: creating symbolic link `/etc/init.d/mailip' to `/home/kristie/.gnome/mailip': File exists
[email]kristie@Sparktop:~/.gnom[/email]e$ update-rc.d mailip defaults
update-rc.d: /etc/init.d/mailip: file does not exist


i tried cd'ing back to my home directory and trying
update-rc.d mailip defaults
again, and got the same result. what's up?

---

### Post by jordank on 2007-11-20
anyone know how to use the update-rc.d command?

---

### Post by jordank on 2007-11-21
maybe this would better be posted as a new thread involving scripts

---

### Post by Dr Small on 2007-11-21
> **jordank said:**
> urgh.
there must be something wrong.

kristie@Sparktop:~$ cd .gnome
[email]kristie@Sparktop:~/.gnom[/email]e$ chmod +x mailip
[email]kristie@Sparktop:~/.gnom[/email]e$ sudo ln -s /home/kristie/.gnome/mailip /etc/init.d/mailip
[sudo] password for kristie:
ln: creating symbolic link `/etc/init.d/mailip' to `/home/kristie/.gnome/mailip': File exists
[email]kristie@Sparktop:~/.gnom[/email]e$ update-rc.d mailip defaults
update-rc.d: /etc/init.d/mailip: file does not exist


i tried cd'ing back to my home directory and trying
update-rc.d mailip defaults
again, and got the same result. what's up?
Did you make sure mailip was in .gnome ?
If it is, and you have chmodded the file, and created a symbolic link, and all was successful, try this:
```
sudo update-rc.d mailip defaults
```

if it says /etc/init.d/mailip doesn't exist again, trying looking in /etc/init.d/ and see if it DOES exist.

---

### Post by jordank on 2007-11-21
jordan@Jorcomp:~$ sudo update-rc.d mailip defaults
[sudo] password for jordan:
 System startup links for /etc/init.d/mailip already exist.

alright, that's in there, but i'm really not seeing anything happen on startup.
it should be creating a file on my desktop and sending me an email. I'm not getting either.

Urgh.

---

### Post by jordank on 2007-11-21
Also, i seem to be experiencing problems with the mail command.

I type 
mail [email]address@example.com[/email]
press enter
it asks for 
cc
subject
and from there i can type my message
when i'm finished writing it, i press Control+D
None of these messages ever seem to send.  I don't know if it's because Control+D is not the right command to send my message, or if it has something to do with my configuration, any help is awesome!

---

### Post by jordank on 2007-11-21
i dont understand how my mail function has stopped working.  Now when i type the command, it doesn't send anymore.  I'm really having trouble understanding this whole idea.

Main problems:
My script does not run on startup. Surely this can not be that hard to do

My mail program is very unreliable. Sometimes it sends, sometimes it doesnt.  I don't know what causes it to send.

I can't write regular emails, ones that arent in strings of commands, as seen on the first page of this thread.


What configurations are essential for sending emails?  Why would it be inconsistent with sending emails?
Also, why do only some email applications recieve these emails?  Only gmail, in my experience, has been able to recieve mail from the command line.

---

### Post by MegaJim on 2007-11-21
why don't you give ddclient a go? it takes about 5 minutes to install and configure

---

### Post by Dr Small on 2007-11-21
> **jordank said:**
> i dont understand how my mail function has stopped working.  Now when i type the command, it doesn't send anymore.  I'm really having trouble understanding this whole idea.

Main problems:
My script does not run on startup. Surely this can not be that hard to do

My mail program is very unreliable. Sometimes it sends, sometimes it doesnt.  I don't know what causes it to send.

I can't write regular emails, ones that arent in strings of commands, as seen on the first page of this thread.


What configurations are essential for sending emails?  Why would it be inconsistent with sending emails?
Also, why do only some email applications recieve these emails?  Only gmail, in my experience, has been able to recieve mail from the command line.
It sounds like the mail application isn't starting at startup, which it should be.

---

### Post by jordank on 2007-11-21
How, do i use DDclient, what is it, and more importantly, is it something you see at startup? because i only want something that runs in the background, something that you don't see.


Also, why wouldnt the mail client be loading at startup?

---

### Post by MegaJim on 2007-11-21
ddclient runs (by default) as a daemon at startup.  It determines the IP address of your computer then publishes it to a DNS server of your choice supporting a number of protocols.

Simply 
1. go to [www.dyndns.com](www.dyndns.com) (or other supported service) and create a free account
2. Create a new hostname for your computer on the site
3. Install ddclient and follow the instructions that popup in the config menu

done.

The daemon scans every 300 seconds (this can be configured) for your IP and publishes it to the site if it has changed, once you have done this once that is all you need to do...

later on at a remote location you can access your computer by using that hostname, for example my box is setup to be *****.dyndns.org (hehe, the stars are something else) whenever i type that into a web browser at uni I get to my webinterface for remote management and stuff, despite the dynamic IP where the ubuntu box lives.

---

