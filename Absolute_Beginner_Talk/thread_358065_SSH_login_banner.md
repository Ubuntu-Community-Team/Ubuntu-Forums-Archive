---
title: "SSH login banner"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by zappadragon on 2007-02-10
So I followed the directions i found on another post. This is what I did:

You will have to modify /etc/ssh/sshd_config, one time only, to enable
the "banner" option. If you change "#Banner /etc/issue.net" to
"Banner /etc/issue.ssh", then restart sshd, you can then create and
maintain the banner file using figlet or any other tools. If the file
is created so that you can write it as yourself, then you won't need to
use sudo

Now when I login it asks for my username and then give me my ssh login banner. I want to have the full banner I created as soon as users ssh to the server. Is there any way I can have the banner pop up before the users type in there usernames?

Thanks.

---

### Post by jpeddicord on 2007-02-10
Try changing the /etc/issue.ssh part to just /etc/issue. Then edit the /etc/issue file. It works fine here on my PC using just that. :) 

For reference, /etc/motd is the file that appears after users login, and /etc/issue is before. Bothh can be very handy. :)

---

### Post by zappadragon on 2007-02-10
I tried that and I have my login banner working but when I ssh to the box I get :
login as:
 Then after I type my username I get my banner then the prompt for a password. I want to be able to ssh to the box and get teh banner then the login as prompt.

---

### Post by JHStealth on 2008-01-23
Did you ever get it to work, Zappadragon?   I just ran into this today after putting up a banner for the first time.   I enter my username and then it shows the banner.   

I'm running 7.10
Banner path is:

/etc/issue.net

I've tried pointing it to:

/etc/issue

as well as a third file that I created as a test.   It doesn't seem to matter which I use, the result is the same.  The banner is shown after I enter my user name and I want it to appear on connect prior to entering the user.

I am connecting to it via Putty from a non-linux system.   Could that be the problem, perhaps?

---

### Post by bodhi.zazen on 2008-01-23
What I do, 

in /etc/sshd-config 

Banner /etc/issue.ssh

put your text (banner) in issue.ssh

BUT it does not work with Putty

References :

[http://www.cyberciti.biz/tips/change-openssh-sshd-server-login-banner.html](http://www.cyberciti.biz/tips/change-openssh-sshd-server-login-banner.html)

Putty [http://www.derkeiler.com/Newsgroups/comp.security.ssh/2002-10/2611.html](http://www.derkeiler.com/Newsgroups/comp.security.ssh/2002-10/2611.html)

> You are aware that you can't expect to see the login banner before
the username prompt, aren't you? Due to an unfortunate protocol
misfeature in SSH2, the earliest the banner can usefully be
displayed is _after_ prompting for the username and before the
password or passphrase prompt.

SO, when I ssh from linux -> banner is PRIOR to entering user name

ssh windows (putty) -> banner is AFTER entering user name

---

### Post by szandor on 2008-07-06
> **bodhi.zazen said:**
> 
BUT it does not work with Putty

what about plink?

> **bodhi.zazen said:**
> 
SO, when I ssh from linux -> banner is PRIOR to entering user name

the username is already passed. banner appears first then your password is requested next to your login.

> **bodhi.zazen said:**
> 
ssh windows (putty) -> banner is AFTER entering user name

no. only when you pass the username through putty via the auto-login username option in connection data.

---

