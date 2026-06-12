---
title: "Playing media and fstab entries"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by OU812 on 2006-07-20
Couldn't quite think of the most appropriate title for this. I have two dvd drives. In fstab I have

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

So of course I want to play dvds. So I followed the instructions on

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

After some trial and error, I was able to play dvds by editing  gxine and mplayer preferences from /dev/cdrom0 to /dev/hdc. So I have two questions (one related and one a bit off-topic):

1. What is the best way to handle this situation? Would it be better to edit fstab? If so, what should it look like? Or should I just edit a media player's prefs if I run into trouble? (I notice that when most linux flavors create fstab, hdc is usually cdrom and dvd is usually hdd. So most media players seem to expect this. Did I just answer my own question?)
2. When I put a dvd totem automatically launches and tries to play it. This brings up two problems: I don't like apps automatically launching themselves. How do I turn this off? Also, in Totem, I can hear sound, but no video. I looked at the preferences, but couldn't see (haha) a way to change anything.

Thanks.

john

---

### Post by reacocard on 2006-07-20
you can fix the auto-launch in System -> Preferences -> Removable Drives and Media. no idea about the rest though.

---

### Post by OU812 on 2006-07-20
Thanks. It's a start. ;) 

john

---

### Post by OU812 on 2006-07-22
Since in most apps

/dev/hdc = /dev/cdrom
/dev/hdd = /dev/hdd

I edited /etc/fstab with the stuff on the right. This way I don't have to change the preferences of every single multimedia app. I also don't have to do any other work - just this one edit.

One question though. At first install, the only fstab entry was

/dev/cdrom /media/cdrom0

but in /media there were two folders: cdrom and cdrom0. What is cdrom? Why is is there? I don't get it. I also notice an arrow on it. What is the significance of that?

Thanks.

john

---

