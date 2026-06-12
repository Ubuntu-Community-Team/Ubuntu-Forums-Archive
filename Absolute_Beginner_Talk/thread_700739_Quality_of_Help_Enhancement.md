---
title: "Quality of Help Enhancement"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by jan quark on 2008-02-18
[CENTER]**:confused:.................................. :shock: .................:-k ............................. :arrow:........ [COLOR="DarkOrange"]Ubuntuforums [/COLOR]..........................\\:D/**[/CENTER]
[B][CENTER]
[SIZE="3"]Quality of Help Enhancement[/SIZE][/CENTER][/B]

*[CENTER]some thoughts for helpers and the users seeking help[/CENTER]*

After reading some (quite a lot of threads) in this Absolute Beginners Section I realize there are two sorts of threads.

[LIST=1]
[*]Recurring Issues
[*]Unique Issues
[/LIST]

The unique issues must be read as if it were your first day in the Linux World. You must forget every standard procedure and search for new ways, start being creative. Ask intelligent new questions which will guide the new user and also you as the helper to the core of the problem. The Unique Issues are the threads which will bring you knowledge to a higher level. Because when you stand still, not moving, only copy this paste that, your brain also makes a break. Sometimes it is very relaxing. But it should not become your target state.

But there are also the Recurring Issues. Issues which are well known by the helpers which spent some time in this forum. This is the salient point of this thread. As the seeker of help start your thread with some input, so we can suggest a solution based on facts not on stories.

Also use a descriptive title for your new thread. "Help me, I am a new user, and hit the wall" is bad. "Wireless Broadcom 4311 Connectivity Issue" is good.

Another important point is that I do not want to write a guide how to solve every problem. I just want to stress the importance of being as exact as possible without to degenerate to a robot.

Please feel free to add your advices and suggestions, your important and recurring starting commands, your first ideas.

I hope this small thread will help to improve the great service this forums offers. I do not want to make the help unspiritual and static. But sometimes some input at the beginning would be nice...


[CENTER][B]
Help us to help you[/B][/CENTER]
[U][I][CENTER]
_Network Issues_[/CENTER][/I][/U]

Please post the output of these terminal commands to shed some light on your current network status.

```
iwconfig
```
```

ifconfig
```

```
sudo iwlist scan
```
```

cat /etc/network/interfaces
```


*_[CENTER][U]Mounting Issues_[/CENTER][/U]*

Please post the output of these terminal commands to detect the current partition situation:

```
mount
```
```

sudo fdisk -l
```
```

cat /etc/fstab
```

[CENTER]*_Graphical Issues_*[/CENTER]

and also other issues somehow linked with hardware. We have to know your hardware to help.
What driver do you have installed? Are you running Compiz ? Do you have installed some unusual applications in the past days? Are you dual-booting? 

```

lspci
```
```

lsusb
```
```

sudo lshw
```

```
cat /etc/X11/xorg.conf
```

to test your card and show info run this
```

glxgears -info
```

Reconfigure the Xserver automatically:
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

Restarting GNOME
```
sudo /etc/init.d/gdm restart
```

[CENTER]*_Application Installation Issues_*[/CENTER]

```
sudo apt-get update

sudo apt-get upgrade
```

```
cat /etc/apt/sources.list
```
for fixing broken packages
```
sudo apt-get -f install
```
```

sudo dpkg --configure -a
```
[CENTER][I][U]
Other useful Terminal Commands

[/U][/I][/CENTER]

Navigating in Terminal

for changing the directory
```
cd
```

for listing all files and folders in the current directory
```
ls
```

You can use the TAB-key to automatically finish a long filename. For instance a file is named asadkjfnaskfnas.deb. Just type cd asa and press tab to auto-complete the file name.

List Command

for additional help on the list command run
```
ls --help
```



list permissions in the current folder
```
ls -l
```


Show free space in memory, cache and swap
```
free
```

Show cpu usage, tasks running, memory and swap
```
top
```

---

### Post by Joeb454 on 2008-02-18
Nice guide **jan quark** +1 for a sticky in the ABT Forum

---

### Post by paultag on 2008-02-18
Awesome List!

Some other ones:

Check Mounted Drives
```

df -h

```

Find process IDs and how many processes are running

```

ps -ef | grep -v grep | grep <process name>

```


Cheers,
Tag

---

