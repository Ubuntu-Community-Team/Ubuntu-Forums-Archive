---
title: "Default Volume Setting?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by AdrianStrays on 2008-04-08
I have a tendenacy to leave the volume on my laptop cranked up, and because of this whenever I boot I hear the start up noise blaring.  This happens consistently in the library or during lectures.  I was wondering if there was a way I could set a default setting that the volume would go to everytime I start my computer.

---

### Post by warbread on 2008-04-08
An easier solution might be to turn off system even sounds, or even just the startup sound.  I've had to do the same thing.  If you do, make sure you go into Administration > Login Window and turn off the sound there.

---

### Post by kpkeerthi on 2008-04-08
Perhaps consider turning off login sound from System > Preferences > Sound until someone more knowledgeable chimes in with a proper fix for your problem.

[IMG]http://www.howtogeek.com/wp-content/uploads/2006/12/WindowsLiveWriter/DisabletheLoginSoundonUbuntu_62E8/loginsound.png[/IMG]

---

### Post by kpkeerthi on 2008-04-08
1. Get the numid of 'master channel' from **/etc/asound.state**
It might look something like this
```

control**[COLOR="Red"].2[/COLOR]** {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Playback Volume'
		value.0 15
		value.1 15
	}

```
2. To set the master channel volume to 50% 
```

amixer -c 0 cset **[COLOR="Red"]numid=2[/COLOR]** 50% 

```

Test this code from a terminal and if it works, add the command to **/etc/rc.local**

For more info see
[http://murga-linux.com/puppy/viewtopic.php?t=23900&sid=25c4934f35eb17a5fe0237365fe575ff](http://murga-linux.com/puppy/viewtopic.php?t=23900&sid=25c4934f35eb17a5fe0237365fe575ff)
[http://www.penguin-soft.com/penguin/man/1/amixer.html](http://www.penguin-soft.com/penguin/man/1/amixer.html)

---

### Post by erginemr on 2008-04-08
As a complement to **kpkeerthi**'s suggestion, the file in question in my system resides in: **/var/lib/alsa/asound.state**

which you can view with:
```
less /var/lib/alsa/asound.state
```

---

### Post by AdrianStrays on 2008-04-08
Thank you for your help thus far, but where exactly do I add the command
amixer -c 0 cset numid=2 50%
In the asound.state file?

---

### Post by redbob on 2008-04-09
Why not just type it in crontab?
> @reboot amixer -c 0 cset numid=2 50% 
Don't forget you must type "sudo crontab -e", so crontab will executed by root.

---

### Post by AdrianStrays on 2008-04-09
Crontab....?

---

### Post by kpkeerthi on 2008-04-09
> **AdrianStrays said:**
> Thank you for your help thus far, but where exactly do I add the command
amixer -c 0 cset numid=2 50%
In the asound.state file?

> **kpkeerthi said:**
> 1
2. To set the master channel volume to 50% 
```

amixer -c 0 cset **[COLOR="Red"]numid=2[/COLOR]** 50% 

```

[SIZE="2"]Test this code from a terminal and if it works, add the command to **/etc/rc.local**[/SIZE]


to /etc/rc.local as I explained in my earlier post

---

### Post by redbob on 2008-04-09
crontab is a scheduler for Linux. It works like Task Scheduler from Windows. It wil executes amixer at system startup. My computer plays music almost 24h per day, at 23h it lay down volume level at 50% by crontab, so at 05h20  i raise it up to 100% to wake me up!!
Look this link:
> [http://team.macnn.com/drafts/crontab_defs.html](http://team.macnn.com/drafts/crontab_defs.html)

---

### Post by kpkeerthi on 2008-04-10
> **redbob said:**
> crontab is a scheduler for Linux. It works like Task Scheduler from Windows. **It wil executes amixer at system startup.** 

No . crontab entries won't run at system startup. They run at a time specified in crontab file.

---

### Post by redbob on 2008-04-10
kpkeerthi, you're right,  crontab runs anything in specified time. Perhaps, @reboot is a specified time! Everything you specificate with @reboot syntax will be done at startup time! Look, I made a test and it worked. I put this instruction in crontab
> @reboot /etc/init.d/gdm stop
And it worked. Look at /var/log/syslog:
> Apr 10 19:13:00 pica-pau anacron[5610]: Anacron 2.3 started on 2008-04-10
Apr 10 19:13:00 pica-pau anacron[5610]: Normal exit (0 jobs run)
Apr 10 19:13:00 pica-pau /usr/sbin/cron[5637]: (CRON) INFO (pidfile fd = 3)
Apr 10 19:13:00 pica-pau /usr/sbin/cron[5638]: (CRON) STARTUP (fork ok)
Apr 10 19:13:00 pica-pau /usr/sbin/cron[5638]: (CRON) INFO (Running @reboot jobs)
Apr 10 19:13:00 pica-pau kernel: [   74.701688] tap0: no IPv6 routers present
Apr 10 19:13:00 pica-pau /USR/SBIN/CRON[5682]: (root) CMD (/etc/init.d/gdm stop)

---

### Post by kpkeerthi on 2008-04-11
Thanks redbob. I was not aware of @reboot thing. I learnt something new from you. Cheers.

---

### Post by AdrianStrays on 2008-04-13
I'm still trying to figure this out, the code you guys provided didn't work for me.  The only time anything that would cause change would be if I swapped the location of the percentage.

---

### Post by AdrianStrays on 2008-04-13
I actually was given a solution, by Nickrud on Irc.  The following line:
amixer sset Master 10%

Thanks Nick!

---

### Post by redbob on 2008-04-14
This solution is not suitable, due to several types of audio devices. In my case, this doesn't works. The message below> amixer: Unable to find simple control 'Master',0
tells it. Other consideration to do is: if you have two audio output jacks, it may alter both. If you type this command> amixer controlsyou'll know exactly which interface to deal with.

---

