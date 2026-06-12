---
title: "echo startup script"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by aaronbridge on 2007-11-18
I have added /usr/local/sbin/pure-ftpd -A -B -E & to the /etc/rc.local file and it is working great.  I would like to add an echo (I hope that is what it is called) to the file as well that would say something like "Starting Pure-ftpd..." when the Ubuntu server is starting.

---

### Post by terdon on 2007-11-18
Just add > echo "Whatever you want it to say"  to your rc.local file.

---

### Post by mdpalow on 2007-11-18
+1 for answer above.

However, it sounds like you want to be able to see the message as well, so you might want to try:

echo -n "Whatever you want to say:

Press Enter to Continue: "

*** or you could do this: ***

echo "Whatever you want to say:"
sleep 5

The first option will make it so the message is displayed and you have to press enter to continue.

Second option won't require you to press enter, but it will show the message for 5 seconds before moving on....

Good luck...

---

### Post by LinuxGuy1234 on 2007-11-18
> **aaronbridge said:**
> I have added /usr/local/sbin/pure-ftpd -A -B -E & to the /etc/rc.local file and it is working great.  I would like to add an echo (I hope that is what it is called) to the file as well that would say something like "Starting Pure-ftpd..." when the Ubuntu server is starting.

This code will help out: (if you have the Ubuntu Server edition please comment out the usplash_write lines using #):
```
echo "Starting Pure-FTPD..."
          # Comment out if you use the Ubuntu Server edition by using #
          usplash_write "Starting FTP server daemon: pure-ftpd"
          # Please uncomment by removing # if a start line for Pure-FTPD is not there (if it's in a daemon section, there's no need)
          # /etc/init.d/pureftpd start

```

---

### Post by aaronbridge on 2007-11-18
I went with mdpalow's second option and it worked perfectly.

Thanks.

---

