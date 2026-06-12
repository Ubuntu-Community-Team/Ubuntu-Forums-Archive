---
title: "vncserver"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Aleks67 on 2008-03-10
I am trying to start vnc on my remote server running Ubuntu 6.06.

Using Putty I type the command vncserver:1 and get 'command not found'. 

Why might that be?

Aleks

---

### Post by .nedberg on 2008-03-10
Don't think you need the :1 at the end... I use vnc4server though...

---

### Post by Aleks67 on 2008-03-10
I tried without the :1 as you suggested and get the same message 'command not found'.

Any other ideas?

Aleks

---

### Post by .nedberg on 2008-03-10
Is vncserver installed? Try with vnc4server...

---

### Post by Aleks67 on 2008-03-10
Sorry but how do I do that? If I just type vnc4server I get the same message 'command not found'.

Aleks

---

### Post by .nedberg on 2008-03-10
I don't think you have the program installed. Install it with ```
sudo apt-get install vncserver
```or ```
sudo apt-get install vnc4server
```
vnc4server is preferred to vncserver, but I don't know if that is available in Dapper

---

### Post by Bubba64 on 2008-03-10
Learning to use the terminal is very beneficial in the long run, but if you want to see the programs they are available in synaptic if you search with vnc4server. synaptic is in system administration. Actually it is in my Gutsy distribution it may be different in Dapper as .nedberg suggests. I hope you understand what code is, these commands would be put in the terminal which is in application's accessories if not on the top bar.

---

### Post by Aleks67 on 2008-03-10
I get this message:

$ sudo apt-get install vncserver
Reading package lists... Done
Building dependency tree... Done
Package vncserver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vncserver has no installation candidate

Aleks

---

### Post by .nedberg on 2008-03-10
Try vnc4server

or ```
apt-cache search vnc | grep server
```and see if you get any hits

---

### Post by Aleks67 on 2008-03-10
vnc4server cannot be found.

$ apt-cache search vnc | grep server

Gives:

vino - VNC server for GNOME
vnc-common - Virtual network computing server software

Aleks

---

### Post by .nedberg on 2008-03-10
I just checked with my Dapper server install. Both vncserver and vnc4server is available.

Have you enabled universe and multiverse in /etc/apt/sources.list?

---

### Post by Aleks67 on 2008-03-10
Thank you so much for your help and sticking with this.

>Have you enabled universe and multiverse in /etc/apt/sources.list?

I don't think so, how can I tell or how do I do it?

Aleks

---

### Post by .nedberg on 2008-03-10
This is my sources.list on my Dapper machine:

```

cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

You can edit it with ```
sudo nano /etc/apt/sources.list
```(backup first!)

Remove any # in front of a **deb** or [B]deb-src[/] line. Especially the universe and multiverse ones!

Then ```
sudo apt-get update
``` adn install vnc4server

---

### Post by Aleks67 on 2008-03-10
After editing it looks like this:

```
$ cat /etc/apt/sources.list
#
deb cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/ dapper main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Is that correct?

Aleks

---

### Post by Bubba64 on 2008-03-10
I don't know if maybe this package is in the extra repositories available by opening system administration software resources and checking on everything but source code to get extra packages you might be missing besides this one your trying to get, good luck .nedberg has you on the right track.

---

### Post by .nedberg on 2008-03-10
Looks fine!

But I have a 'multiverse' at the end of these lines:```

deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

```

---

### Post by Aleks67 on 2008-03-10
Shall I add 'multiverse' at the end of these two lines and see what happens?

Aleks

---

### Post by .nedberg on 2008-03-10
Yes! Do that and ```
sudo apt-get update
```.

---

### Post by Aleks67 on 2008-03-10
Added 'mutiverse' and now looks like this:

```
cat /etc/apt/sources.list
#
deb cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/ dapper main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Then did:

```
sudo apt-get update
Ign cdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper Release.gpg
Ign cdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper Release
Ign cdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/main Packages
Ign cdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/restricted Packages
Ign cdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/main Packages
Ign cdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/restricted Packages
Errcdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/main Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Errcdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/restricted Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Errcdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/main Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Errcdrom://Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1) dapper/restricted Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get: 1 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get: 2 http://gb.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get: 3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get: 4 http://gb.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://gb.archive.ubuntu.com dapper Release
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security Release
Get: 5 http://gb.archive.ubuntu.com dapper-backports Release [38.4kB]
Get: 6 http://wine.budgetdedicated.com gutsy Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://gb.archive.ubuntu.com dapper/main Packages
Hit http://gb.archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Get: 7 http://gb.archive.ubuntu.com dapper/universe Packages [2458kB]
Hit http://wine.budgetdedicated.com gutsy Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Ign http://wine.budgetdedicated.com gutsy/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get: 8 http://security.ubuntu.com dapper-security/universe Packages [93.6kB]
Hit http://wine.budgetdedicated.com gutsy/main Sources
Hit http://wine.budgetdedicated.com gutsy/main Packages
Get: 9 http://security.ubuntu.com dapper-security/universe Sources [12.0kB]
Get: 10 http://gb.archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Get: 11 http://gb.archive.ubuntu.com dapper/universe Sources [975kB]
Get: 12 http://gb.archive.ubuntu.com dapper/multiverse Sources [46.6kB]
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Sources
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Get: 13 http://gb.archive.ubuntu.com dapper-backports/main Packages [20.4kB]
Get: 14 http://gb.archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get: 15 http://gb.archive.ubuntu.com dapper-backports/universe Packages [61.7kB]
Get: 16 http://gb.archive.ubuntu.com dapper-backports/multiverse Packages [12.2kB]
Get: 17 http://gb.archive.ubuntu.com dapper-backports/main Sources [5951B]
Get: 18 http://gb.archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get: 19 http://gb.archive.ubuntu.com dapper-backports/universe Sources [15.7kB]
Get: 20 http://gb.archive.ubuntu.com dapper-backports/multiverse Sources [2700B]
Fetched 3838kB in 5s (667kB/s)
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/dists/dapper/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/dists/dapper/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/dists/dapper/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)]/dists/dapper/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Aleks

---

### Post by .nedberg on 2008-03-10
You are getting some errors because of the 'deb cdrom' line.

It looks for packages on the cdrom you installed from, and would use that instead of downloading it. Get rid of it by adding a # in front of every 'deb cdrom' line.

---

### Post by Aleks67 on 2008-03-10
OK - did that and then:

```
sudo apt-get update
Get: 1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get: 2 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get: 3 http://gb.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get: 4 http://gb.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://gb.archive.ubuntu.com dapper Release
Get: 5 http://wine.budgetdedicated.com gutsy Release.gpg [191B]
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://gb.archive.ubuntu.com dapper-backports Release
Hit http://wine.budgetdedicated.com gutsy Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://gb.archive.ubuntu.com dapper/main Packages
Hit http://gb.archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Hit http://gb.archive.ubuntu.com dapper/universe Packages
Hit http://gb.archive.ubuntu.com dapper/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper/universe Sources
Hit http://gb.archive.ubuntu.com dapper/multiverse Sources
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Sources
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://gb.archive.ubuntu.com dapper-backports/main Packages
Hit http://gb.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://gb.archive.ubuntu.com dapper-backports/universe Packages
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper-backports/main Sources
Hit http://gb.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://gb.archive.ubuntu.com dapper-backports/universe Sources
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Sources
Ign http://wine.budgetdedicated.com gutsy/main Packages
Hit http://wine.budgetdedicated.com gutsy/main Sources
Hit http://wine.budgetdedicated.com gutsy/main Packages
Fetched 5B in 0s (24B/s)
Reading package lists... Done
```

- Aleks

---

### Post by .nedberg on 2008-03-10
Everything looks good now! Go ahead and install vnc4server```
sudo apt-get install vnc4server
``` (or vncserver if you prefer that one)

---

### Post by Aleks67 on 2008-03-10
OK did that:

```
sudo apt-get install vnc4server
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
vnc-java
The following NEW packages will be installed
vnc4server
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 1011kB of archives.
After unpacking 2392kB of additional disk space will be used.
Get: 1 http://security.ubuntu.com dapper-security/universe vnc4server 4.1.1+xorg1.0.2-0ubuntu1.6.06 [1011kB]
Fetched 1011kB in 0s (4846kB/s)
Selecting previously deselected package vnc4server.
(Reading database ... 70757 files and directories currently installed.)
Unpacking vnc4server (from .../vnc4server_4.1.1+xorg1.0.2-0ubuntu1.6.06_i386.deb) ...
Setting up vnc4server (4.1.1+xorg1.0.2-0ubuntu1.6.06) ...
```

Does that look as though it has been installed successfully? If so how do I run it?

Aleks

---

### Post by .nedberg on 2008-03-10
That looks just fine!

I start vnc4server at my gutsy-box like this```
vnc4server -extension XFIXES -depth 24 -geometry 1024x768
```
Try just ```
vnc4server
```first and then try to connect from another PC. When that works use the command above.

You will need to edit your ~/.vnc/xstartup file to fit your needs also.

---

### Post by Aleks67 on 2008-03-10
OK I tried your suggestion:

```
$ vnc4server

You will require a password to access your desktops.

usage: vncpasswd [passwdFile]


```

Does this mean I have to type 'vncpasswd mypassword'?

Aleks

---

### Post by .nedberg on 2008-03-10
Did it tell you to type a password or did it just exit? I thought it told you to type one (does on Gutsy where I run vnc4server).

If it does not, just run ```
vncpasswd
``` and it will ask for a password that you will have to use to access your desktop.

---

### Post by Aleks67 on 2008-03-10
Ok I did:

```
$ vnc4server

You will require a password to access your desktops.

usage: vncpasswd [passwdFile]
```

And then entered my password:

```
$ vncpasswd
Password:
Verify:

```

Aleks

---

### Post by .nedberg on 2008-03-10
OK, vnc4server is now set up with a password you will have to use to access your desktop. Start the server ```
vnc4server
```and try to connect

---

### Post by Aleks67 on 2008-03-10
Ok did that and then brought up VNC Free Edition Viewer for Windows Version 4.1.2 on my PC.

I entered my IP address xxx.xxx.xxx.xx and got the message:

unable to connect to host: Connection refused (10061)

Aleks

---

### Post by .nedberg on 2008-03-10
OK

Is it a remote computer or a computer running on your LAN? If it is remote, did you foreward the ports in your firewall/router?

---

### Post by Aleks67 on 2008-03-10
>If it is remote, did you foreward the ports in your firewall/router?

Yes it is a remote server. As it is the server that is refusing the connection do you mean firewall/router on the server?

Aleks

---

### Post by .nedberg on 2008-03-10
Yes, the server needs to have some ports forwarded to it.

VNC works at port 5800+display and 5900+display. If you connect to display :1 you need ports 5801 and 5901 open. Installing vnc4server takes care of the firewall on the Ubuntu server, but if it is behind a router, the router needs to be set up as well.

Be aware that VNC is not a secure protocol and is not recommended outside LAN.

---

### Post by Aleks67 on 2008-03-10
>...the server needs to have some ports forwarded to it.

Thank you, how do I do that?

Aleks

---

### Post by .nedberg on 2008-03-10
Have a look [here]("http://portforward.com/")!

You need the make of your router. I don't think this can be done remotely...

---

### Post by Aleks67 on 2008-03-10
.nedburg thank you so much for taking the time to help me during the day. I appreciate it and wish you all the best for the future.

Regards.

Aleks

---

### Post by .nedberg on 2008-03-10
No problem! Just glad I could help!

---

### Post by BlizzofOZ on 2008-03-19
> **Aleks67 said:**
> Ok did that and then brought up VNC Free Edition Viewer for Windows Version 4.1.2 on my PC.

I entered my IP address xxx.xxx.xxx.xx and got the message:

unable to connect to host: Connection refused (10061)

Aleks

I have the same situation, except I'm trying to connect VNC within the LAN... and getting the same type of 10061 error.

I don't have any ports forwared as this within the LAN and not trying access from outside.

Any what I might be able to look at to help determine my problem?

---

### Post by .nedberg on 2008-03-20
> **BlizzofOZ said:**
> I have the same situation, except I'm trying to connect VNC within the LAN... and getting the same type of 10061 error.

I don't have any ports forwared as this within the LAN and not trying access from outside.

Any what I might be able to look at to help determine my problem?

Have you started the vnc4server? Have you set a password with vncpasswd?

---

