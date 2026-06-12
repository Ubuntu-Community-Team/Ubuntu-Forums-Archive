---
title: "[SOLVED] Two simple questions. (Bash and cron)"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-03-27
I have two different questions here.
1.) When I login to my server via SSH, right above the prompt, I get:
```
You have mail.
Last login: Thu Mar 27 11:37:41 2008 from darkghost
```

What file is these commands in?
I have checked /etc/profile and /etc/bash.bashrc but can not find anything about them.

2.) I have a cronjob setup to run @daily I am constantly getting mail from this cronjob. Here is my crontab:
```
@daily ~/bin/db_backup 2& > /dev/null
```

I thought that "2& > /dev/null" was supposed to suppress and messages?
The mail is not about errors, but rather success. Maybe I have something wrong there though...

Anyhow, if anyone can enlighten me on these two question, I would be grateful :)

Thanks,
Dr Small

---

### Post by scottro on 2008-03-27
I think it's 
cronstuff > /dev/null 2>&1

The redirector usually comes at the end. 

As for the mail, it's probably some system message, (probably from cron).  I use mutt, which always checks the default, usually /var/spool/mail or /var/mail before other things.  

Y'know, I never have looked into what file prompts the system to give you that message.  Sorry I can't give more information there.

---

### Post by opscure on 2008-03-27
I believe the ssh welcome message is located in ```
/etc/motd
```

As for the cron issue you should edit your crontab file ```
/etc/crontab
``` and enter ```
MAILTO=""
```

Then execute ```
crontab
``` to update cron with the new information.

When mailto is not defined it automatically send a message to the user.

For more information about crontab see: 
[http://www.hmug.org/man/5/crontab.php](http://www.hmug.org/man/5/crontab.php)

---

### Post by Dr Small on 2008-03-27
Ok, thanks for the information.
I was browsing around, and found that login is executed when logging in via SSH, and the New Mail message is executed from /etc/login.defs :)

I had to do some reading in man pages to figure that one out :)
Also, I am going to try the MAILTO trick before changing the redirection to /dev/null. If MAILTO doesn't work, I'll try the former. Because I believe there are multiple ways to use redirection to /dev/null

Thanks again for the help!

Dr Small

---

### Post by hyper_ch on 2008-03-27
> **scottro said:**
> I think it's 
cronstuff > /dev/null 2>&1

yes it is

---

### Post by rkd on 2008-03-27
For login from a local terminal, those messages are displayed by the login program before it starts your shell.  

For login via ssh, sshd handles the login steps and so sshd displays those messages.

For redirecting the output:

>   x        redirects stdout to file x
2>  x       redirects stderr to file x
&>  x       redirects both stdout and stderr to file x

You were probably thinking of 2>&1 which sends stderr to the same file as whatever stdout is, but got a little mixed up about it.

---

### Post by ahsile on 2008-03-27
It's also possible to create a file named .forward in your home folder, and place a real email address in it. This will foward any messages to your 'user' account where you want them to go.

---

### Post by Dr Small on 2008-03-30
Ok, so taking the advice opscure and rkd, I have added:
```
MAILTO=""
```

To /etc/crontab and then I edited my crontab to say:
```
@daily ~/bin/db_backup &> /dev/null
```

And I am still receiving mail. Maybe I should add the MAILTO varible to my crontab, instead of /etc/crontab ? It's really strange, and the mail contains no errors, but simply is showing the output of wget.

Here is the header of one of the mail files:
```
From: Cron Daemon <root@mycroft>
To: drsmall@mycroft
Subject: Cron <drsmall@mycroft> ~/bin/db_backup &> /dev/null
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/drsmall>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=drsmall>
```

Any other ideas? ... because this is beginning to become annoying.

Dr Small

---

### Post by rkd on 2008-03-30
What is ~/bin/db_backup?  Could it be doing something that causes the redirection to be ignored?  I don't know what could do that, since I'm not very experienced yet with Linux, but maybe there is something that could cause that.

But aside from that, the MAILTO="" is supposed to suppress ANY mail, so if you have that set properly, the redirection stuff should not matter.

So check your crontab again to be sure the MAILTO="" didn't get lost or mangled somehow.

Could there be another crontab somewhere that you aren't changing that is causing the mail to be sent?  I know that seems unlikely, but I thought it might be worth thinking about.

---

### Post by Dr Small on 2008-03-30
~/bin/db_backup is a script I wrote to backup my database from the internet.
It simply uses wget to download the latest and greatest database.

I do not use /etc/crontab, and I think this is where all the problems are pouring in from. I use the crontab for my account, by running:
```
crontab -e
```

I have not added MAILTO to it yet, and that is probably the problem.

---

### Post by rkd on 2008-03-30
Oh, I didn't read your posts carefully enough.  Definitely, the MAILTO setting applies ONLY to the crontab it is in, so the one you put into /etc/crontab naturally has no effect in your personal one.

It would be good to solve the problem with redirection, since using MAILTO="" will keep you from seeing any error from any crontab work.  I can think of a couple of experiments to try.

1.  Change the command to redirect stdout and stderr separately: ```
@daily ~/bin/db_backup >/dev/null 2>/dev/null
```I kind of doubt that will make any difference, but just in case the &> isn't being recognized somehow, this might help.

2. Go inside the db_backup script and put the output redirection on each command in there as well.  I don't know how output redirection propagates from the script invocation command to the individual commands inside the script.  Maybe it doesn't propagate.  Unless you have a large number of commands in the script, this should be easy to try.

Once you manage to get the mails to stop, it might be good to try redirecting only the stdout so that if any errors happen, you will get notified of that.  Of course, if the circumstances are such that you don't even want notification of errors, then forget about this suggestion.

---

### Post by Dr Small on 2008-03-30
Ok, thanks there. I'll try that out. The strange thing is, I have another script in my crontab that uses the identical redirection and never sends me an email:
```
@hourly ~/bin/IPupdate &> /dev/null
```

But in this script, differenting from the other one, I am using wget -q, which means quiet. No messages are outputted. And I don't get any mail.

---

### Post by rkd on 2008-03-30
As I understand it, cron only sends mail if the command you have it run produces output.  

So the fact that your script that doesn't produce output doesn't send mail seems quite consistent with that.

The puzzle is why the script whose output you are sending to /dev/null causes cron to send mail.  There probably is some good explanation, but I know next to nothing about using cron, so I probably won't figure it out quickly.

Is there some reason that you don't use the -q on the wget in this script?  That wouldn't solve the puzzle, but it seems it would eliminate the problem!

---

### Post by Dr Small on 2008-03-30
It is quite simple to change the script to use -q on wget, but I don't want to do that for every script I write. Hence the reason I asked about redirection, and I guess I'll just play with it for awhile until I get it perfect :)

Might as well call it "Case Closed".

Thanks for all the help, everyone!

Dr Small

---

### Post by rkd on 2008-03-30
I'm willing to continue to help you get it working the way you would like.  But if you want to drop it at this point, that's okay with me.

---

