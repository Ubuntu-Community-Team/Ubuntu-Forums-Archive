---
title: "Huge increase in disk usage after splitting mp3"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-12-05
Hi everyone,
I just can't seem to figure that one out!

I used Audacity to split a 105MB.mp3 so as to be able to upload it for a friend in India to pick it up. The file is on my /hda3 FAT 32 partition.

All went fine in Audacity; I selected the part I wanted and proceeded to "Export the selection as mp3".

I then checked my disk space and noticed it went from 38% used to 71% following splitting the file.mp3.
What's the command line (or the way) to find out where large files are stored.
I want to be able to delete them.
Any help appreciated.

---

### Post by zgornel on 2006-12-05
> **xyz said:**
> Hi everyone,
I just can't seem to figure that one out!

I used Audacity to split a 105MB.mp3 so as to be able to upload it for a friend in India to pick it up. The file is on my /hda3 FAT 32 partition.

All went fine in Audacity; I selected the part I wanted and proceeded to "Export the selection as mp3".

I then checked my disk space and noticed it went from 38% used to 71% following splitting the file.mp3.
What's the command line (or the way) to find out where large files are stored.
I want to be able to delete them.
Any help appreciated.
Check the Audacity temp directory: [http://www.die.net/doc/linux/man/man1/audacity.1.html](http://www.die.net/doc/linux/man/man1/audacity.1.html) . The fs usage increased for the root partition ?

---

### Post by xyz on 2006-12-05
Root's only 2.8 MB
Nothing in /tmp/audacity1.2-user
> root@luser:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.7G  6.5G  2.7G  71% /
varrun                244M   92K  244M   1% /var/run
varlock               244M  4.0K  244M   1% /var/lock
udev                  244M  136K  244M   1% /dev
devshm                244M     0  244M   0% /dev/shm
lrm                   244M   18M  226M   8% /lib/modules/2.6.15-27-686/volatile
/dev/hda1              15G  6.7G  8.1G  46% /media/hda1
/dev/hda3              49G  1.3G   48G   3% /media/hda3

I know there's a command line to see where there are incredibly large files that should not be there but I can't remember it.
Thx for your time.

---

### Post by xyz on 2006-12-06
OK I found the command line I was looking for to get info about where all the space is going to:
```
cd /
sudo du -hc --max-depth=1
```
and that revealed that I've got:
> 3.0G    ./.glameswap

So no wonder and yes I'd forgotten I'd tried Glame to split my file.mp3!
Itried the rm command to no avail. Any thought?
```
 whereis ./.glameswap

```
the output is:
> : /usr/src/rpm/. /bin/. /usr/bin/. /sbin/. /usr/sbin/. /etc/. /etc/.java /lib/. /usr/lib/. /usr/games/. /usr/X11R6/bin/. /usr/bin/X11/. /usr/local/bin/. /usr/local/sbin/. /usr/local/lib/. /usr/local/games/. /usr/include/. /usr/local/. /usr/share/. /usr/man/man1/. /usr/man/man5/. /usr/share/man/man8/. /usr/share/man/pl/. /usr/share/man/man1/. /usr/share/man/man7/. /usr/share/man/fr/. /usr/share/man/pt_BR/. /usr/share/man/es/. /usr/share/man/ja/. /usr/share/man/sv/. /usr/share/man/man5/. /usr/share/man/ru/. /usr/share/man/de/. /usr/share/man/man3/. /usr/share/man/hu/. /usr/share/man/id/. /usr/share/man/it/. /usr/share/man/ko/. /usr/share/man/cs/. /usr/share/man/sk/. /usr/share/man/fi/. /usr/share/man/gl/. /usr/share/man/man4/. /usr/share/man/man6/. /usr/share/man/man2/. /usr/share/man/man9/. /usr/share/man/tr/. /usr/share/man/zh_CN/. /usr/share/man/zh_TW/.

I had run:
```
sudo aptitude remove glame
```
and that was fine...but what am I missing about removing ./.glameswap?

---

### Post by xyz on 2006-12-06
Anyone?
Thx

---

### Post by Biggus on 2006-12-06
Hi dude, I'm not an expert by any means (third week of Linux) but I've found from messing around that there are a huge number of 'hidden' files in my home directory, all of which start with a period.

Maybe you too have a folder called .glameswap in your home folder?

---

### Post by xyz on 2006-12-06
> **Biggus said:**
> Hi dude, I'm not an expert by any means (third week of Linux) but I've found from messing around that there are a huge number of 'hidden' files in my home directory, all of which start with a period.

Maybe you too have a folder called .glameswap in your home folder?
Hey Biggus...RIGHT ON! Thanks a lot!
I must be going blind or TOO complicated with this!

---

