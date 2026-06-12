---
title: "Getting the Clock chime every hour?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by FireFusion on 2006-09-08
Is the there any way to get the Ubuntu to alert me every hour? It's good to take a break from the PC to strech and move about.

---

### Post by keithclark on 2008-06-22
Did you ever get an answer to this question?  I'm looking to do the same thing.

Keith

---

### Post by prshah on 2008-06-23
> **FireFusion said:**
> Is the there any way to get the Ubuntu to alert me every hour? It's good to take a break from the PC to strech and move about.

> **keithclark said:**
> Did you ever get an answer to this question?  I'm looking to do the same thing.


I have setup a cron job that will announce the time every hour and half-hour. You can do the same:```

$ crontab -l
# m h  dom mon dow   command
0 * * * * /home/user/telltime.sh
30 * * * * ./telltime.sh
$ cat telltime.sh
espeak -s 120 "The time is `date +%I:%M%p`"

```

You can set up the crontab as above with the command ```
crontab -e
``` The first column in the crontable indicates minute, the second hour, the third the day of month, etc. So the above table indicates that the "telltime.sh" script should be run every 0th minute and every 30th minute of every day, every month, on all days.

telltime.sh uses espeak to say the time. If you don't already have espeak, you can install it with ```
sudo apt-get install espeak
``` If you want to play a chime or so, use the "play" command (part of the sox library), eg```
play somefile.wav
```

Don't forget to give the script mentioned in the crontab execute permissions```
chmod +x telltime.sh
```

---

### Post by phrawzty on 2008-06-23
> **FireFusion said:**
> Is the there any way to get the Ubuntu to alert me every hour? It's good to take a break from the PC to strech and move about.

Ubuntu has a built-in feature for this - it's called "Typing Break", and it can be configured via Keyboard Preferences.

System --> Preferences --> Keyboard ^ Typing Break

---

