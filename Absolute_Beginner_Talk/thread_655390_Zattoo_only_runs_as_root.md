---
title: "Zattoo only runs as root"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by PereUbu on 2008-01-01
I've just installed Zattoo on my laptop and on my desktop pc, both with Ubuntu 7.10.

On my laptop it runs ok, but on my desktop pc it crashes when it is starting up.

I tried to run Zattoo as root after reading this post...
[http://ubuntuforums.org/showpost.php?p=2948771&postcount=26](http://ubuntuforums.org/showpost.php?p=2948771&postcount=26) 

... and it worked.

How can I get it to work as a regular user on my desktop pc?

Best regards PereUbu

---

### Post by kzutter on 2008-01-01
I do not know this program, but it could be that you are a member of a group on your laptop that is allowed to run this program, while you are not a member of that group on your desktop.

Do two things:
[LIST=1]
[*]Find out who owns the executable on each machine - are they different?
[*]Find out which groups you belong to on each machine - are they different?
[/LIST]

Use the CLI to determine these things,

```
 ls -al /usr/bin/zatoo_player
```

and

```
groups
```

respectively.

---

### Post by PereUbu on 2008-01-01
Thanks for your tip, kzutter!
As you can see from the output underneath, the output from my two computers are exactly the same.
```
ls -all /usr/bin/zattoo_player
_Desktop:_ 
-rwxr-xr-x 1 root root 625720 2007-12-17 21:56 /usr/bin/zattoo_player
_Laptop:_
-rwxr-xr-x 1 root root 625720 2007-12-17 21:56 /usr/bin/zattoo_player

groups
_Desktop:_ 
myusername adm dialout cdrom floppy audio dip video plugdev scanner lpadmin netdev powerdev admin
_Laptop:_
myusername adm dialout cdrom floppy audio dip video plugdev scanner lpadmin netdev powerdev admin
```

Is there another possible solution to this problem?

This is what I get when starting Zattoo from CLI:
```
/usr/bin/zattoo_player

_Desktop:_
20:07:18 01-01-2008 [MSG]       Current locale is da_DK.UTF-8
20:07:18 01-01-2008 [MSG]       Welcome to Zattoo (3.0.9.10040)
20:07:18 01-01-2008 [MSG]       Further log messages will be written to /home/myusername/.Zattoo/Data/logs/zattoo.debuglog
Segmentation fault (core dumped)

_Laptop:_
20:01:34 01-01-2008 [MSG]       Current locale is da_DK.UTF-8
20:01:34 01-01-2008 [MSG]       Welcome to Zattoo (3.0.9.10040)
20:01:34 01-01-2008 [MSG]       Further log messages will be written to /home/myusername/.Zattoo/Data/logs/zattoo.debuglog
```

This the debuglogs:
```
/home/myusername/.Zattoo/Data/logs/zattoo.debuglog

_Desktop_:
20:07:18 01-01-2008 [MSG]	Welcome to Zattoo (3.0.9.10040)
20:07:18 01-01-2008 [MSG]	OpenGL Info:
20:07:18 01-01-2008 [MSG]	GL_RENDERER = GeForce4 MX 440/AGP/SSE/3DNOW!
20:07:18 01-01-2008 [MSG]	GL_VERSION = 1.5.8 NVIDIA 96.39
20:07:19 01-01-2008 [MSG]	closed channel
20:07:19 01-01-2008 [MSG]	player status: Starting Up...
20:07:19 01-01-2008 [MSG]	zattood_initlib.  Assumes zattood is in the same current working dir.
20:07:19 01-01-2008 [MSG]	Using conf directory: /home/myusername/.Zattoo/Data
20:07:19 01-01-2008 [MSG]	Using executable home: /usr/bin
20:07:20 01-01-2008 [MSG]	player status: Starting Up...
01-01 19:07:20.105 	D2 Absent nb backup address, do without.
01-01 19:07:20.106 	D1 tmeshd: realmaxcp set to 4
20:07:20 01-01-2008 [MSG]	new zattood status = 0
20:07:20 01-01-2008 [MSG]	closed channel
20:07:20 01-01-2008 [MSG]	player status: Starting Up...
20:07:20 01-01-2008 [DEBUG]	FD response
20:07:20 01-01-2008 [MSG]	There are no updates available.
20:07:20 01-01-2008 [MSG]	player status: Starting Up...

_Laptop_:
20:01:34 01-01-2008 [MSG]	Welcome to Zattoo (3.0.9.10040)
20:01:35 01-01-2008 [MSG]	OpenGL Info:
20:01:35 01-01-2008 [MSG]	GL_RENDERER = Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
20:01:35 01-01-2008 [MSG]	GL_VERSION = 1.3 Mesa 7.0.1
20:01:36 01-01-2008 [MSG]	closed channel
20:01:36 01-01-2008 [MSG]	player status: Starting Up...
20:01:36 01-01-2008 [MSG]	zattood_initlib.  Assumes zattood is in the same current working dir.
20:01:36 01-01-2008 [MSG]	Using conf directory: /home/myusername/.Zattoo/Data
20:01:36 01-01-2008 [MSG]	Using executable home: /usr/bin
20:01:36 01-01-2008 [MSG]	player status: Starting Up...
01-01 19:01:36.608 	D2 Absent nb backup address, do without.
01-01 19:01:36.608 	D1 tmeshd: realmaxcp set to 4
20:01:36 01-01-2008 [MSG]	new zattood status = 0
20:01:36 01-01-2008 [MSG]	closed channel
20:01:36 01-01-2008 [MSG]	player status: Starting Up...
20:01:36 01-01-2008 [DEBUG]	FD response
20:01:36 01-01-2008 [MSG]	There are no updates available.
20:01:36 01-01-2008 [MSG]	player status: Starting Up...
20:01:37 01-01-2008 [MSG]	login of user: mail@mydomain.com -->status=0
20:01:37 01-01-2008 [MSG]	player status: Logging in...
20:01:37 01-01-2008 [MSG]	new zattood status = 1000
20:01:38 01-01-2008 [MSG]	Did log in: mail@mydomain.com
20:01:38 01-01-2008 [MSG]	Building channel list
20:01:38 01-01-2008 [MSG]	player status: Logged in
20:01:38 01-01-2008 [MSG]	new zattood status = 1002
20:01:42 01-01-2008 [MSG]	player status: Logged in
20:01:42 01-01-2008 [MSG]	player status: Logged in
20:01:42 01-01-2008 [MSG]	player status: Logged in
20:01:42 01-01-2008 [MSG]	player status: Logged in

```

/PereUbu

---

### Post by hyper_ch on 2008-01-01
did you try the latest zattoo version?

---

### Post by PereUbu on 2008-01-02
Yes, I did. Zattoo (3.0.9.10040) is the latest version at the moment. I had the same problem with the former version, as well.

/Pere Ubu

---

### Post by cowkiller on 2008-01-06
Hi, I'm getting the same error here. I can't run it as user (I checked the permissions and everyone should be able to run it), and when I run it as root I just can get a bad image with a lot of flickering.

If I run it as user I get segmentation fault (core dumped) and this output at the zattoo.debuglog:

```
01:36:35 07/01/08 [MSG]	Welcome to Zattoo (3.0.8.9191)
01:36:36 07/01/08 [MSG]	OpenGL Info:
01:36:36 07/01/08 [MSG]	GL_RENDERER = ATI RADEON 9600 Series
01:36:36 07/01/08 [MSG]	GL_VERSION = 2.1.7170 Release
01:36:36 07/01/08 [MSG]	closed channel
01:36:36 07/01/08 [MSG]	player status: Starting Up...
01:36:36 07/01/08 [MSG]	zattood_initlib.  Assumes zattood is in the same current working dir.
01:36:36 07/01/08 [MSG]	Using conf directory: /home/simon/.Zattoo/Data
01:36:36 07/01/08 [MSG]	Using executable home: /usr/bin
01-07 00:36:36.944 	D2 Absent nb backup address, do without.
01-07 00:36:36.944 	D2 Absent nb backup address, do without.
01-07 00:36:36.944 	D2 Absent nb backup address, do without.
01-07 00:36:36.944 	D1 tmeshd: realmaxcp set to 4
01:36:37 07/01/08 [MSG]	player status: Starting Up...
01:36:37 07/01/08 [MSG]	new zattood status = 0
01:36:37 07/01/08 [MSG]	closed channel
01:36:37 07/01/08 [MSG]	player status: Starting Up...
01:36:37 07/01/08 [DEBUG]	FD response
01:36:37 07/01/08 [MSG]	There are no updates available.
01:36:37 07/01/08 [MSG]	player status: Starting Up...
```

I hope there's any solution or that anyone has got more info about this. thx in advance.

---

### Post by NorQue on 2008-04-03
Something similar is happening to me, but my zattoo.debuglog looks different. The executable crashes with the message "Segmentation fault (core dumped)" whe I run it as user, but it works fine when I start it as root. Has anyone found a solution for this problem during the last few months?

```
07:00:22 PM 04/03/2008 [MSG]	Welcome to Zattoo (3.1.0.11060)
07:00:22 PM 04/03/2008 [MSG]	zattood_initlib.  Assumes zattood is in the same current working dir.
07:00:22 PM 04/03/2008 [MSG]	Using conf directory: /home/nrq/.Zattoo/Data
07:00:22 PM 04/03/2008 [MSG]	Using executable home: /usr/bin
04-03 17:00:22.474 	D2 Absent nb backup address, do without.
04-03 17:00:22.474 	D1 tmeshd: realmaxcp set to 4
07:00:22 PM 04/03/2008 [MSG]	OpenGL Info:
07:00:22 PM 04/03/2008 [MSG]	GL_RENDERER = GeForce Go 7600/PCI/SSE2
07:00:22 PM 04/03/2008 [MSG]	GL_VERSION = 2.1.0 NVIDIA 96.39
07:00:22 PM 04/03/2008 [MSG]	closed channel
07:00:22 PM 04/03/2008 [MSG]	closed channel
07:00:22 PM 04/03/2008 [DEBUG]	Delaying FD response
07:00:22 PM 04/03/2008 [DEBUG]	FD response
07:00:22 PM 04/03/2008 [MSG]	There are no updates available.
07:00:22 PM 04/03/2008 [DEBUG]	Delayed FD response
07:00:22 PM 04/03/2008 [MSG]	new zattood status = 0, old status = -1
```

TiA! :)

---

