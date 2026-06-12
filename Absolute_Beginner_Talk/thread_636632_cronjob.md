---
title: "cronjob"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-12-10
Hi,
I have saved the following bash script in my home dir as background.sh
> #!/bin/bash
IMGS=`find /media/sda5/pers/pictures -name \*.jpg`
N=`echo $IMGS | wc -w`
((N=RANDOM%N))
gconftool-2 -t str -s /desktop/gnome/background/picture_filename "`echo $IMGS | cut -d ' ' -f $N`"

I wish to make a cronjob so that I am able to run the script every 10 minutes.
How should I edit my crontab file to achieve that?
When I run the script normally through the terminal it works fine.
Thanks for any help.

---

### Post by PointyWombat on 2007-12-10
In a terminal, run:

```
crontab -e
```

then add the following line:

```

# m h  dom mon dow   command
0,10,20,30,40,50 * * * * /path/to/your/script
```

then confirm it's working with:
```
crontab -l
```

---

### Post by gupta_sumesh63 on 2007-12-10
Thanks Pointy. Its working wonderfully. Thanks again.:guitar:

---

### Post by hyper_ch on 2007-12-10
I prefer not editing crontab directly but creating a cron text file and add this then to cron by issuing
```

crontab cron.txt

```

---

