---
title: "sbackup - won't create files or save prefs"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-08-19
I installed sbackup using synaptic, because as I am configuring a new install of Ubuntu I am worried that I am going to make major changes that are going to cause major problems at one point or another (as I am a recent convert from Windows and still don't know what I'm doing, really). So, I go to the System menu, hit Administration, then Simple Backup Config.

I set it up to make regular automatic backups, but also save settings and hit backup now. I have no indication that it did anything. So I go into Simple Backup Restore. At first it said that it couldn't find the folder, nor could it find backup files in that folder. So I did *gksudo nautilus* and created the folder where it said it should go (/var/backup although there already was /var/backup**s**). 

So anyway, it didn't give me the error saying that the folder was missing, but it still said there were no backups. So using Config, I created the backup again. In Restore, it still said there were no backups!

The odd thing that I noticed was that the settings in Config were not saved, despite me hitting the button. Still, I cannot make backups. What gives?

Thanks for any help!!

---

### Post by mikeyphi on 2007-08-19
Try these actions:
First make sure that your system is up to date
Then use Synaptic to Reinstall sbackup

sounds like a program problem with it not saving your settings - I use it for a daily backup without any problems, only difference is I save to a folder on a separate disc.

---

