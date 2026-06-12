---
title: "Cron Help"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by justin597 on 2007-04-12
I wanted a way to track my cable modems ip address so i can access my system remotely.

I created a php file on my remotely hosted website which displays the ip address of whomever is accessing the site.

I created a script which downloads the file and repost to my website as a text file, I added a time stamp for testing purposes.  This is what it displays:

```
10.0.0.0
Thursday 12th of April 2007 11:01:34 AM
```

I can run the file manually, called postIP, and it works just like I need it to.

I'm trying to create a cron job to run every hour.  Here is my current crontab:
(I have it running every 5 minutes so I can see if it's working, then I'll switch it to run hourly.)

```
*/5 * * * * /home/justin/postIP >/dev/null 2>&1
```

As far I can tell, the cron job isn't running, because the file on my site doesn't update.

Any help will be appreciated.  Thank you.

---

### Post by spin2cool on 2007-04-12
Permissions error?  chmod the script to 777 and see what happens. 

Also, you can use the no-ip service (or something similar) to do this for you.  Sign up for your preferred address atwww.no-ip.com and then instlal the no-ip package.

---

### Post by justin597 on 2007-04-12
i have it chmodded to 777 already.  is there a command to execute cron jobs manually to test them?

---

### Post by justin597 on 2007-04-12
i fixed it.  i had run the script as root at one point and created the local file. when i ran it as my user, it couldn't overwrite the local file, thus the remote file never changed.  i deleted the local file, ran the script and everything works.

thanks for your time.

---

