---
title: "Sending an email via script without an MTA"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by buzz_bomb on 2007-12-28
Howdy,
I have an Ubuntu server that I use for backups of workstations at home.  I am putting together a script that will tell me when the last successful backup was and how much disk space is left.  The only trouble I am having is sending an email of this status from a script.

The objective is to find the simplest way to send email to my external gmail account without installing any email server software like postfix, exim4, etc.  I don't need to receive mail, just send.  

I have tried exim4 anyway but could not get it to work, probably because of my ISP, comcast.  Another possible reason is that I didn't know what I was doing.  Right now I am attempting to solve this problem using mutt and a python script called putmail, as described in [_this thread_.]("http://ubuntuforums.org/showthread.php?t=481366") Unfortunately no luck as I am getting an error parsing the configuration file when trying to send from Mutt.  

Any suggestions for accomplishing what I thought would be an incredibly straightforward task?

Thanks.

---

### Post by Dr Small on 2007-12-28
If you have another host somewhere else on the internet, you could setup a sendmail script (with php), and just use wget to download the file, and it would automatically send you an email.

Dr Small

---

### Post by buzz_bomb on 2007-12-28
Dr Small,
Thanks for the reply to my post.  Does establishing a sendmail script with PHP require that sendmail be installed?  I guess I was essentially trying to emulate at the command line what Outlook Express does on my Windows box:  send a message through smtp.comcast.net to my (or any) external account.  Like this:

cat backupresults.log | [insert mail program here] -s 'Backup Results!' [email]myemail@gmail.com[/email]

---

### Post by Dr Small on 2007-12-28
Yes, sendmail would need to be enabled on the host, but here is what I was thinking:

(Incase you couldn't get the MTA working {which is hard})
You could have a remote host, like some other hosting company (free?) that has Php and Sendmail support. You could then have a sendmail script which would send you a predesigned message to your email account, by using wget on the system doing the backups.

Dr Small

---

### Post by Adtk on 2007-12-28
There is also sendEmail ([http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)), which is what I am planning on using for roughly the same purpose.  I'm just having a few issues at the moment (probably me not reading instructions) other than that it seems to do the trick.

---

### Post by jfehribach on 2007-12-29
I found this thread since I was frustrated trying to get 'sendmail' to work.  I saw the reference to 'sendEmail' and got that up and running in maybe an hour or two.  I am using the option:
 -s "smtp.gmail.com:587" 
which is just the server I'd prefer.

Thanks to Adtk for mentioning 'sendEmail'.

Jerry Fehribach

---

### Post by buzz_bomb on 2007-12-29
sendEmail worked great!  Installed and had it working in about 10 minutes, which is just about the fastest I've ever figured anything out on my new Ubuntu server.  Thanks Adtk for the suggestion and everyone for your input.

---

### Post by Adtk on 2007-12-30
One issue I did come across is that sendEmail doesn't like long/complicated passwords. (or doesn't seem to send it all through to GMail)

I got this, until I changed to a simpler password:

sendEmail[9215]: ERROR => Received:    535 5.7.1 Credentials Rejected m1sm39010216uge.85

---

### Post by scorp123 on 2007-12-30
> **buzz_bomb said:**
> sendEmail worked great!  Installed and had it working in about 10 minutes, which is just about the fastest I've ever figured anything out on my new Ubuntu server.  Thanks Adtk for the suggestion and everyone for your input. You should take a look at the "mailx" command. It's available via the repos too (sudo apt-get install mailx). Wikipedia article on "mailx":

[http://en.wikipedia.org/wiki/Mailx](http://en.wikipedia.org/wiki/Mailx)

---

### Post by Sir.Babau on 2008-01-30
> **Adtk said:**
> There is also sendEmail ([http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)), which is what I am planning on using for roughly the same purpose.  I'm just having a few issues at the moment (probably me not reading instructions) other than that it seems to do the trick.

A thousand thankyous. I was losing my mind with mailx and sendmail. sendEmail worked within 30 seconds of grabbing it from the repos.

---

