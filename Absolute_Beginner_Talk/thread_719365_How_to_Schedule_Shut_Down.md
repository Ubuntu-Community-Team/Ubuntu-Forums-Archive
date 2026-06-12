---
title: "How to Schedule Shut Down?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by kelinu on 2008-03-09
Hi guys,
I've been wondering if there is any way to schedule Ubuntu to shut down at a specific time i choose.  (like a sort of Auto Shat Down)  If there is any program or any way to do so, could you please tell me of it?  
Thanks,
Mike

---

### Post by banewman on 2008-03-09
If you type in a terminal -
sudo shutdown -h 5
the system will shutdown in 5 min.
Hope it helps
:)

---

### Post by hyper_ch on 2008-03-09
if you want to make it regurarly shutting down you'd use a "poweroff" comman in a cron job.

---

### Post by kleo skywalker on 2008-03-09
> **banewman said:**
> If you type in a terminal -
sudo shutdown -h 5
the system will shutdown in 5 min.
Hope it helps
:)

Seriously?
This is awesome.

---

### Post by billgoldberg on 2008-03-09
```
 shutdown --help
```
Usage: shutdown [OPTION]... TIME [MESSAGE]
Bring the system down.

Options:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

TIME may have different formats, the most common is simply the word 'now' which
will bring the system down immediately.  Other valid formats are +m, where m is
the number of minutes to wait until shutting down and hh:mm which specifies the
time on the 24hr clock.

Logged in users are warned by a message sent to their terminal, you may include
an optional MESSAGE included with this.  Messages can be sent without actually
bringing the system down by using the -k option.

If TIME is given, the command will remain in the foreground until the shutdown
occurs.  It can be cancelled by Control-C, or by another user using the -c
option.

The system is brought down into maintenance (single-user) mode by default, you
can change this with either the -r or -h option which specify a reboot or
system halt respectively.  The -h option can be further modified with -H or -P
to specify whether to halt the system, or to power it off afterwards.  The
default is left up to the shutdown scripts.

Report bugs to <upstart-devel@lists.ubuntu.com>

---

### Post by kelinu on 2008-03-09
OK but would it be possible to do it like with time sor t of lke 7:00 AM let's say...Any progam?

---

### Post by hyper_ch on 2008-03-09
You can use cron to shut down any program at a given time.

---

### Post by kelinu on 2008-03-09
whats cron?

---

### Post by rolnics on 2008-03-09
> **kelinu said:**
> whats cron?

Interesting subject this thread. As for cron, I've just done a search in synaptic and found it, take a look for yourself, it basically says that it runs programs at specific times in the background, it can even do updates for you! As how to use it i don't know!

---

### Post by ./. on 2008-03-09
> **kelinu said:**
> whats cron?
Some examples:
[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)
[http://www.linuxhelp.net/guides/cron/](http://www.linuxhelp.net/guides/cron/)

Or type *man cron* at the command line for more information.

---

### Post by diegosouza on 2008-03-09
> **kelinu said:**
> whats cron?

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by xc3RnbFO8P on 2008-03-09
In Synaptic Package Manager **GShutdown**.

[http://gshutdown.tuxfamily.org/en/index.php]("http://gshutdown.tuxfamily.org/en/index.php")

---

### Post by davidwhthomas on 2008-04-07
Or, for a KDE graphical shutdown utility, try:

**kshutdown** from your package manager or,

[http://kshutdown.sourceforge.net/](http://kshutdown.sourceforge.net/) for the homepage.

DT

---

### Post by njparton on 2008-04-07
If you're going to use cron to shutdown at a specified time, remember to use sudo's cron not your own as the shutdown command needs root permissions:
 
```
sudo crontab -e
```
 
add your code in there.

---

### Post by prodigy6630 on 2008-04-07
I use gshutdown for schedulling shutdown which is very nice GUI and it's in the repositories.

---

### Post by jakupl on 2008-04-07
hmm not to throw this tread off topic, but I was just experimenting with cron.

I made a script that says:
```
#!/bin/bash
totem /home/jakup/Music/Damien\ Rice/9/*.ogg
```

I called the script "Dillo" and I placed it on the Desktop.

in terminal I entered 
crontab -e, wrote the following:

```
05 13 * * * /home/jakup/Desktop/Dillo
```

and saved it. But when the clock was 13:05 nothing happened...

the script is ok. what am i doing wrong?

---

### Post by kpkeerthi on 2008-04-07
Is the script file Dillo executable? 
You need to change totem to /usr/bin/totem (full path) when specifying it in a crontab.
You may also want to check [this]("http://ubuntuforums.org/showthread.php?t=185993") for cronning GUI application? (I would rather use /usr/bin/mplayer)

---

### Post by jakupl on 2008-04-07
ok now I changed the Dillo script to:

```
#!/bin/bash
/usr/bin/totem /home/jakup/Music/Damien\ Rice/9/*.ogg
```

and it is executable.

but still no luck. I will try to download Kcron. :)

---

### Post by kpkeerthi on 2008-04-07
What happens when you write ```
/usr/bin/totem /home/jakup/Music/Damien\ Rice/9/*.ogg
``` in a terminal?

---

### Post by jakupl on 2008-04-07
the music starts with totem... just as it should...

---

### Post by jakupl on 2008-04-07
there is no problem with the script. and Kcron is aware of it... because when I press "run now" it runs perfectly. It's only the timing that is the problem. it wont start at a specified time.

---

### Post by jakupl on 2008-04-07
and cron IS running... 

```
jakup@bobby:~$ ps -A | grep cron
 5923 ?        00:00:00 cron
```

---

### Post by kpkeerthi on 2008-04-07
Did you try with **export DISPLAY=:0** as mentioned in the link I provided earlier?

---

### Post by jakupl on 2008-04-07
that must be the problem.. but where do I put it?
do I simply write it in the terminal? or at the beginning of the crontab or what?

---

### Post by jakupl on 2008-04-07
IT WORKED :=)

I wrote ```
37 * * * * export DISPLAY=:0 && /home/jakup/Desktop/Dillo
```

thankyou very much

---

### Post by kpkeerthi on 2008-04-07
You are welcome. Glad it worked for you. :)

---

### Post by prismpirate on 2008-04-07
Or you could use a GUI interface using GShutdown:

[http://gshutdown.tuxfamily.org/en/download.php]("http://gshutdown.tuxfamily.org/en/download.php")

Allows Scheduling of Shutdowns :)

---

### Post by nyborjare on 2008-07-20
Sorry this is an old thread and nobody might look into it anymore. But I did.

I am trying to get CRON to start a script at a given time etc. But I cannot get this working.

In CRON i write:

55 09 * * * export DISPLAY=:0 && /scripts/streamrecord.

I know the script in /scripts/ does work as if I run it in terminal it works and if I use Kcron and hit Start now it works. But it does not work automatically.
Nothing happeneds if I use CRON

Can anybody help me. I am totally new and ned step by step suport if possible.

Regards and thank you in advance.

---

