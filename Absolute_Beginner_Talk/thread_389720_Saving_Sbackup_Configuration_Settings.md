---
title: "Saving Sbackup Configuration Settings"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by JonBL on 2007-03-21
I'm a new user to Ubuntu 6.10, and I'm attempting to configure Sbackup to back up to an attached external disk drive. I've used Synaptic Package Manager to download and install Sbackup, and I see entries "Simple Backup Config" and "Simple Backup Restore" under System -> Administration. 

When I click on "Simple Backup Config", I'm prompted for a password - I specify the password of the one account I created when I installed Ubuntu. The "Backup Properties" dialog is then displayed. 

Saving changes to the configuration does not report any errors, and the timestamp on /etc/sbackup.conf is updated to the time of the save. But when I exit config, and re-enter it, configuration settings remain unchanged. The contents of /etc/sbackup.conf also remain unchanged. /etc/sbackup.conf is owned by root.

I can't tell if I've got a permissions problem, a Sbackup problem, or I've misunderstood how I should be running "Simple Backup Config" from Ubuntu. Can anyone assist me with this? :confused: 

Regards,
  Jon

---

### Post by Kobalt on 2007-03-21
I don't understand your question.
sBackup is an administrative tool and it's normal in Ubuntu to place under root privileges administrative applications...

---

### Post by louieb on 2007-04-05
I used sbackup for the first time last night. The only thing I changed from the default was the target (like you I save it to my external disk drive). You post made me curious so  I look in my /etc/sbackup.conf and the file has the target change I made. 
I wonder if you pressed save before you made your configuration changes?

---

### Post by arpad on 2007-05-09
I'm having problems getting sbackup to save settings as well and I sure have clicked "Save". 

Sometimes I get an alert box that tells me the settings have been saved which is partially true. Other times no alert box and no saved settings.

When I do have my settings saved the "Time" tab setting never gets saved. Backup frequency always returns to "never" and the backups don't happen. 

I'm running sbackup from the command line right now and it seems to be backing up my data but sbackup config program is what's causing me conniptions.

---

