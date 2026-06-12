---
title: "can't play a windows .wax stream"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-04-02
Hi,

trying to play this stream:

[http://boss.streamos.com/wmedia/jacksonville/radio_shows/032906jaguarsthisweek.wax](http://boss.streamos.com/wmedia/jacksonville/radio_shows/032906jaguarsthisweek.wax)

from jaguars.com.

i have the proper win codecs installed, and firefox opens up mplayer to play it, but it won't play.

i tried it from the command line and got this:

[PHP]box@ubuntu:~$ mplayer http://boss.streamos.com/wmedia/jacksonville/radio_sh ows/032906jaguarsthisweek.wax
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Duron MG Morgan (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for Debian.


86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing http://boss.streamos.com/wmedia/jacksonville/radio_shows/032906jaguarsth isweek.wax.
STREAM_HTTP(1), URL: http://boss.streamos.com/wmedia/jacksonville/radio_shows/03 2906jaguarsthisweek.wax
Resolving boss.streamos.com for AF_INET6...
Couldn't resolve name for AF_INET6: boss.streamos.com
Resolving boss.streamos.com for AF_INET...
Connecting to server boss.streamos.com[69.27.174.221]:80 ...
STREAM_ASF, URL: http://boss.streamos.com/wmedia/jacksonville/radio_shows/032906 jaguarsthisweek.wax
Resolving boss.streamos.com for AF_INET6...
Couldn't resolve name for AF_INET6: boss.streamos.com
Resolving boss.streamos.com for AF_INET...
Connecting to server boss.streamos.com[69.27.174.221]:80 ...
Cache fill:  0.09% (941 bytes)

Exiting... (End of file)[/PHP]

hmm.... system startup scripts...  thought i'd ask before i bust out the scalpel and start doing some damage.  ;) 

i couldn't get this file type to play on my mac to save my life and i flat refuse to resort to ie.  

thanks,

takayuki

---

### Post by takayuki on 2006-04-02
got it.

the mplayer plugin for mozilla did the trick.

also, vlc worked.  both downloaded via synaptic: System > Administration > Synaptic Package Manager

cool.  micro$oft streams without micro$oft.

---

