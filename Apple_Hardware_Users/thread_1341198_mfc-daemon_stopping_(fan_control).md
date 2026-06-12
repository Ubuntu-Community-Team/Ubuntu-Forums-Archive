---
title: "mfc-daemon stopping (fan control)"
date: 2009-11-29
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2009-11-29
It happens to me that sometime mfc-daemon stops to update the speed of fans. Is this happening to others? Any clue?
Today my cpus went up to 95°C...

For the moment I put a restart every 4 minutes in crontab:

*/4 *   * * *   root    (pkill mfc-daemon ; sleep 0.5; rm -f /var/run/mfc-daemon.pid ; /usr/sbin/mfc-daemon)


The rm of the pid file is needed because it seems that sometime mfc-damon refuses to start because of the presence of that file.

Also sometime I notice mfc-daemon does not update both the fans but just one.

Any suggestion?

---

### Post by luigi.viggiano on 2009-11-30
I checked the source code of mfc-daemon and I see that it is doing complex logics when the temp goes up and down, so it may be possible that the temperature raises by 2 degree, then lower by 1, then raises again by 2 and lower by 1 and continue this way... without mfc-daemon never to change the temperature. I know this is improbable, but still possible, and I prefer a simpler logic, so I made my changes. With this logic I see high temperature sometime, with mfc-daemon not updating the fan speed.

Now with my changes mfc-daemon is sensible to temp change of ±2°C or more
I changed the fan speed formula to (((t) - 40) * 200) (a little bit colder)
And I lowered delay time between checks from 5 seconds to 4.

Temp changes are more frequent now, and they better reflect cpu temperature, on my system.

To apply the patch, copy the file on the mfc-daemon directory then 
$ patch < mfc-daemon-patch-luigi.patch.txt

(I had to add .txt extension otherwise this forum does not allow me to upload it)

---

### Post by luigi.viggiano on 2009-12-02
The patch is now included in mfc-daemon, downloading lastest sources using git you don't need anymore to apply it.

---

