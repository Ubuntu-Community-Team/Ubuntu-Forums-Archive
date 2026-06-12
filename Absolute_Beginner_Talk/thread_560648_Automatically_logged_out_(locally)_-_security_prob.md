---
title: "Automatically logged out (locally) - security problem?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Winawer on 2007-09-26
Hello,

I'm a fairly new switcher to Ubuntu, though I've poked around a tiny bit with it in the past.  But I had a problem today which freaked me out a little bit, and I'm hoping that somebody might be able to shed some light.  

When I left this morning, I was still logged into my system, and I had left some programs running.  When I got home this afternoon I was back at the login screen, and everything I had left running was shut off.  I was a little worried as to why it had shut down (and a little peeved that I'd lost the results of the analysis that I was running), so I decided to try out these "log files" I keep hearing about. :)  Something immediately jumped out at me when I looked at /var/log/auth.log:  I have hundreds of messages like this:

> Sep 26 06:20:56 ***** sshd[20816]: Invalid user tester from 213.30.139.91
Sep 26 06:20:57 ***** sshd[20816]: reverse mapping checking getaddrinfo for reverse.completel.net failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 26 06:20:57 ***** sshd[20816]: (pam_unix) check pass; user unknown
Sep 26 06:20:57 ***** sshd[20816]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=213.30.139.91 
Sep 26 06:20:58 ***** sshd[20816]: Failed password for invalid user tester from 213.30.139.91 port 43586 ssh2
Sep 26 06:20:59 ***** sshd[20818]: Invalid user firewall from 213.30.139.91
Sep 26 06:20:59 ***** sshd[20818]: reverse mapping checking getaddrinfo for reverse.completel.net failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 26 06:20:59 ***** sshd[20818]: (pam_unix) check pass; user unknown
Sep 26 06:20:59 ***** sshd[20818]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=213.30.139.91 
Sep 26 06:21:01 ***** sshd[20818]: Failed password for invalid user firewall from 213.30.139.91 port 44710 ssh2
Sep 26 06:21:02 ***** sshd[20823]: Invalid user firewall from 213.30.139.91
Sep 26 06:21:02 ***** sshd[20823]: reverse mapping checking getaddrinfo for reverse.completel.net failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 26 06:21:02 ***** sshd[20823]: (pam_unix) check pass; user unknown
Sep 26 06:21:02 ***** sshd[20823]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=213.30.139.91 
Sep 26 06:21:05 ***** sshd[20823]: Failed password for invalid user firewall from 213.30.139.91 port 44991 ssh2
Sep 26 06:21:06 ***** sshd[20828]: Invalid user firewall from 213.30.139.91


I set up ssh on my machine so that I can log in from school, so I know that the port is open.  But then the log file culminates in:

> Sep 26 12:48:47 ***** sshd[2984]: User root from 218.106.252.245 not allowed because not listed in AllowUsers
Sep 26 12:48:47 ***** sshd[2984]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.106.252.245  user=root
Sep 26 12:48:49 ***** sshd[2984]: Failed password for invalid user root from 218.106.252.245 port 58255 ssh2
Sep 26 12:48:57 ***** sshd[2989]: User root from 218.106.252.245 not allowed because not listed in AllowUsers
Sep 26 12:48:57 ***** sshd[2989]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.106.252.245  user=root
Sep 26 12:49:00 ***** sshd[2989]: Failed password for invalid user root from 218.106.252.245 port 59015 ssh2
Sep 26 13:14:45 ***** sshd[5190]: Server listening on :: port 22.

I think this means that either the computer restarted or I was logged out / in, and then I arrived home about an hour later.  None of the other log files really told me all that much of use as to why I was logged out.

My questions are thus:

1).  Are all these attempts to log-in to my system just normal "scanning" - cost of being exposed to the internet, as it were - or do they signify something more directed?

2).  Are they unrelated to my subsequent strange log-out?

3).  If there's no connection, do you have any idea where I might find out more on why I was booted?  Other log files to look at, commands to run, FAQs to hunt through?  I've tried the usual suspects like Google, but I must be asking the wrong questions because I'm not getting any answers...

My gut says that I'm probably overreacting, but I'd rather pack an umbrella than cry in the rain.  Thanks for your help!

---

### Post by reckless2k2 on 2007-09-26
ok...a couple of things.....if you are going to have ssh open to the whole world you should make a few adjustments to the sshd_conf file so you are more secure. 

you need to disable root logins and AllowUsers at the end of the file and specify your user so only you can login via ssh. like this


```
AllowUsers Winawer
```

just reboot your machine. that'll be the easiest thing. 

now, ssh attacks will happen no matter what on an open ssh server. that's the internet for you. it's about being as secure as possible. the other consideration is changing the port number at the top to something like 222 instead of 22. simple things to lesson the attacks but they will still come. 

as far as the logout business, probably a brownout of something. not sure i understand that one but it wouldn't log it out if someone even got in under your name. it doesn't work like that. this isn't windows. haha. you can log into your machine a bunch of times at the same time unless you tell it not to. 

make sure you password is tight with open ssh ports as well. not something silly simple. at least 8 characters with case sensitive, yadda yadda.

got it?

---

### Post by Dr Small on 2007-09-26
[quote=reckless2k2]just reboot your machine. that'll be the easiest thing. [/quote]

Or, a faster way:
```
sudo /etc/init.d/ssh restart
```

---

### Post by Winawer on 2007-09-26
Thanks, reckless2k2 and Dr. Small - I've secured ssh like you suggested, and that seems fine.  The logout thing is still bugging me, though.  A brownout seems unlikely, because I have more than one machine on this network, and they didn't go down (they're also all plugged into the same surge protector).  Any other ideas?

---

