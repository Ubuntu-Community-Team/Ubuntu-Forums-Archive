---
title: "Xauth? Whatever it is drives me up the wall"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-09-08
I don't understand XAUTH at all....

All i'm trying to do, is SSH into a box, run VLC and display it on the monitor connected to that box.


At mars : ssh pluto

ssh@pluto : export DISPLAY=:0
ssh@pluto : vlc -I http -f

So no running processes on one machine and displaying them on another, it runs on pluto and is displayed on pluto.

Of course this decides to work every second day. How do i fix it so it always works?. Essientially i'm getting a Xlib: connection to ":0.0" refused.

So xserver is refusing connections from stuff run on its own box?!?!?! 

How do i set up xauth to bloody work right?.

---

### Post by 13ojo on 2007-09-08
What my putty terminal shows. (jibberish is it displaying ncurses kinda stuff, instead of playing on the pc im logged into )


> =~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2007.09.08 21:47:17 =~=~=~=~=~=~=~=~=~=~=~=
login as: bojo
bojo@192.168.0.201's password: 
Linux pluto 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Fri Jan  1 09:04:08 1999 from 192.168.0.2

]0;bojo@pluto: ~bojo@pluto:~$ vlc -I httpexport DISPLAY=:0
[C[C[C[C[C[C[C[C[C[C[C[C[C[C[6Pvlc -I http
VLC media player 0.8.6 Janus
[00000287] main interface: creating httpd
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 66
[00000373] xvideo video output error: cannot open display 
[00000373] x11 video output error: cannot open display 
[00000378] glx private error: cannot open display
[00000378] glx private error: no GLX support


]0;caca for ncurses[?1049h[1;24r[m(B[4l[?7h[?1h=[?25l[?1000h[39;49m]0;VLC - Colour AsCii Art (caca)[39;49m[37m[40m[H[2J[32m[40m;[0;5m(B[34m[40mS@8@XX@8X[33m[40mS[0;1m(B[30m[43m8[0m(B[37m[43m8[0;5m(B[33m[40m: [35m[40m.X[34m[40m@S[35m[40m8[34m[40mX[35m[40m8[34m[40m@8[0;1m(B[30m[44m88[0m(B[34m[40m8[0;5m(B[34m[40m8[0m(B[34m[40m8[0;5m(B[34m[40m8[0m(B[34m[40m8[0;1m(B[30m[40m8[0m(B[30m[44m8[0;1m(B[30m[40m8[0m(B[34m[40m8[0;1m(B[30m[40m8[0m(B[34m[40m@[0;1m(B[30m[40m8[0m(B[34m[40mX[0;1m(B[30m[40m@[0m(B[34m[40mS[0;1m(B[30m[40m@[0m(B[34m[40mS[0;1m(B[30m[40m@[0m(B[34m[40mS[0;1m(B[30m[40m@[0m(B[34m[40mX[0;5m(B[35m[40m.[0;1m(B[30m[44m8S[0m(B[30m[44m8[0;1m(B[30m[40m@[0m(B[31m[40mS[0;5m(B[30m[40m8[0m(B[31m[40m8[0;1m(B[30m[40m88[0;5m(B[34m[40m@[0m(B[31m[40m8[0;5m(B[31m[40mX[0m(B[31m[40m8[0;5m(B[34m[40mS[0m(B[31m[40m8[0;5m(B[35m[408[30m[46m8[34m[45m8[0;5m(B[36m[40mt[34m[44m@[36m[40m%[34m[44m8X%[0;1m(B[34m[44m8[30m[44m88@%[0m(B[30m[44m8[0;5m(B[30m[40m8[0m(B[34m[40mX[0;1m(B[30m[40m8[0m(B[34m[40m8[0;1m(B[30m[40m88[0m(B[34m[40m@[0;1m(B[30m[40m@8[0;5m(B[34m[40m8[0m(B[34m[40mS[0;5m(B[30m[40m8[0;1m(B[30m[40m8[0;5m(B[34m[40m@[0m(B[34m[40m8[0;1m(B[30m[40m8@[0m(B[34m[40mX[0;1m(B[30m[40m@XX[0m(B[34m[40m@[0;1m(B[30m[40m@[0m(B[34m[40mX[0;1m(B[30m[40m8[0;5m(B[30m[40mX@[0m(B[30m[41m8[0;1m(B[30m[40mX[24d[m(B[39;49m[37m[40m]0;[?1000l[?12l[?25h[39;49m
[K[24;1H[?1049l
[?1l>signal 2 received, terminating vlc - do it again in case it gets stuck
[00000281] main playlist: stopping playback



]0;bojo@pluto: ~bojo@pluto:~$ export Dis[K[KS[KOS[K[KISPLAY=:0
]0;bojo@pluto: ~bojo@pluto:~$ export DISPLAY=:0
[C[C[C[C[C[C[C[C[C[C[C[C[C[C[6Pvlc -I http
VLC media player 0.8.6 Janus
[00000287] main interface: creating httpd
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 66
Xlib: connection to ":0.0" refused by server

Xlib: Invalid MIT-MAGIC-COOKIE-1 key

[00000378] xvideo video output error: cannot open display :0
Xlib: connection to ":0.0" refused by server

Xlib: Invalid MIT-MAGIC-COOKIE-1 key

[00000378] x11 video output error: cannot open display :0
Xlib: connection to ":0.0" refused by server

Xlib: Invalid MIT-MAGIC-COOKIE-1 key

[00000389] glx private error: cannot open display
[00000389] glx private error: no GLX support
Xlib: connection to ":0.0" refused by server

Xlib: Invalid MIT-MAGIC-COOKIE-1 key

[00000378] caca video output error: cannot initialize libcaca
Xlib: connection to ":0.0" refused by server

Xlib: Invalid MIT-MAGIC-COOKIE-1 key



7m[40mnI[m(B[37m[40mM[10C)p[1m[37m[40m|[m(B[37m[40mO[1m[37m[40m%%[m(B[37m[40mL[1m[30m[40m Q[m(B[37m[40m`[8;26H[1m[37m[40m][m(B[37m[40m-=[1m[30m[40m [m(B[37m[40m-/j[1m[37m[40ml)[10C[m(B[37m[40mc<)c[1m[37m[40m%`[m(B[37m[40m_[1m[30m[40m   [m(B[37m[40m-_[1m[30m[40m [9;25H[m(B[37m[40m9[9C+[18;23H[1m[37m[40m<do1[8C%[m(B[37m[40mQ[5C[1m[30m[40m [10CQ  [m(B[37m[40m,[17C[1m[30m[40mQ[19;23H[m(B[37m[40m-[1m[37m[40mvXrvuXZZn%[m(B[37m[40mQ[9C_[9C,[16C=[1m[30m[40m [m(B[37m[40m)[20;25H[1m[37m[40mIX][5Cv%1[17C`[21;28HXIn[m(B[37m[40mg[1m[37m[40m>[m(B[37m[40mF[1m[37m[40mvoo}[m(B[37m[40m,[22;26H[1m[37m[40mi%>[m(B[37m[40mqgmn4[14C_[16C__[8C[1m[30m[40m [23;26H[37m%[m(B[37m[40m#m4QF!j[1m[37m[40mn3[30C[30m [m(B[37m[40m)[1m[30m[40m [24;26H[m(B[37m[40mj[1m[37m[40m<%%[m(B[37m[40mgd!][1m[37m[40mvvv>[m(B[37m[40m=[16C_%,[10C-[1;1H[24;1H[m(B[39

[?1049lsignal 2 received, terminating vlc - do it again in case it gets stuck
[00000281] main playlist: stopping playback
]0;bojo@pluto: ~bojo@pluto:~$ exit
logout


---

