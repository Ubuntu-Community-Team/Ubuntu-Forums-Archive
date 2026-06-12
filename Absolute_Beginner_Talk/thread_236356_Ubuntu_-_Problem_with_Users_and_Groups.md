---
title: "Ubuntu - Problem with Users and Groups"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by henrikfromnorway on 2006-08-14
Hi!

I have Ubuntu installed on my shell/web-server, and I tried to start Users and Groups (in Gnome)

I got this error:
```
ERROR

The configuration could not be loaded

There was an error running the backend script
```

When I press OK, the program terminates.

How can I fix this? I've tried logout-login, but it didn't work.
I also googled, but I didn't find anything good.

I got a hint; 
```
gksu users-admin
``` in termnial

That resulted in this:
```
hc@square:~$ sudo gksu users-admin

(gksu:13466): Gtk-WARNING **: cannot open display:
hc@square:~$
```
I also tried without sudo in front, no difference.


So, any ideas?

---

### Post by reacocard on 2006-08-14
try just sudo users-admin. gksu is just the GUI version of sudo.

---

### Post by henrikfromnorway on 2006-08-14
Got the same error, but I also got this:

```
sudo ushc@square:~$ sudo users-admin
Password:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function 
snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat 
returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
Entity: line 439: parser error : Input is not proper UTF-8, indicate 
encoding !
Bytes: 0xF8 0xF8 0xF8 0x74
      <comment>Ove Ragnar,,,,overagnar er s&#65533;&#65533;&#65533;t &lt;3</comment>
                                           ^
hc@square:~$

```

---

### Post by reacocard on 2006-08-14
since this is a shell/web server, how are how controling it? if it's through ssh, that's your problem right there. you can't run a gui program over ssh.

---

### Post by henrikfromnorway on 2006-08-14
Hahaha, i'm not so nuub. :p
i have it right here, with a monitor.

but; i found the problem.

it was an ø in the name (not username, real name) and that screwed everything up. the program starts now :)

---

