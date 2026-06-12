---
title: "script file"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-09-05
I wrote recently a script file to clean my .thumbnails folder.  Is there a way to automatically make this script run every 30 minutes or each hour.  I noticed this directory gets loaded with junk thumbs every time I edit pictures from my digital camera.  I am using gthumbs to view the downloaded pictures.  If anyone has an easier way to keep this directory from getting so many files in it I would appreciate it.

Donald

---

### Post by kidders on 2006-09-06
Looks like you've done the hard part already :-) The only thing you're missing is to throw your script into **/etc/cron.hourly** There are a few other cron directories, if that frequency doesn't suit you ... and then of course, there's **/etc/crontab**, which offers waaay more flexibility.

I'm pretty sure you can turn off thumbnail caching in your apps if you want to, but it's nice not to slow down your PC by constantly making it regenerate eye candy.

---

### Post by alienexplorers on 2006-09-06
How would I go about adding this script to the cron file.  I have never worked with cron before.  A short description would really help me out alot.  I am really new at this stuff.

---

### Post by kidders on 2006-09-06
No worries :-)

All you need to do (as far as I understand) is copy your script into one of the cron directories. Assuming the cron daemon has permission to execute it, the thing should just work.

I say "as far as I understand" because I like to use /etc/crontab most of the time ... it allows for far more flexibility in terms of when and how something executes, but is much more complicated to use.

The other possibly confusing thing I mentioned was to do with permissions. Take a peek at the contents of /etc/crontab and notice that one of the columns in it reads "root root root root...". This means that the hourly, daily, etc. scripts run with root privileges. With that in mind, the following is EXTREMELY important:

After you have copied your script into, say, /etc/cron.daily, you must do the following. Let's say you called it /etc/cron.daily/thumbkiller ...

```

sudo chown root:root /etc/cron.daily/thumbkiller
sudo chmod 750 /etc/cron.daily/thumbkiller

```

This ensures that no-one but root can access the script. The reason for this is that, since cron runs its scripts as root, anything that happens to be in them will be executed, regardless of the consequences.

If someone were to maliciously tweak such a script, they could erase your hard disk with a single command ... and you'd never see it coming! Also, it prevents you from making careless changes to it in the future, by requiring you to use "sudo" to modify it. As I'm sure you've noticed by now, typing "sudo" means "whoa now ... think before you type!".

---

### Post by alienexplorers on 2006-09-06
Thanks for the help and information.

Donald

---

### Post by hw-tph on 2006-09-06
If you are cleaning out files in your own home directory there is no reason whatsoever to run the script as root! Run it as yourself. To edit your own crontab file, simply type **crontab -e**. When done, save and exit.

If your file is called "myscript" and located in ~/bin/ and your user name is alienexplorers, this is how it could look:
```
40 * * * * /home/alienexplorers/bin/myscript
```
You may need to set the $PATH in the script as cron by default runs with a limited $PATH.


Håkan

---

