---
title: "[SOLVED] Disable Compiz on standby.. is it possible ?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by P4man on 2007-11-07
Compiz doesnt play nice with standby. That is well known, I am not looking for a magical solution for that, but for a simlpeworkaround: Is it possible to automatically stop compiz when I initiate a standby, ideally automatically start it again on resume ? 

Thing is, standby/resume works just fine if I disable Compiz first (simply in system > preferences > appearance and turn off desktop effects). After resuming I can re-enable it and everything works great.

Rather than doing it manually, could I create a script or something that would do this automatically ?

If that is too hard, at least could I make a launcher that disables/enables desktop effects? What is the command line .. euh.. command to do that ?

---

### Post by skymera on 2007-11-07
a wuick way to return to normal desktop with no effects is

alt+f2
metacity --replace

---

### Post by P4man on 2007-11-07
Thanks, thats a good start, with that I can make an icon to quickly stop Compiz. 
Can I also restart it with a similar command ?

---

### Post by Rinzwind on 2007-11-07
If you know about about coding have a look in /etc

/etc$ cd rc
rc0.d/ rc1.d/ rc2.d/ rc3.d/ rc4.d/ rc5.d/ rc6.d/ rcS.d/ 

These directories handle the start en stopping of your system and are called runlevels.
In detail: [http://www.faqs.org/docs/linux_scratch/chapter07/usage.html](http://www.faqs.org/docs/linux_scratch/chapter07/usage.html)

More info about creating scripts: 
[http://en.opensuse.org/SDB:How_to_Create_Your_Own_Init_Script](http://en.opensuse.org/SDB:How_to_Create_Your_Own_Init_Script)
[http://www.hackosis.com/index.php/2007/10/02/linux-create-your-own-initd-scripts/](http://www.hackosis.com/index.php/2007/10/02/linux-create-your-own-initd-scripts/)

The last link explains how to make a daemon that works like this:

myownscript start
myownscript stop

and if you stuff a line to start compiz in there and a metacity --replace in there you'd be set for life :)

Yes it's not beginners stuff. 
IF I have the time I'll try to whip something up.

---

### Post by P4man on 2007-11-07
Thank you, that is an extremely helpful answer. 
I didn't expect it to be easy, but learning is part of the fun with Linux, and this certainly seems worth delving in to.

meanwhile I figured out that

```
compiz --replace

```
will restart compiz, so I am marking this thread as solved. 

Of course, if you feel like guiding me further into automating this when initiating "Pauze" (standby) and resuming, you are most welcome :)

I suspect a lot of people would benefit from such a script, as almost everyone has problems using standby with compiz. Something as "simple" as this would be a nice workaround!

---

### Post by Rinzwind on 2007-11-07
I hope this does the trick

```
#!/bin/sh
### BEGIN INIT INFO
# Provides: Start and stop Compiz
# Required-Start: $network
# Required-Stop: $network
# Default-Start: 2 3 5
# Description: Start and stop Compiz 
### END INIT INFO

case "$1" in
	start)
	compiz --replace
	;;

	stop)
	metacity --replace
	;;

	*)
	;;	
esac
exit
```

I named it
SwitchCompiz.sh

Do a chmod 774 on the file to make it executable.


./SwitchCompiz start
./SwitchCompiz stop


Works in command line :)

I TAKE NO RESPONSIBILITY :+

---

### Post by P4man on 2007-11-07
sorry if this is a silly question.. but why do I need a script like that ? Is it because one can not define different actions for suspending rather than resuming, or some other reason why just adding "compiz --replace" in the correct "place" wouldnt work ?

---

### Post by P4man on 2007-11-18
Rinzwind, can you elaborate a bit where I call these scripts ?

I've been looking further into this, but I can't get it working. Must be doing something stupid. I figured the way to do this was edit sleep.sh, but that didn't quite work.

So I tried with: /etc/acpi/perpare.sh

I added a line at the beginning  calling:
```
/usr/bin/metacity --replace
```

But it does nothing.  Upon resuming (if it does), its still compiz that is running, not metacity.

I tried redirecting the output to a text file:
```
/usr/bin/metacity --replace > /home/myname/acpitest.txt
```

The file is created, so the code is executed but is empty. 

What am I doing wrong ?

---

### Post by klhoard on 2007-12-06
Rizwind,

The scripts work great!!  This needs to be made a sticky somewhere, especially over at the games forums.  The only re-boots I've had to do with my Ubuntu system have been program conflicts with Compiz.  

Now if someone can show me how to refine this fine script so all of my open programs return to their original workspace window.

---

