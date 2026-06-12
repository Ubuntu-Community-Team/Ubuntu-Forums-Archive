---
title: "Gnome alsa mixer crashes"
date: 2006-06-18
forum: Bug Reports / Support
---

### Post by matjaz_pirnovar on 2006-06-18
I have Dapper for a week now, but yesterday sound suddenly stopped working. When I turn on the computer, default sound setting is MUTE.

So I wanted to install Gnome alsa mixer to change the "defaul MUTE". But it doesn't want to run after installation. I get the icon in Applications/ Sound&Video but when I open it, window is empty with File and Help toolboxes at the top.

When I try to open it in File -> Preferences it reports an error (The device quit unexpectedly. Please report this to the developers...) and the following report is:

Backtrace was generated from '/usr/bin/gnome-alsamixer'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1223436064 (LWP 734]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb74bd463 in __waitpid_nocancel ()
from /lib/tls/i686/cmov/libpthread.so.0
#2 0xb7f728e6 in libgnomeui_module_info_get ()
from /usr/lib/libgnomeui-2.so.0
#3 <signal handler called>
#4 0x0804cae1 in ?? ()
#5 0x080a0d20 in ?? ()
#6 0x082965ac in ?? ()
#7 0xbf9c8428 in ?? ()
#8 0x08051366 in ?? ()
#9 0x00000000 in ?? ()

Thread 1 (Thread -1223436064 (LWP 734):
#0 0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1 0xb74bd463 in __waitpid_nocancel ()
from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2 0xb7f728e6 in libgnomeui_module_info_get ()
from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3 <signal handler called>
No symbol table info available.
#4 0x0804cae1 in ?? ()
No symbol table info available.
#5 0x080a0d20 in ?? ()
No symbol table info available.
#6 0x082965ac in ?? ()
No symbol table info available.
#7 0xbf9c8428 in ?? ()
No symbol table info available.
#8 0x08051366 in ?? ()
No symbol table info available.
#9 0x00000000 in ?? ()
No symbol table info available.
#0 0xffffe410 in __kernel_vsyscall ()

The Bug Buddy opens and suggests to report the 'bug'. Have a funny feeling that content of the mixer is somehow empty...
Sound and video devices run, but there is no sound. And when I run Mplayer it says 'no sound. It 'couldn't be initiated'

Any clues? The repository has no broken packages.

Have no sound.

Really appreciate help.

Thanks.

M

---

### Post by matjaz_pirnovar on 2006-06-21
When I type "alsamixer" in terminal I get this:

matjaz@cpc5-cbly1-0-0-cust771Matjaz:~$ alsamixer
ALSA lib conf.c:1592:(snd_config_load1) _toplevel_:29:1:Unexpected char
ALSA lib conf.c:2837:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2700:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3066:(snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: Invalid argument
matjaz@cpc5-cbly1-0-0-cust771Matjaz:~$

Something looks corrupt.

Can someone tell me what is happening to my alsamixer please. 

REALLY appreciate help. Thanks.

Matjaz

---

### Post by matjaz_pirnovar on 2006-06-23
An update on this crash.

I did mess around a bit with alsa configuration when I was trying to reconfigure it as instructed for skype installation - so it would work together with ESD.

Now I completely reinstalled Ububtu 6.06 (erasing previous one) and now alsa works like a charm.

I will examine again what I reconfigured before (instructions in "How I got skype to work" posting).

Matjaz

PS: Let's hope it stayes this way, fingers crossed

---

