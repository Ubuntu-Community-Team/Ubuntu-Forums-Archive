---
title: "SWAT does not run."
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-03-27
Hi,

Just installed Samba and swat via, apt-get install. On my old p3 with lamp and DNS options enabled (didnt know what each did, so i just said yes ill have them).

i also put SSH on, and am SSH ing into the pc.

It seems however that swat does not run by itself?, and i have no idea how to fix it in UBUNTU SERVER 6.10.

All googling results in commands that are unknown in ubuntu?.

i've noticed netstat -lt does not show swat as running.

So how do i enable it?, give it to me in full, even including apt-get install samba, cause im ohh so lost :(

---

### Post by felker2 on 2007-03-27
Check out this forum [http://ubuntuforums.org/showthread.php?t=58434]("http://ubuntuforums.org/showthread.php?t=58434")


In short, install netkit-inetd doing something like this:

```
sudo apt-get install netkit-inetd
```

Then browse to [http://localhost:901/](http://localhost:901/)

HTH

---

### Post by danbopes on 2007-03-28
I have followed that link and all the directions, but when I run netstat -lt it doesn't come up that swat is listening.  I don't have any clue what I am doing wrong, but it looks like some other people are having similar issues.

---

### Post by felker2 on 2007-03-29
> **danbopes said:**
> I have followed that link and all the directions, but when I run netstat -lt it doesn't come up that swat is listening.  I don't have any clue what I am doing wrong, but it looks like some other people are having similar issues.

Swat didn't run on my machine until I installed netkit-inetd. Now it works and I indeed see swat in netstat -lt:

```
sander@kubuntu:~$ netstat -lt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:2208          *:*                     LISTEN
tcp        0      0 *:swat                  *:*                     LISTEN

```

So if you have installed 'swat' and 'netkit-inetd' (check with locate) and still [http://localhost:901/]("http://localhost:901/") doesn't work, I don't have any more tips.

---

### Post by 13ojo on 2007-03-29
installing netkit-inetd fixed it for me.

though part of me is just gonna say, forget about swat if your setting up a small network.

more worthwhile to learn the notepad route, as to get some things working, your going to have to add them into smb.conf, SWAT just didn't have the options to.

---

### Post by danbopes on 2007-03-29
> **13ojo said:**
> installing netkit-inetd fixed it for me.

though part of me is just gonna say, forget about swat if your setting up a small network.

more worthwhile to learn the notepad route, as to get some things working, your going to have to add them into smb.conf, SWAT just didn't have the options to.

I don't have a very small network, im trying to get it working with a Domain Controller among other things.  When I do locate netkit I get this:
```

/etc/cron.daily/netkit-inetd
/usr/bin/netkit-ftp
/usr/bin/telnet.netkit
/usr/share/doc/netkit-inetd
/usr/share/doc/netkit-inetd/BUGS
/usr/share/doc/netkit-inetd/changelog.Debian.gz
/usr/share/doc/netkit-inetd/changelog.gz
/usr/share/doc/netkit-inetd/copyright
/usr/share/doc/netkit-inetd/README
/usr/share/man/man1/netkit-ftp.1.gz
/usr/share/man/man1/telnet.netkit.1.gz
/var/cache/apt/archives/netkit-inetd_0.10-10.2ubuntu1_i386.deb
/var/lib/dpkg/info/netkit-inetd.conffiles
/var/lib/dpkg/info/netkit-inetd.config
/var/lib/dpkg/info/netkit-inetd.list
/var/lib/dpkg/info/netkit-inetd.md5sums
/var/lib/dpkg/info/netkit-inetd.postinst
/var/lib/dpkg/info/netkit-inetd.postrm
/var/lib/dpkg/info/netkit-inetd.preinst
/var/lib/dpkg/info/netkit-inetd.prerm
/var/lib/dpkg/info/netkit-inetd.templates

```
I know I did install it through apt-get, but here is my netstat -lt:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:ldap                  *:*                     LISTEN
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:ftp                   *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp6       0      0 *:ldap                  *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN

```
Still don't know exactly what to do.  Is there anything I have to start or run for the netkit?

---

### Post by danbopes on 2007-03-29
This is really starting to piss me off.  Can anyone help me out?

---

### Post by danbopes on 2007-03-29
I just looked in the swat log file and found this:
```

[2007/03/28 01:47:39, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/03/28 01:47:40, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

```
Could this be the problem, and if so how do I fix it?

---

### Post by jacksonz123z on 2007-04-09
SWAT works on my laptop (Feisty) using the netkit fix, however on the desktop (Feisty)  I have to use xinetd as explained in [https://help.ubuntu.com/community/Swat?highlight=%28swat%29](https://help.ubuntu.com/community/Swat?highlight=%28swat%29) .   Now both work well, but why the difference??:confused:

---

### Post by 13ojo on 2007-04-12
danpobes,

how much are you expecting to share?/ change the file.

because swat doesn't seem to list everything, eg. i couldnt get swat to share a folder without asking for logins, so everytime ive used swat, i've had to edit it by hand anyway.

ps. what are you running? im running ubuntu 6.10 server with LAMP, maybe you don't have apache2 setup correctly?. (im a complete noob with ur problem, so taking stabs in dark)

---

### Post by ronald_stall on 2007-04-12
I was having the same problem but I followed jacksonz123z suggestion and it worked perfectly.

[https://help.ubuntu.com/community/Sw...ght=%28swat%29]("https://help.ubuntu.com/community/Sw...ght=%28swat%29")

---

