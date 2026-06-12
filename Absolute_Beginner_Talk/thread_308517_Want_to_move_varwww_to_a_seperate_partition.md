---
title: "Want to move var/www to a seperate partition"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-11-28
I have successfully move my home folder to a new partition and would now like to move /var/www to the same partition.

This will enable me to reload the system at any point and still have my web files etc untouched.


Using the same instructions as for moving my /home folder:

```
sudo mkdir /old
sudo mount -t ext3 /dev/sda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/sda5 /new
sudo mkdir /new/www
cd /old/var/www
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/www/
sudo mv /old/var/www /old/var/www_backup
sudo mkdir /old/var/www
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab
```

adding this to fstab:

```
/dev/sda3/www	/var/www	ext3	nodev,nosuid 0 2
```


I think I got the above ok, but not exactly sure.



Synopsis:

New folder on sda3:  /www

All contents of /var/www copied to: sda3/www

Folder sda3/www mounted as: /var/www



I presume that there is no need to modify anything else as the system should see no difference from the original /var/www and the newly mounted /var/www/ (/sda3/www).


Any help would be appreciated. :)

---

### Post by Bachstelze on 2006-11-28
If the partition is going to be mounted on /var/www, you must put all your files at the root of the partition (that is, in /new, not in /new/www)

And of course, you must mount /dev/sda3, /dev/sda3/www makes no sense.

---

### Post by Scorpuk on 2006-11-28
ahh okies.


Was originally wanting to mount a fodler on the sda3 to var/www, but I guess this not possible.


I will resize the partition on sda3 to give me a new partition for /var/www.

Would 5Gb be sufficient?  sda3 is 250Gb approx.

---

### Post by Bachstelze on 2006-11-28
Maybe it would be a better idea to move the root of your web server to /mnt/sda3/www (or wherever you mounted your sda3 partition to).

You can do so by editing /etc/apache2/sites-enabled/default

---

### Post by timcredible on 2006-11-28
it'll be much simpler to just move the /var/www files to your /home partition using grsync or tar, then just create a symlink that points /var/www to /home/var/www.  if you're not familiar with rsync, grsync, or tar, do some research on them, because if you change file permissions, it'll mess up being able to use the files correctly.

---

### Post by Bachstelze on 2006-11-28
It will be simpler indeed but security-wise, not a good thing to do...

---

