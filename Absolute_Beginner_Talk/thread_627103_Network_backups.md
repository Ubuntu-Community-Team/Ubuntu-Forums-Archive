---
title: "Network backups"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-11-29
Hello all,
I'm looking to do backups in a particular way. I have three machines. The scenario is a bit more complex than what can be done with a single file copy, so I wanted to get some ideas from the forums. There are three boxes on the network that will need to be backed up to a Linksys network storage device. I can copy files to the device from any machine on the network because it uses windows shares (or appears to for the purposes of connecting to it from Linux and Windows). The boxes I will be backing up are described below:
1) Linux laptop running Fiesty. Periodically connected. Will need to manually backup configuration to a share set aside for it. Will also need to back up documents for two users to shares set up for the users. These shares will be used across multiple machines. It will also need to be able to manually synchronize some directories under the user directory with different shares on the network (MP3, for instance).
2) Windows laptop running Win2K. It's the wife's machine, so I haven't switched it over yet. She wants me to put Suse on it eventually (or maybe Kubuntu). Her personal files will need to be backed up (I can do this with a batch file, so no big deal there). I don't care much about the laptop configuration - I can get it running again pretty quickly if something breaks.
3) Linux desktop running Fiesty. This one is always on and I want it to synchronize the contents of some directories under a user directory at night (my MP3 directory, for instance). Other directories, such as configuration and individual user directories, will need to be able to be backed up manually.

I'd like to have separate shares for:
1) Individual users to back up their stuff
2) Shared media files (these are big files and there are a lot of them, so I want to schedule the backups for off-peak hours)
3) Backups of configuration for each machine

What tool would you use to do this? I was thinking maybe unison for the synchronizations, and simple backup for the configuration backups. Any thoughts?

Thanks,
Will

---

### Post by sixsixone on 2007-12-01
How about rsync? Run it as a cron job on your regularly connected machines every hour or so to back up your home directory, and just run a script on your laptop when it's connected.

Really simple, reasonably elegant. It plays well with low-bandwitdh situations too- my old laptop used to be on the road a lot and my backup server was a network storage device with its own dyndns name sitting behind my router at home.

that setup lets me have near-real time incremental backups to the device over ssh, even when I'm using a cellphone for internet access. I use the same setup on my mac. Not sure how you'd do it in Windows though; the rsync client requires cygwin if memory serves me well...

---

