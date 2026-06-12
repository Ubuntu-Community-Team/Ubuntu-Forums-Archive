---
title: "ESMTP - How I Made it Work"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by discodan on 2008-02-16
Hi,

I am a recent convert from Windows Server, and I have been struggling to figure out how to send log files to my comcast.net email account.

Here's how I did it on Ubuntu 7.10 server:

(I'll list the steps in order, but I doubt that the sequence made a difference)

1:  Install 7.10 server
2:  Disabled CDRom from /etc/apt/sources.list
3:  Update System (I usually had to go thru 3 or 4 sets of apt-get update and apt-get upgrade before all updates applied)
4:  apt-get install esmtp esmtp-run
5:  dpkg-reconfigure esmtp
6:  follow the prompts to provide your external smtp server name, smtp username, and smtp password  
7:  leave tls disabled
8:  use procmail to send
9:  apt-get install procmail
10:  apt-get install mailutils
11:  vi /etc/esmtprc
12:  add quotes around username and password
13:  save an close esmtprc
14:  test... echo "test" | mail -s "test" [email]username@domain.com[/email]

sorry so short, very busy...

For me the key was adding the quotes around the smtp credentials.  After writing this out, I suspect that you could include the quotes in step 5 and 6.

Well, hopefully this will help someone else out there.

Merry emailing,

-disco-

---

### Post by dcstar on 2008-02-16
> **discodan said:**
> Hi,

I am a recent convert from Windows Server, and I have been struggling to figure out how to send log files to my comcast.net email account.

Here's how I did it on Ubuntu 7.10 server:
.......

Here's how my 7.10 system was set up to e-mail me log files:

Install the ** postfix** and **mailx** packages - done!

---

### Post by discodan on 2008-02-16
Hi David,

Thanks for the reply.  Did you have to do any configuring of postfix?  I had trouble with this because the smtp server for comcast.net requires authentication.

That was why I needed esmtp.  It allows for credentials to entered for the smtp server.

-disco-

---

