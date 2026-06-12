---
title: "Cron Job Help"
date: 2011-06-06
forum: Any Other OS
---

### Post by mbudden on 2011-06-06
So I've been messing with this for an hour and it's really starting to upset me because it's not working. I've Googled and Googled to my wits end and I still can't find an answer.

All I want to do is have a simple script run every hour via Cron but that seems not to work.

```
crontab -e
```

I edit the cron job that I want.

```
0 * * * * bash /home/mbudden/Minecraft/backup.sh
```

Save it. Nothing happens. So I troubleshoot. I try it for every minute.

```
* * * * * bash /home/mbudden/Minecraft/backup.sh
```

Nothing happens. 

I have tried in sudo
```
sudo crontab -e
```

and it shows up via 
```
sudo crontab -l
```

But nothing happens after a minute. 

What is up? I don't get it.
My backup script works when running it via terminal, but cron isn't working. Even restarted cron via
```
service cron restart
```

Some help?
OS: Linux Mint 10 LXDE

---

### Post by DaithiF on 2011-06-06
Hi,
2 possibilities ... 
1. problem with cron set up means that your jobs don't get executed, or
2. your job is being executed, but a problem with the script causes it to fail before it does anything useful / noticeable.

amend the cron entry to capture stdout and stderr from the job to a log file somewhere, e.g.:

* * * * * bash /home/mbudden/Minecraft/backup.sh >> /home/mbudden/minecraft.log 2>&1


then see what turns up in the log file.

---

### Post by mbudden on 2011-06-06
For some reason, when I added the command you posted. It made a backup and a log. How strange.

```
Starting world backup...
	zip warning: name not matched: plugins

zip error: Nothing to do! (try: zip -r /home/mbudden/Minecraft/backups/2011-06-06-18-38-01.zip . -i plugins)
  adding: home/mbudden/Minecraft/world/ (stored 0%)
  adding: home/mbudden/Minecraft/world/session.lock (stored 0%)
  adding: home/mbudden/Minecraft/world/level.dat_old (stored 0%)
  adding: home/mbudden/Minecraft/world/region/ (stored 0%)
  adding: home/mbudden/Minecraft/world/region/r.0.0.mcr (deflated 25%)
  adding: home/mbudden/Minecraft/world/region/r.-2.-3.mcr (deflated 87%)
  adding: home/mbudden/Minecraft/world/region/r.0.-1.mcr (deflated 26%)
  adding: home/mbudden/Minecraft/world/region/r.-2.-4.mcr (deflated 89%)
  adding: home/mbudden/Minecraft/world/region/r.-1.-2.mcr (deflated 100%)
  adding: home/mbudden/Minecraft/world/region/r.-2.-1.mcr (deflated 100%)
  adding: home/mbudden/Minecraft/world/region/r.-2.0.mcr (deflated 100%)
  adding: home/mbudden/Minecraft/world/region/r.-1.0.mcr (deflated 30%)
  adding: home/mbudden/Minecraft/world/region/r.-1.-1.mcr (deflated 27%)
  adding: home/mbudden/Minecraft/world/players/ (stored 0%)
  adding: home/mbudden/Minecraft/world/players/HeWhoDared.dat (stored 0%)
  adding: home/mbudden/Minecraft/world/players/mbudden.dat (stored 0%)
  adding: home/mbudden/Minecraft/world/players/Versatility.dat (stored 0%)
  adding: home/mbudden/Minecraft/world/players/jbudden.dat (stored 0%)
  adding: home/mbudden/Minecraft/world/level.dat (stored 0%)
  adding: home/mbudden/Minecraft/world/data/ (stored 0%)
  adding: home/mbudden/Minecraft/world/data/idcounts.dat (stored 0%)
  adding: home/mbudden/Minecraft/world/data/map_0.dat (stored 0%)
Saving '/home/mbudden/Minecraft/world' to '/home/mbudden/Minecraft/backups/2011-06-06-18-38-01.zip'
Backup complete.
```

---

### Post by bleutyler on 2011-06-06
The crontab very likely does not have your environment setup, so use the explicit path for commands.
Try
/bin/bash instead of just bash.

---

### Post by DaithiF on 2011-06-07
> **mbudden said:**
> For some reason, when I added the command you posted. It made a backup and a log. How strange.

that will be issue described in my post here [http://ubuntuforums.org/showthread.php?t=825242](http://ubuntuforums.org/showthread.php?t=825242) then

---

