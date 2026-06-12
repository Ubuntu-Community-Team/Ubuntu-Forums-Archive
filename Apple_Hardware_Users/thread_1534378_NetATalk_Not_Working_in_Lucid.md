---
title: "NetATalk Not Working in Lucid"
date: 2010-07-19
forum: Apple Hardware Users
---

### Post by jrolland on 2010-07-19
Hello, all!

I have been using netatalk to use my old LaserWriter PS 4/600 with Kubuntu.

Everything was fine until I upgraded to Lucid.

Now, when I go to restart netatalk, I get

```

user@machine:~$ sudo /etc/init.d/netatalk restart
Restarting Netatalk Daemons (this will take a while)Stopping Netatalk Daemons: afpd cnid_metad papd timelord atalkd.
..Starting Netatalk services (this will take a while):  afpd.
done.
user@machine:~$

```

and the process takes about 2 seconds, instead of the ~5 minutes it took under Karmic.

Finally, when I go to do an nbplkup, I get nothing:

```

user@machine:~$ nbplkup
nbp_lookup: Cannot assign requested address
user@machine:~$ 

```

I tried uninstalling and reinstalling netatalk, but the same thing happens. Can anyone help?

---

### Post by radag87 on 2010-07-19
Hello jrolland

I had a similar issue with regular Ubuntu 10.04.  I got instructions on another Mac related issue that talked about /etc/default/netatalk.

Change the /etc/default/netatalk file from 
```

# Set which daemons to run (papd is dependent upon atalkd):
ATALKD_RUN=no
PAPD_RUN=no

```to 

```

# Set which daemons to run (papd is dependent upon atalkd):
ATALKD_RUN=yes
PAPD_RUN=yes

```Then execute 

```

sudo /etc/init.d/netatalk restart

```See if that solves your issue.  If it does not, then you have exhausted the limit of my knowledge on netatalk and will have to seek help from a different person.

Regards

---

### Post by jrolland on 2010-07-28
radag87,

That worked! Thank you so much!

(Sorry I didn't reply earlier. I thought I had set my preferences to have me emailed when there was a reply to this topic, but I evidently didn't have my preferences set that way.)

I will mark this thread as "Solved".

---

### Post by Suchthefool on 2011-03-19
This is exactly what I need to do as I'm having the same problems but I am pretty inexperianced with this. How do I do this part:

> **radag87 said:**
> 
Change the /etc/default/netatalk file from 
```

# Set which daemons to run (papd is dependent upon atalkd):
ATALKD_RUN=no
PAPD_RUN=no

```to 

```

# Set which daemons to run (papd is dependent upon atalkd):
ATALKD_RUN=yes
PAPD_RUN=yes

```

Any help will be much appreicated!

---

### Post by epud on 2012-10-30
```
sudo gedit /etc/default/netatalk
```

Should allow you to edit the file.

---

