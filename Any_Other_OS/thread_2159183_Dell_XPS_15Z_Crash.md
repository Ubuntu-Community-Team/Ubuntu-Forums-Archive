---
title: "Dell XPS 15Z Crash"
date: 2013-07-02
forum: Any Other OS
---

### Post by Shadius on 2013-07-02
Hello everyone,

I have a Dell XPS 15Z with Winodws 7 Home Premium installed.  However, it seems to have crashed after a blue screen and now when I turn it on it just gives me a black screen with a blinking underscore. I've tried to enter Safe Mode by tapping on F8, but it doesn't work.  It used to start up fine before.  The problem started when I installed some Windows Updates. Now I don't know what to do. I used Ubuntu's LiveCD to run the Disk Utility and check the hard disk drive and it told me that the drive was bad.  I suspect that the hard disk drive has crashed.  How can I be sure though?  Please help me in solving this! Much thanks in advance!

---

### Post by mips on 2013-07-02
Post the output of smartctl or gsmartcontrol here. If they are not on the livecd you can install them, the first is a cli util and the second gui.

---

### Post by Shadius on 2013-07-05
ubuntu@ubuntu:~$ smartctl
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

ERROR: smartctl requires a device name as the final command-line argument.


Use smartctl -h to get a usage summary

ubuntu@ubuntu:~$

---

### Post by mips on 2013-07-07
I was hoping you would use some initiative on how to use the command.

[https://wiki.archlinux.org/index.php/S.M.A.R.T.](https://wiki.archlinux.org/index.php/S.M.A.R.T.)

---

### Post by Shadius on 2013-07-08
I was trying to do that, but I don't exactly know which option to use. I actually tried a bunch of options from reading the manual, but I don't know what to look for. I greatly appreciate your help with this.

---

### Post by Shadius on 2013-07-10
Bump

---

### Post by mips on 2013-07-11
Short test,
```

sudo smartctl --test=short /dev/sd[COLOR=#ff0000]X[/COLOR]
```

Long test,
```
sudo smartctl --test=long /dev/sd[COLOR=#ff0000]X[/COLOR]
```


Results of test(s),
```
sudo smartctl -a /dev/sd[COLOR=#ff0000]X[/COLOR]
```

Where [COLOR=#ff0000]X[/COLOR] is your particular drive letter.

Remember to wait during the tests, it will tell you more or less when it will be finished.


[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]

---

