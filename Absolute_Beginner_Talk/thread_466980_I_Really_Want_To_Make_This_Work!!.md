---
title: "I Really Want To Make This Work!!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by dyno_eq on 2007-06-07
Hi,

just installed feisty all went well installed perfectly on my vaio no problems in the slightest except..... now when i use adept for updates and so forth when i install the updates it asks me to put the feisty dvd back in the drive then press enter...  its now not recognising the feisty dvd in the drive and will not let me do the updates.... however i can explore the dvd normally.....this was working fine untill i installed kubuntu??

any help would be very much appreciated

thanks

---

### Post by Bachstelze on 2007-06-07
```
sudo nano -w /etc/apt/sources.list
```

Delete or comment out the lines about the CD, and run

```
sudo apt-get update
```

---

### Post by BHelts on 2007-06-07
```
gksudo gedit /etc/apt/sources.list
``` in terminal
and comment out any references to your DVD Drive (with a #)

aaahhhhh...  kubuntu, hymn to life is right again

---

### Post by dyno_eq on 2007-06-07
thanks,
that was a quick response will give it a go tonight

---

