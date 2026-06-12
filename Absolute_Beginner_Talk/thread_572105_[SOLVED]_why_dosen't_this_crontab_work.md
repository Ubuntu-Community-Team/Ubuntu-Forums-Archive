---
title: "[SOLVED] why dosen't this crontab work?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-10-10
Hi All,

in crontab i got:
[COLOR="SeaGreen"]*/25 * * * * ~/amule.cron[/COLOR]

in amule.cron i got:
```
#!/bin/sh

pidof amule >/dev/null

if [ $? != 0 ]
then
    logger amule stopped working restarting...
    exec /usr/bin/amule
fi
```

it logs  [COLOR="SeaGreen"]amule stopped working restarting...[/COLOR]
[COLOR="Red"]but dosent start the exec /usr/bin/amule[/COLOR]

do i need to change crontab to:
[COLOR="SeaGreen"]*/25 * * * * root ~/amule.cron[/COLOR]

to make it work?

when i manually execute the script everything works great...but not when crontab executes it?

any ideas?

thanks...

---

### Post by HermanAB on 2007-10-10
Cron has a very limited environment.  You have to specify the full path of every program that you want to invoke.

Cheers,

Herman

---

### Post by hopelessone on 2007-10-10
?

err... sorry don't know what you mean...can you please give a e.g.?

thanks

---

### Post by hopelessone on 2007-10-10
do you mean something like [COLOR="SeaGreen"]*/25 * * * * $HOME/amule.cron[/COLOR] ??

will this work now?

---

### Post by hopelessone on 2007-10-12
please help[COLOR="Red"] exec /usr/bin/amule[/COLOR] dosent work...

but [COLOR="SeaGreen"]logger amule stopped working restarting... [/COLOR]does !!!!

any ideas??????

---

### Post by Dr Small on 2007-10-12
maybe because your files is called amule.cron, and yet it is a shell script.
Perhaps you could try renameing amule.cron to amule.sh and in your crontab add sh $HOME/amule.sh

Dr Small

---

### Post by hyper_ch on 2007-10-12
is the amule cron executable?

I'd use anyway
```

*/25 * * * * sh /path/to/amule.cron

```

---

### Post by jordanmthomas on 2007-10-12
The file extension doesn't matter, Dr Small (this is Linux after all).

Perhaps there's a problem with launching GUI apps from cron.  Try this:
```
xhost +
```
which should allow cron to run gui apps.
Then, in your cron job:
```
*/25 * * * * export DISPLAY=:0 && /home/jordan/amule.cron
```

note that xhost + allows unauthorized persons to launch things on your xserver.  I think there's a way to only let cron@local to do it as well.

---

### Post by hopelessone on 2007-10-12
jordanmthomas - thanks !!!!

```
*/25 * * * * export DISPLAY=:0 && /home/jordan/amule.cron
```

worked !!!

```
xhost +
``` <- i couldn't get this to go ...

all in all it worked...!!!

i love you ubuntu ...

thanks everyone...

---

