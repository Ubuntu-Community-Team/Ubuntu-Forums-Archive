---
title: "Internal email on my machine"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by jreid08 on 2006-10-18
I want to set up email on my Ubuntu 6.06 machine so that users on my machine can send email to each other locally only in that I don’t want mail to leave the machine.  I don’t have it on a dmz nor do I want it on one or open to the public – ports 80, 25, yada, yada...  Basically, what do I have to do so that user1@mymachinename can send messages to user2@mymachinename?

Basically there might be a situation where my wife is being “watched” at work.  Rather than having her email me with her web based email I’m thinking it might be better for her to use Putty, log into her account on my machine and email me locally?

That’s what I want to accomplish, unless that’s not more private or there’s a better or more efficient way to handle it.

Is this something that’s easy enough for a total newbie to do or does it take advanced skill.  What are the steps I need to follow to accomplish my goal?  My initial thought is that what I want to do is different and perhaps easier to do than most of the email questions I’m seeing on this forum.

Thanks for any help!
JR

---

### Post by kidders on 2006-10-18
Hi there,

Afaik, your system should already be able to do what you're describing without any tweaking. If not, install sendmail. A more elabourate alternative would be to use an SMTP server (like postfix), but this is totally unnecessary if you're only interested in sending mail to a single box.

Many Linux apps depend on the ability to send mail to local users to function properly, so *not* having at least some form of mail handler on your system is ill-advised.

**Edit:** Btw, it's very likely that getting caught using SSH in a workplace will get you fired. In most countries, employers are legally responsible for things their employees do with their network, so they need to monitor all use of it to be sure what's going on is consistent with their workplace policies. SSH connections can't be monitored effectively, and are usually banned.

---

### Post by jreid08 on 2006-10-18
She works for a small 4 person family owned business and they don’t have an “Internet” or “email” policy.

Okay, so I’m a newb… after I login, and type “mail” I get “-bash: mail: command not found.”  Now, please keep in mind that the last flavor of linux I used was Suse.  If doing internal mail on Ubuntu is different would you please explain it.  How do I access, read and send messages to other accounts on my machine?

Lastly, can I use pine with the solution I’m looking for?  If so, what’s the installer for pine called because I did a sudo apt-get install pine and I get the message “Package pine is not available, but is referred to by another package.”

Thanks for any help,
JR

---

### Post by kidders on 2006-10-18
> **jreid08 said:**
> She works for a small 4 person family owned business and they don’t have an “Internet” or “email” policy.Excellent :-)

You'll probably need to check that you have access to the right repositories for packages like sendmail & pine ... Afaik pine has some licensing issues that may be keeping it out of the main ones, for instance. Alternatively, Debian packages *should* also do the trick.

Once you've installed the right packages, mail should work just like it does on Suse. Typically, mail is stored in users' homes (either as mboxes or maildirs ... up to you), and most mail clients (including pine) can handle either or both. Have you used sendmail & pine on Suse before?

Hope that helps.

---

### Post by jreid08 on 2006-10-19
I'm sorry for the trouble but I did install everything you mentioned.  Pine is still not installing.

Nothing is working as it did when I used Suse.  When I used Suse it would tell me once I logged in that I had or didn't have mail.  I would simply type 'mail' and I would read mail.  If I wanted to use Pine I would simply type 'pine' and then I'd be using Pine.

What are the commands to send and read mail in Ubuntu?

---

### Post by kidders on 2006-10-20
> **jreid08 said:**
> Pine is still not installing.
Oh dear ... what kind of error are you getting? What version are you using?

> **jreid08 said:**
> When I used Suse it would tell me once I logged in that I had or didn't have mail.  I would simply type 'mail' and I would read mail.
If you like using the "mail" command, you can install it too ... if you take a look in Ubuntu's software database, you'll find it ... it's in a package called "mailx".

---

### Post by nsleiman on 2007-01-09
> **kidders said:**
> Oh dear ... what kind of error are you getting? What version are you using?


If you like using the "mail" command, you can install it too ... if you take a look in Ubuntu's software database, you'll find it ... it's in a package called "mailx".

how to get pine with apt-get?

---

### Post by kidders on 2007-01-09
Hi there,

Make sure you have access to a repository with pine in it and just do **apt-get install pine**. As you may know, pine is not free/open source, so Ubuntu's official repositories can't distribute it.

---

### Post by Aberrix on 2007-01-19
> **nsleiman said:**
> how to get pine with apt-get?

first download the package.

```
wget ftp://ftp.cac.washington.edu/pine/pine_4.64_i386.deb
```

download/install the additional packages needed.

```
sudo apt-get install libssl0.9.7
```

then install the pine .deb

```
dpkg -i pine_4.64_i386.deb
```

and viola! pine is now installed.

---

