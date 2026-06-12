---
title: "GUI problems?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by kanly6486 on 2006-12-15
after i leave my system up for a bit it gives me 

Could not launch application

Details: Failed to execute child process "gnome-terminal" (Input/output error)

error, this is when i try to start up most any application, from the terminal to firefox, if i restart it will work agian but after a hour or 2 if i come back to the computer its done it agian. Even more some times the gui will disapear after this has happened. any help? im thinking its  a X problem but idk =/ i dont want to ruin anything

---

### Post by Ecthelion on 2006-12-15
Have you looked in your system logs for an error?
If you use Edgy, then the system logs are really easy to use!
Look there and say which error you have
(I'm afraid the system log isn't that good in dapper, so there you might have to look in the logs using the good 'old teksteditor)

---

### Post by kanly6486 on 2006-12-15
how do i know if im using edgy? i never heard of it before =/ and also while were at it the log files? where would i find those?

---

### Post by Ecthelion on 2006-12-16
If you click on System > About Ubuntu , the first line of text, under the table of content, should be: 
"Thank you for your interest in Ubuntu 6.10 -the Edgy Eft - released in ..."
(or something like that, I'm translating to English what it says with me)

If your not using Edgy Eft, then it should be about dapper drake or breezy badger ...


As I said, I is easy (if you do use Edgy Eft) to check your system logs.
Click System > Administration > System logs
And then search for an error
Since date ans time are displayed, the easiest is to check if there are errors at the last time/date you start having these error reports.

---

### Post by kanly6486 on 2006-12-16
its dapper drake, i checked the system logs like you said to do for edgy but nothing shows in there

---

### Post by Ecthelion on 2006-12-16
> its dapper drake, i checked the system logs like you said to do for edgy but nothing shows in there

That's normal then. In dapper drake the system logs aren't developed as good as in Edgy Eft.

Your logs can be found in /var/log/ .
The only way to see them is then to go with nautilus to /var/log/ and clicking on the logs and looking with the teksteditor for an error.

The logs in /var/log that you have to look to are:
auth.log
daemon.log
kern.log
messages
syslog
user.log
Xorg.0.log

Just use "find" to go to a date/time you know the error started to appear.
If you see no error a that time (+-2 min) just go to the next log.

---

### Post by kanly6486 on 2006-12-16
ok im actually upgraded to edgy now, i looked in there, and i have the logs open and the error is happening agian, when i click on anything and it fails to start and gives me that error nothing is recorded in the error logs that i can see. Im thinking it might be my X config since it seems to be GUI related?

---

### Post by Ecthelion on 2006-12-17
> , when i click on anything and it fails to start and gives me that error nothing is recorded in the error logs that i can see
Do you mean there is nothing in your logs? 
Or do you mean you don't find an error in it.

> Im thinking it might be my X config since it seems to be GUI related?

If you think it is your x, then you can try to reconfigure it...

First backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back
```
If you mess things up you can go back to your old xorg.conf with this:
```
sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf
```

Stop your current xserver
If you use gnome by default
```
sudo /etc/init.d/gdm stop
```
If you use kde by default
```
sudo /etc/init.d/kdm stop
```

Then reconfigure your xserver:
```
sudo dpkg-reconfigure xserver-xorg
```
Fill in what you know, if your not sure, leave the default.

After that restart your xserver:
If you use gnome by default
```
sudo /etc/init.d/gdm start
```
If you use kdm by default
```
sudo /etc/init.d/kde start
```

---

