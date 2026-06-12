---
title: "installing JRE"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by someone447 on 2005-06-26
I am having trouble installing the Java Runtime Enviroment.  I want to be able to us Azereus but I need JRE.  I have the bin downloaded.  Now I just need to install it, so if anyone can give me a step by step on how to do it, it would be greatly appreciated.

---

### Post by SGC on 2005-06-26
It is easier to install azureus and jre using apt-get or synaptic, just follow this instructions:
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)
[http://ubuntuguide.org/#azureus](http://ubuntuguide.org/#azureus)

---

### Post by someone447 on 2005-06-26
ive been trying that also but i keep getting this 
[B]name@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5[/B]

also, whenever i enter synaptic I get this message

[B]W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-amd64_Packages) - stat (2 No such file or directory)[/B]  

I do not know how I am supposed to fix either of those.

---

### Post by codejunkie on 2005-06-26
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) this should help you get the repositories fixed, and you can install java by following the guide at [www.ubuntuguide.org](www.ubuntuguide.org). 
To Manually install Java Download the Linux (self-extracting file) at [http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp) open a terminal and follow these steps to manually install java.
```

$ cd to where you downloaded the jre-1_5_0_04-linux-i586.bin file.
$ sh jre-1_5_0_04-linux-i586.bin
$ sudo mkdir /usr/java
$ sudo mv jre1.5.0_04/ /usr/java/
$ sudo chown -R root:root /usr/java/jre1.5.0_04/
$ sudo ln -s /usr/java/jre1.5.0_04/bin/java /usr/bin/java
$ sudo ln -s /usr/java/jre1.5.0_04/bin/java_vm /usr/bin/java_vm
$ sudo cp /etc/bash.bashrc /etc/bash.bashrc_backup
$ sudo gedit /etc/bash.bashrc

add the following lines at the end of the bash.bashrc file

JAVA_HOME=/usr/java/jre1.5.0_04
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

```
```

example: /etc/bash.bashrc file

# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
    ;;
*)
    ;;
esac

JAVA_HOME=/usr/java/jre1.5.0_04
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

```
now test java with 

java -version

it should output something like

java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b09)
Java HotSpot(TM) Client VM (build 1.5.0_04-b09, mixed mode, sharing)

now install the java plugins for mozilla and mozilla firefox with 
```

$ sudo ln -s /usr/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
$ sudo ln -s /usr/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

```
restart any open web browser
and java is installed.

---

### Post by Kvark on 2005-06-26
Do that [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) thingy, I did and after that it was very easy to install JRE plus a number of other things from synaptic.

---

### Post by j0ma2 on 2005-06-26
[QUOTE=codejunkie]now test java with 

java -version

it should output something like

java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b09)
Java HotSpot(TM) Client VM (build 1.5.0_04-b09, mixed mode, sharing)
[/QUOTE]

Hi,

I was using Java (Azureus was working perfectly), but the Firefox plug-in did not work. I have re-installed Java with your guide (many thanks :) ) and this is what I get now:

java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) Client VM (build 1.5.0_03-b07, mixed mode, sharing)

The strange think is that I have reinstalled from "jre-1_5_0_04-linux-i586.bin", so versions (downloaded and installed) do not match :-/

Anyhow, the Firefox plug-in nows work (and Azareus too).

---

### Post by someone447 on 2005-06-26
when i do java -version i get this
[B]SableVM version 1.1.8
- compile date and time: 2005-01-01 19:42:12 UTC
- gcc version: 3.3.5 (Debian 1:3.3.5-5)
- 'real life brokenness' features enabled
- copying garbage collection
- bidirectional object layout
- direct-threaded interpreter[/B]

my synaptic doesn't have a lot of the stuff I want in it, like azureus, or java.  I have added the extra repositories, but to no avail.

---

### Post by Kvark on 2005-06-26
[QUOTE=someone447]my synaptic doesn't have a lot of the stuff I want in it, like azureus, or java.  I have added the extra repositories, but to no avail.[/QUOTE]

If you added the extra repositories then sun's java is there, the package is called "JRE".

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=someone447]
my synaptic doesn't have a lot of the stuff I want in it, like azureus, or java.  I have added the extra repositories, but to no avail.[/QUOTE]


Are you using the 64 bit version? The 64 bit version is for experianced users only....its lacks codecs and easy to install Java.

---

### Post by someone447 on 2005-06-26
UGH, yes I am using the 64bit.  Meh, I guess ill just have to learn, at least I am dual booting, so I can do stuff in windows still while im learning.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=someone447]UGH, yes I am using the 64bit.  Meh, I guess ill just have to learn, at least I am dual booting, so I can do stuff in windows still while im learning.[/QUOTE]


There is a way to fix this in the 64 bit version:

[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot)

Basically you run a 32 bit version inside the 64 bit version. This is kinda the bar...aka "you must be this nerdy to ride 64 bit Ubuntu."

---

