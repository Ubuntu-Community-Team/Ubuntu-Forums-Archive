---
title: "shell scrip / batch file - ifconfig"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by rv2internet on 2007-08-08
Howdy, I'm very new to Ubuntu and loving ever minute of it.

I am running into one little problem...I don't get "ifconfig"

"ifconfig -?"makes not sense to me...and I end up mousing up to the Ethernet adapter to switch from DHCP to a static IP address...and this wouldn't be a big thing except I have to do it about 5x a hour (programming new hardware systems).

Can  a shell script (batch):
set adapter to IP address 192.168.1.200/255.255.255.0
point Firefox to IP address 192.168.1.20

**Pause** while I upload firmware in the user interface...

set adapter to IP address 192.100.1.200/255.255.255.0
point Firefox to "http://www.random.org/dice/?num=6" for 5 seconds
point Firefox to 192.100.1.20
stop

---

### Post by Cypher on 2007-08-09
Pul the following in a file
```

#!/bin/sh

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.200 netmask 255.255.255.0 up
firefox-bin http://192.168.1.20 &
echo "Going to wait now.."
read KEY
sudo ifconfig eth0 down
sudo ifconfig et0 192.100.1.200 netmask 255.255.255.0 up
firefox-bin http://www.random.com/dice/?num=6 &
echo -n "Waiting for 5 seconds"
for i in `seq 5`; do echo -n "."; sleep 1; done
echo
killall firefox-bin
firefox-bin http://192.100.1.20 &
echo "We're done"
exit 0

```

I'm assuming that you only have one Ethernet inteface and it's called "eth0". If that isn't the case, you can change it whatever "ifconfig" reports.

Also, after you start the script, the first Firefox winodw that appears will  have to be closed by you, then hit any key to continue the script and allow it to do the rest of the work.

Save this script where you can access it and do
```

chmod 755 <script-name>

```

Execute and enjoy..

---

### Post by rv2internet on 2007-08-09
```

#!/bin/sh

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.200 netmask 255.255.255.0 up
firefox -bin http://192.168.1.20 &
echo "Going to wait now.."
read KEY
sudo ifconfig eth0 down
sudo ifconfig eth0 192.100.1.200 netmask 255.255.255.0 up
firefox -bin http://www.random.com/dice/?num=6 &
echo -n "Waiting for 5 seconds"
for i in `seq 5`; do echo -n "."; sleep 1; done
echo
killall firefox -bin
firefox -bin http://192.100.1.20 &
echo "We're done"
exit 0

```

AWESOME!!!!!

Yes, I do only have one Ethernet interface and it is called "eth0".

I copied the script to gedit, saved the script as BATCH on the desktop. Opened terminal confirmed BATCH was in the current directory and typed:
```

chmod 755 BATCH

```
I got nothing...it just sat there...

So I tried some of the commands individually and got a few to work and fixed a few...still...I don't know the principle of operation behind these commands...

Example, should I be able to see the commands being executed? I don't see them "running" like I would old batch files...

P.S. I made a mistake...instead of setting to static second time need an address from the newly installed DHCP service...what's the "ifconfig" equivalent of: ```
ipconfig /renew
```

My wrists THANK you a million times!!! Changing DHCP to static over and over is KILLING me...

---

### Post by asmoore82 on 2007-08-09
you have to tell chmod/any program where the file is unless it is in your Current Working Directory.
if you have just opened a term, your CWD is your home and Desktop is in there ...

```
~ $ chmod 755 Desktop/BATCH
```

to set eth0 back to dhcp and bring it up ...

```
~ $ ifconfig eth0 dhcp up
```

---

### Post by rv2internet on 2007-08-09
I went into terminal and ran:

```

reuben@Open-Src-desktop:~$ sudo ifconfig eth0 dhcp up
Password:
dhcp: Unknown host
ifconfig: `--help' gives usage information.
reuben@Open-Src-desktop:~$

```

Also the file was in the Current Working Directory just like your command. (tried every variation anyways).

What bothers me is that I'm not being prompted for a password on the "batch" script. When I run the command separately, I am prompted for the system password (as seen above when attempting DHCP).

---

### Post by jkeyes0 on 2007-08-09
> **rv2internet said:**
> I went into terminal and ran:

```

reuben@Open-Src-desktop:~$ sudo ifconfig eth0 dhcp up
Password:
dhcp: Unknown host
ifconfig: `--help' gives usage information.
reuben@Open-Src-desktop:~$

```

Also the file was in the Current Working Directory just like your command. (tried every variation anyways).

What bothers me is that I'm not being prompted for a password on the "batch" script. When I run the command separately, I am prompted for the system password (as seen above when attempting DHCP).

When I've done this before, I use 
```
sudo dhclient eth0
```
for DHCP.

---

### Post by asmoore82 on 2007-08-09
sorry, my ifconfig-ing is not up to par on changing configs.
:shock: I should just stick to up/down :lol:

---

### Post by rv2internet on 2007-08-09
```

sudo dhclient eth0

```

"dhclient" works like a charm! thank you!

Now the ten million dollar question in how to wrap it into a shell script...

Call me crazy...but shouldn't I put a suffix on the file name...or something in the file aside from:

```
#!/bin/sh
```

---

### Post by asmoore82 on 2007-08-09
this i do know about ...

the only thing you need is to set the execute permissions with the chmod utitlity.

these permissions are the only thing that keeps the system from trying to load a command
interpreter for and "execute" any other text file. the "#!/bin/sh' bit tells it which command interpreter to load.

suffixes or extensions mean absolutely nothing to the core OS, but they may case GUI hiccups sometimes.

the 'file' command will tell you lots of great info and does NOT look at extensions.

```
asmoore@asmoore-laptop:~$ file resume.pdf 
resume.pdf: PDF document, version 1.2
asmoore@asmoore-laptop:~$ file iso/ubuntu-7.04-desktop-powerpc.iso 
iso/ubuntu-7.04-desktop-powerpc.iso: ISO 9660 CD-ROM filesystem data UDF filesystem data (unknown version, id 'NSR0
asmoore@asmoore-laptop:~$ file Apps/frostwire-4.13.2.i586.deb 
Apps/frostwire-4.13.2.i586.deb: Debian binary package (format 2.0)
asmoore@asmoore-laptop:~$ file Apps/Firefox\ Setup\ 2.0.0.6.exe 
Apps/Firefox Setup 2.0.0.6.exe: MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit
asmoore@asmoore-laptop:~$ file run.bash
run.bash: Bourne-Again shell script text executable
asmoore@asmoore-laptop:~$ mv run.bash run
asmoore@asmoore-laptop:~$ file run
run: Bourne-Again shell script text executable
```

file has Super Penguin Powers ...

```
asmoore@asmoore-laptop:~$ sudo dd bs=512 count=1 if=/dev/sda of=sda.txt
1+0 records in
1+0 records out
512 bytes (512 B) copied, 7.5429e-05 seconds, 6.8 MB/s
asmoore@asmoore-laptop:~$ file sda.txt 
sda.txt: x86 boot sector; partition 1: ID=0x7, active, starthead 1, startsector 63, 39311937 sectors; partition 2: ID=0x83, starthead 254, startsector 39327120, 114864750 sectors; partition 3: ID=0x82, starthead 254, startsector 154191870, 2104515 sectors, code offset 0x48
asmoore@asmoore-laptop:~$ sudo rm sda.txt
```

---

### Post by rv2internet on 2007-08-09
Ok smarty pants...

```
reuben@Open-Src-desktop:~$ file batch2
batch2: Bourne shell script text executable
reuben@Open-Src-desktop:~$ 
```

That's what I get back from 'file'

how do I execute my fancy script?... :D

(You guys are awesome...love this forum!!!)

---

### Post by rv2internet on 2007-08-11
So is the ```
#!/bin/sh
```

Not working because changing the network adapter settings is an administrator password level function?

---

