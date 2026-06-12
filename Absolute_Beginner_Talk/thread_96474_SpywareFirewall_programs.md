---
title: "Spyware/Firewall programs"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by PinkFloyd56 on 2005-11-28
Thats something I forgot to do >< get some spyware software and a firewall. Does anyone suggest any programs for spyware checking? 


TY :razz:

---

### Post by akiro.yamamoto on 2005-11-28
For firewall you can use Firestarter.
I believe that it's in the repository.
Just use Synaptic to install it.
Regards

---

### Post by PinkFloyd56 on 2005-11-28
[QUOTE=akiro.yamamoto]For firewall you can use Firestarter.
I believe that it's in the repository.
Just use Synaptic to install it.
Regards[/QUOTE]


o.O I know how to get to the Synaptic Manager, but where is the repository? I've only been using it for about a week,

---

### Post by amohanty on 2005-11-28
Synaptic works off of repositories that are specified in /etc/apt/sources.lst
you dont have to do anything for those. just fire up synaptic, hit the search button and install stuff...

HTH
AM

---

### Post by PinkFloyd56 on 2005-11-28
Found it, I tried looking up Firestarter and it wasn't there. I also tried to upgrade my system and it said 1 file in the Synaptic is broke, how do I find it? Theres a lot of stuff there :)

---

### Post by ubuntu27 on 2005-11-29
Firestarter is in System Administration (Universe)

By the way, are your repositories updated?

I belive you did not add Multiverse and Universe.
Go here: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by PinkFloyd56 on 2005-11-29
[QUOTE=ubuntu27]Firestarter is in System Administration (Universe)

y the way, are your repositories updated?[/QUOTE]


Prolly not, I am updating some stuff now, but as soon as it's done I need to find the broken file then update my system. When I got the installation CDs Breezy just came out, and when I installed it there where 116 updates available. I had to reinstall it now there is probably more.:rolleyes:

---

### Post by amohanty on 2005-11-29
You have to enable universe in your list of repositories:

Some links that will help:
[https://wiki.ubuntu.com/AddingReposi...ositories%](https://wiki.ubuntu.com/AddingReposi...ositories%) 29
[http://ubuntuguide.squarecows.com/doku.php#repositories](http://ubuntuguide.squarecows.com/doku.php#repositories)

HTH
AM

---

### Post by bionnaki on 2005-11-29
you need to have the proper repos in your sources.list
follow these instructions: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by PinkFloyd56 on 2005-11-29
Well, to my suprise my whole system is up-to-date. I'm goin to try and update to breezy.

Thanks for your help!!

---

### Post by Danielle on 2005-11-29
for scanners you could get clamav and rkhunter. calm is an antivirus which i think you should have if you have any contact with windows, though more for windows then ubuntu. and rkhunter is a rootkit scanner which is more important to have and run. don't forget to update the scanners before you run them. if a scanner ever finds anything don't delete it straight away, ask about the file here first, it could be a false-positve.

here's a screenshot of all the files i downloaded for clam using synaptic they're marked with a green square. than when the files are installed you can run it by typing sudo clamtk. it wouldn't update without the sudo and i think it will need it if it ever needs to delete/rename a file.

---

### Post by PinkFloyd56 on 2005-11-29
I tried searching for clamav but I couldn't find it... :confused:

---

### Post by amohanty on 2005-11-29
For rootkits I use chkrootkit, I think its in the universe repos. Just add it to your crontab and it will check and mail you the results nightly.

Before you ask, at the terminal do a:
man crontab

HTH
AM

---

### Post by PinkFloyd56 on 2005-11-29
Alright, i'm gunna have to do this tomarrow. My moms whinning to get me off the PC.

---

### Post by Danielle on 2005-11-29
have you tried running?:
sudo apt-get update

---

### Post by Danielle on 2005-11-29
[QUOTE=amohanty]For rootkits I use chkrootkit, I think its in the universe repos. Just add it to your crontab and it will check and mail you the results nightly.

Before you ask, at the terminal do a:
man crontab

HTH
AM[/QUOTE]
what's the command for it? i have chkrootkit installed. thanks

---

### Post by Perfect Storm on 2005-11-29
You may check this a Howto I made - [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

Spyware/malware/etc. is aonly a previlage for the Windows users ;)

---

### Post by ubuntu27 on 2005-11-29
[QUOTE=PinkFloyd56]Well, to my suprise my whole system is up-to-date. I'm goin to try and update to breezy.

Thanks for your help!![/QUOTE]

Woah! You are using Hoary? I though you were using Breezy that's way I gave that link. ><

---

### Post by amohanty on 2005-11-29
[QUOTE=Danielle]what's the command for it? i have chkrootkit installed. thanks[/QUOTE]


cron is a service that runs specified programs at specific times (ala windows scheduler, though its much much older than windows). you can create a cron job by typing at the command prompt 
crontab -e
this will fire up nano, 

so for e.g. to run chkrootkit as a nightly job and send it as an email to you
type the following in the editor it opens up
59 23 * * * chkrootkit 2>&1 | mail -s "chkrootkit output for" $USER

save and quite the editor
That will run chkrootkit at 11:59 pm every night and pipe all output and errors to the mail program which will send it the user whose crontab its running.

To get the mail program
sudo apt-get install mailutils

You will also need an smtp server on your box to use the mail program, eg postfix, qmail or sendmail (in my order of preference).

HTH
AM

---

### Post by adduds on 2005-11-29
How do you use firestarter after it's installed???

thx/cheers,
ad

---

### Post by Danielle on 2005-11-29
[QUOTE=amohanty]cron is a service that runs specified programs at specific times (ala windows scheduler, though its much much older than windows). you can create a cron job by typing at the command prompt 
crontab -e
this will fire up nano, 

so for e.g. to run chkrootkit as a nightly job and send it as an email to you
type the following in the editor it opens up
59 23 * * * chkrootkit 2>&1 | mail -s "chkrootkit output for" $USER

save and quite the editor
That will run chkrootkit at 11:59 pm every night and pipe all output and errors to the mail program which will send it the user whose crontab its running.

To get the mail program
sudo apt-get install mailutils

You will also need an smtp server on your box to use the mail program, eg postfix, qmail or sendmail (in my order of preference).

HTH
AM[/QUOTE]
thanks, i'll have to do some reading. i haven't spent enough time reading up on breezy yet. it would be nice to have a smtp server though. would it have to be on 24/7?

---

### Post by akiro.yamamoto on 2005-11-29
It seems very similar to ZoneAlarm it's very simple to set up...
Just go to Applications >> System Tools >> Firestarter
It will ask you for your password.
You'll be asked some simple questions the first time you run this prog.
Just go through the steps, the defaults are probably safe...
Just ensure that you specify which device/network you want to protect.
Eg if you use dialup you probably want ppp0.. etc.

Hope this helps..
If you need more detailed info you can check the the Help supplied with 
firestarter itself...

Regards

---

### Post by amohanty on 2005-11-29
> thanks, i'll have to do some reading. i haven't spent enough time reading up on breezy yet. it would be nice to have a smtp server though. would it have to be on 24/7?

These are actually all GNU tools, available on all flavors of GNU/Linux. Documentation at: [http://www.gnu.org/manual/manual.html](http://www.gnu.org/manual/manual.html)

Unless you are using the SMTP server to recieve email, no it does not need to be on 24/7. Moreover if you are not experienced, I would strictly advise against it, because if its not configured properly it could be hijacked to be used as an open proxy ([http://en.wikipedia.org/wiki/Open_proxy](http://en.wikipedia.org/wiki/Open_proxy)) to send spam.

Typically you would set up the mail server to use some other SMTP server like gmail or myrealbox to send your email _out_ and use fetchmail to get your email to those accounts _in_ via POP or IMAP.

HTH
AM

---

### Post by Danielle on 2005-11-29
thanks, i asked because i wouldn't trust my computer being on all the time, not really for security more because i don't trust the hardware. although i don't want to be in a bot army lol

i'm going to read about it all later. thanks for the help :)

---

### Post by adduds on 2005-11-29
[QUOTE=akiro.yamamoto]It seems very similar to ZoneAlarm it's very simple to set up...
Just go to Applications >> System Tools >> Firestarter
It will ask you for your password.
You'll be asked some simple questions the first time you run this prog.
Just go through the steps, the defaults are probably safe...
Just ensure that you specify which device/network you want to protect.
Eg if you use dialup you probably want ppp0.. etc.

Hope this helps..
If you need more detailed info you can check the the Help supplied with 
firestarter itself...

Regards[/QUOTE]

Ya i had to re-boot cause i did check their b4, but i re-booted and it's working nicely, in the sys-tray :)

thx again,
cheers,
ad

---

