---
title: "chkrootkit results analysis help please"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Biggus on 2006-11-23
Hi chaps, I've just read about a super little tool with this Ubuntu called chkrootkit.

I've ran it through a terminal, and all looked to be super duper, until the last few lines of output, which have cause me some concern.

> Checking `asp'... not infected
**Checking `bindshell'... INFECTED (PORTS:  1524 31337)**
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
[b]Checking `sniffer'... lo: PACKET SNIFFER(/usr/sbin/pmacctd[4658])
eth1: PACKET SNIFFER(/sbin/dhclient3[3392])[/b]
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... user root deleted or never logged from lastlog!


Now, I should explain that I wouldn't recognise a 'bindshell' if it stopped me in the street. I do however recognise that something with a port number of 31337 is potentially not very nice at all.

The other concerning result, the 'sniffer' one, leads me to believe that there is possibly some app on my machine which is monitoring my traffic?

Many thanks to anyone who could provide any assistance or thoughts at all.

---

### Post by astoltz on 2006-11-23
I don't want to jump to any conclusions as chkrootkit is notorious for giving false positives; but these look like the real thing.  A quick google search for bindshell reveals some bad things.  And pmacctd looks like a ligit Ubuntu package but it is definitely a packet sniffer.

I'd try removing both via apt-get and see what happens.  I'd also start to think seriously about wiping the hard drive and re-installing.  Sorry.

---

### Post by astoltz on 2006-11-23
OK, I did some more looking around and it seems there are some cases of chkrootkit reporting false positives for bindshell.  You should investigate further:  the man page for chkrootkit and google are good places to start.

---

### Post by Biggus on 2006-11-25
Yeah, its a bit of a conundrum, to be honest.

A lot of the other Linux forums reckon that this result is the result of running another little application named 'port sentry' (I think that Klaxon might also be an alternative name for it).

The problem is, I can't ever recall running an application named 'port sentry' at any time previous.

I don't suppose anyone happens to know if

a) 'Port Sentry' is installed as standard with 6.10 from live CD

and if so

b) How could I 'turn it off' temporarily in order to run chkrootkit.

> And pmacctd looks like a ligit Ubuntu package but it is definitely a packet sniffer.

Ah, errr, yes, I can explain...... You see, one of the reasons I installed Ubuntu was to find out a little bit more about network security. Consequently, I've downloaded from the 'Synaptic Package Manager' quite a number of security related applications, one of which might well be a packet sniffer (Wireshark is the main one which springs into mind) but I don't recall ever downloading one called anything liike 'pmacctd'. When you say 'legit', I assume you mean that, like most of these network applications it has a legitimate use, as well as nefarious purposes?

Oh, and I didn't get much joy with removing the application

> dave@dave:~$ sudo apt-get remove pmacctd
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pmacctd
dave@dave:~$ 

---

### Post by drphilngood on 2006-11-25
IIWY, I´d install rkhunter from the repos and check with it.

```
sudo aptitude install rkhunter
```

After it´s installed run:

```
sudo rkhunter --update
```

and then:

```
sudo rkhunter --checkall
```

---

### Post by Biggus on 2006-11-25
Wow! That's quite some output.

I'll spare you the gory details, most of it showed up as OK.

> * Filesystem checks
   Checking /dev for suspicious files... -e                      [ OK ]
   Scanning for hidden files...-e                                [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
**Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory)** 


> * Application version scan
   - Exim MTA 4.62 -e                                            [ Unknown ]
gpg: **WARNING: unsafe ownership on configuration file `/home/dave/.gnupg/gpg.conf'**
   - GnuPG 1.4.3 -e                                              [ Unknown ]
   - OpenSSL 0.9.8b -e                                           [ Unknown ]


> Security advisories
* Check: Groups and Accounts
   Searching for /etc/passwd... -e                               [ Found ]
   Checking users with UID '0' (root)... -e                      **[ Warning! (some users in root group)** ]
    info: dave:1000


The user in the root group, I take it is myself. The other two warnings, I'm not so sure about, so I shall go and investigate them further.

---

### Post by drphilngood on 2006-11-26
Im no expert but it appears from the last output that you may have been compromised.  I would either follow up on this with with someone very familiar with linux security or write zeroes to the drive and reinstall.
Once again, I am no expert.  I am just telling you what I would do if in your circumstances.
Good luck!

---

### Post by bodhi.zazen on 2006-11-26
> **drphilngood said:**
> Im no expert but it appears that you may have been compromised.  I would either follow up on this with with someone very familiar with linux security or write zeroes to the drive and reinstall.
Once again, I am no expert.  I am just telling you what I would do if in your circumstances.
Good luck!

I agree. Only root should have a uid = 0

---

### Post by Biggus on 2006-11-27
Hmmm, most disheartening news chaps.

I'm actually going to just see if I can work this one out, before taking such drastic action as wiping my hard drive.

One thing which has came to my attention during my investigation is that every linux box contains a file called passwd in the /etc/ directory. Now then, I've just checked my own /etc/ directory, and I've detected an extra little file called 'passwd-', which doesn't appear to show up on any search engine, (I think the addition of the minus symbol throws off most search engines) and to which I don't have access.

The actual contents of the 'real' passwd file in /etc/ is

> 
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:107::/var/run/dbus:/bin/false
avahi:x:104:108:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
cupsys:x:105:109::/home/cupsys:/bin/false
haldaemon:x:106:110:Hardware abstraction layer,,,:/var/run/hal:/bin/false
hplip:x:107:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:108:113:Gnome Display Manager:/var/lib/gdm:/bin/false
dave:x:1000:0:Dave,,,:/home/dave:/bin/bash
privoxy:x:109:65534::/etc/privoxy:/bin/false
debian-tor:x:110:115::/var/lib/tor:/bin/bash
clamav:x:111:116::/var/lib/clamav:/bin/false
snort:x:112:117:Snort IDS:/var/log/snort:/bin/false
scanlogd:x:113:65534::/usr/lib/scanlogd:/bin/false
avg:x:1001:1001::/home/avg:/sbin/nologin
gnump3d:x:114:65534::/var/music:/bin/false
Debian-exim:x:115:118::/var/spool/exim4:/bin/false

I can now recall 'installing' tor + privoxy, but a lot of the other stuff is new to me.

I've got a linux boffin coming over this evening, so I shall enquire unto them as to what they reckon the problem is.

---

### Post by Biggus on 2006-11-28
OK, the problem, as always, is the user.

I had, on the first day of installing ubuntu, managed to change my own users 'group' to that of 'root', using a little application called 'User accounts Admin'.

(If I recall correctly, I was trying to open a file with gedit, which said I didn't have permission to open it, so I changed my 'group' to 'root', and that seemed to solve the problem)

I've now changed it back, but running

> sudo rkhunter --checkall

again now throws up another problem, namely

> System checks
* Allround tests

**Checking for differences in user accounts... Found differences**

I'm not sure if this simply refers to my changing the 'group' of a user since the last time I ran a scan or not, but I shall investigate further anyway.

Any comments more than welcome.

---

### Post by Foudre on 2006-11-28
umm of course there is no root last login in logged, or eithers its deleted ubununtu doesn't set up a root,. of course i did skim past most of the other post i just like read the 1st and 2nd but there shouldn't be a last root login

---

### Post by Biggus on 2006-11-28
OK, I ran > sudo rkhunter --checkall again, and its came up as OK.

I'm down to just a couple of little problems now, and then I shall have convinced myself that

a) it's a false positive

and

b) I should stop messing around with things I don't yet understand

> * Filesystem checks
   Checking /dev for suspicious files... -e                      [ OK ]
   Scanning for hidden files...-e                                [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory) 

I'm not quite certain why, but it's still insisting that I inspect these files, so I shall have to go and think about what they do, and why " /dev/.static" has a space at the start of it.

> * Application version scan
   - Exim MTA 4.62 -e                                            [ Unknown ]
gpg: WARNING: unsafe ownership on configuration file `/home/dave/.gnupg/gpg.conf'
   - GnuPG 1.4.3 -e                                              [ Unknown ]


I've checked the above file, and it shows me (as user 'dave' in group 'dave') having read and write access to the file, and the 'root' and 'others' groups as having no access. I can't think why that should be unsafe, so that is something else for me to find out about.

---

