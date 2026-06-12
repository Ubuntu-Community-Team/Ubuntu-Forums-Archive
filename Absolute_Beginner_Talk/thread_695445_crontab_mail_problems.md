---
title: "crontab mail problems?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Kasyx on 2008-02-13
Hi, not sure if this is the right place to put this, but it seems like a really basic question (I hope?)...
I have been trying to set up a crontab to get a backup script to run every night at 3am. It runs absolutely fine and has had no issues, the problem is that I have set it to mail me with the output of the script, and it is not working :(

Here is the crontab:

```

MAILTO=xxx@yyy.co.za
0 3 * * * /usr/local/bin/USB-backup.sh | mail -r xxx@yyy.co.za -s "xxx Server Daily Backup" xxx@yyy.co.za

```

As you can see I have hit it with everything I've got, trying to ensure that somehow I will receive mail. Could anyone tell me what I am doing wrong here and why it refuses to send mail?

---

### Post by dcstar on 2008-02-13
> **Kasyx said:**
> Hi, not sure if this is the right place to put this, but it seems like a really basic question (I hope?)...
I have been trying to set up a crontab to get a backup script to run every night at 3am. It runs absolutely fine and has had no issues, the problem is that I have set it to mail me with the output of the script, and it is not working :(

Here is the crontab:

```

MAILTO=xxx@yyy.co.za
0 3 * * * /usr/local/bin/USB-backup.sh | mail -r xxx@yyy.co.za -s "xxx Server Daily Backup" xxx@yyy.co.za

```

As you can see I have hit it with everything I've got, trying to ensure that somehow I will receive mail. Could anyone tell me what I am doing wrong here and why it refuses to send mail?

Why do you assume that cron knows where the mail binary is?

---

### Post by Kasyx on 2008-02-13
> **dcstar said:**
> Why do you assume that cron knows where the mail binary is?

Because I am a noob? How would I set it up?

---

### Post by dcstar on 2008-02-13
> **Kasyx said:**
> Because I am a noob? How would I set it up?

Firstly, cron runs a specific task - not things that use shell commands like "|".

Create a separate script that has everything in it, and have cron run that.

If you are doing things for the first time, search out HOWTOs or other instructions, there are plenty about.

---

### Post by kpkeerthi on 2008-02-13
I think the OP is trying say that you should be using full path to mail in your crontab. 

Find the path to "mail' using
```

which mail

```

and add the full path to crontab entry

---

### Post by discodan on 2008-02-13
Hi Kasyx,

I'm having trouble with a similar issue as well.  I'm hoping that the answer to your question will help me too.

I'm trying to get mdadm to mail me at my ISP email address periodically.  After reading several posts and combing google I installed mailx and postfix per [http://ubuntuforums.org/showthread.php?t=608766](http://ubuntuforums.org/showthread.php?t=608766).

I did my best, but I'm still not getting the emails.  I'm not getting any errors either, so I have no clue where to start troubleshooting.

My current theory is that the SMTP server at my ISP requires authentication, so its not accepting the email.  But I'm not sure how to test for this or how to fix it.

Anyhow, maybe one of the gurus out there can help,

Good luck,

---

### Post by EnkiduinNZ on 2008-02-24
> **dcstar said:**
> Firstly, cron runs a specific task - not things that use shell commands like "|".

Create a separate script that has everything in it, and have cron run that.

If you are doing things for the first time, search out HOWTOs or other instructions, there are plenty about.

That is not correct. The command fed to cron can have 'pipe' symbols in it, and I often use this technique to direct cron emails to the correct recipient.

Cheers,

Cliff

---

