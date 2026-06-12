---
title: "cronjob help"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2008-02-18
I have used the following bit of code to set my pc to automaticatty turn off at 11pm each evening:

00 23 * * * /sbin/shutdown -h now

I would like to transfer some files from a windows pc to it using WinSCP  which may mean that it needs to be on over night and I don't want the pc shutting down at 11pm. Can anyone tell me where this would be stored and how I either find the directory to delete it or how to stop it running. Oh and I  would like to enable it after the files have transfered so that it gets back to normal turning off at 11pm.

cheers

---

### Post by ruy_lopez on 2008-02-18
Try:

```
crontab -e
```

if you see the entry, comment it out with '#'. If you don't see it, try this:

```
sudo -s
<enter password>
crontab -e

```

if you still don't see the entry, look in "/etc/cron.daily/". You'll probably have to go through the files one by one, until you find the entry which shuts down your computer.

---

### Post by fatality_uk on 2008-02-18
Your "Cron" jobs are stored in 

**/etc/cron.d**

Open a terminal and type **sudo gedit /etc/cron.d/anacron** then edit your entry there

---

### Post by fast eddie on 2008-02-18
Hmmm, cant see the approprite cronjob in "/etc/cron.daily/"

and

sudo gedit /etc/cron.d/anacron gives an error "sudo: gedit: command not found"

I must be doing something wrong but I cant see what :confused:

---

### Post by ruy_lopez on 2008-02-18
```
which gedit
```

Remember the path to gedit. Then:

```
sudo /path/to/gedit /etc/cron.d/anacron
```

I take it 'crontab -e' produced nothing?

You should also check "/etc/crontab" just in case you added it there.

---

