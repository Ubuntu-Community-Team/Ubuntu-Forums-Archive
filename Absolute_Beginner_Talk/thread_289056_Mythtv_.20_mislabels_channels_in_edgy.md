---
title: "Mythtv .20 mislabels channels in edgy"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by smihlon on 2006-10-30
Ok, I got everything up and running using the ubuntu documentation guides, but a few of my early channels are mislabeled, which messes up my upcoming programming.  Everything seems to be offset by 2 channels.  For example, channel 2 says home improvement but that is actually playing on channel four.  After the getting through lirc,ivtv,game emulators, and restoring my recording data from .19, I don't want to be beat by this simple problem!  Any  help would be greatly appreciated.  

Here's the hardware I had to set up if anyone has any specific questions to get their's running:
Hauppauge pvr-150 mce edition in ivtv
mceusb2 remote in lirc
nvideo geforce 6150
Asus pundit barebones case
AMD athlon x64 3000+

---

### Post by superm1 on 2006-10-30
Backup your mysql database.

Stop mythbackend.
```
sudo /etc/init.d/mythtv-backend stop
```
Open up mythtv-setup
```
sudo mythtv-setup
```Choose the channel editor.

Delete all your channels.

Refill the database
```
sudo /etc/cron.daily/mythtv-backend
```This won't delete any scheduled recordings, or recording schedules for that matter -  just the guide data and the information about what channel is what.

---

### Post by smihlon on 2006-10-30
thanks a lot, it worked.

---

