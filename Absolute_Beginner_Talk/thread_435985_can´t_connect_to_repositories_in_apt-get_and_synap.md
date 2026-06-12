---
title: "can´t connect to repositories in apt-get and synaptic"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-05-07
i have internet working, i can surf the web, i can ping the servers from the repositories, but if i try to download anything from apt-get or synaptic, it can´t connect to the repositories.

Anyone?

---

### Post by taurus on 2007-05-07
Any chance you have proxy running or on?

What's the output of these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Cypher on 2007-05-07
Please show us your /etc/apt/sources.list file.

---

### Post by Pulka on 2007-05-07
> **taurus said:**
> Any chance you have proxy running or on?

not that i know off

> **taurus said:**
> What's the output of these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

it trys to connect and then timesout

---

### Post by Pulka on 2007-05-07
> **Cypher said:**
> Please show us your /etc/apt/sources.list file.


## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

---

### Post by taurus on 2007-05-07
Can you post the whole error message?

---

### Post by Cypher on 2007-05-07
..and also can you show us the output of 
```

ping archive.ubuntu.com

```

---

### Post by EXCiD3 on 2007-05-07
<snipped>

---

### Post by Pulka on 2007-05-07
> **EXCiD3 said:**
> You = n00b


thank you, that was very helpfull. U can sleep tight now that you had your fun

---

### Post by Cypher on 2007-05-07
> **EXCiD3 said:**
> You = n00b
And you are how old?

---

### Post by Pulka on 2007-05-07
> **Cypher said:**
> ..and also can you show us the output of 
```

ping archive.ubuntu.com

```


ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.89.8) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (91.189.89.8): icmp_seq=1 ttl=52 time=161 ms
64 bytes from archive.ubuntu.com (91.189.89.8): icmp_seq=2 ttl=52 time=162 ms
64 bytes from archive.ubuntu.com (91.189.89.8): icmp_seq=3 ttl=52 time=162 ms
64 bytes from archive.ubuntu.com (91.189.89.8): icmp_seq=4 ttl=52 time=163 ms
64 bytes from archive.ubuntu.com (91.189.89.8): icmp_seq=5 ttl=52 time=161 ms

---

### Post by Pulka on 2007-05-07
> **taurus said:**
> Any chance you have proxy running or on?

What's the output of these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```


 sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US        
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg                               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg                    
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US                
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages                             
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release [34.7kB]                           
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages                         
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources                              
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources                          
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages                             
  404 Not Found
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release [38.4kB]                  
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages                         
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources                              
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources                          
  404 Not Found
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [38.4kB]                   
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [44.6kB]                 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]                  
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]               
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]               
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages [126kB]               
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [274kB]                      
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources [1436B]                
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1068kB]                 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources [45.0kB]               
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages [88.0kB]           
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages [14B]        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages [31.4kB]       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages [3084B]      
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [81.1kB]            
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]         
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages [23.8kB]        
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages [14B]         
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [24.2kB]            
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]          
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources [4694B] 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources [14B]          
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [17.8kB]          
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]       
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [40.1kB]     
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [6087B]     
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources [5571B]            
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources [14B]        
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources [14.4kB]       
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources [2382B]      
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Fetched 6519kB in 10m0s (10.9kB/s)               
Reading package lists... Done




sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Pulka on 2007-05-07
can't connect gaim also. So far, only firefox can connect to internet

---

### Post by bapoumba on 2007-05-07
Please check:
/etc/environment
.bashrc
/etc/apt/apt.conf

for some kind of proxy settings.
Something with your ISP? Your modem/router ?

---

### Post by John.Michael.Kane on 2007-05-07
Try copy pasting this sources.list over your current one. 

Run: ```
gksudo /etc/apt/sources.list  
```

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse


```

Then run ```
gksudo aptitude update
```

---

### Post by John.Michael.Kane on 2007-05-07
> **Pulka said:**
> can't connect gaim also. So far, only firefox can connect to internet

As for the gaim issue what service are wre you trying to connect too eg: msn aim jabber?

---

### Post by Pulka on 2007-05-07
> **bapoumba said:**
> Please check:
/etc/environment
.bashrc
/etc/apt/apt.conf

for some kind of proxy settings.
Something with your ISP? Your modem/router ?


 environment
bash: environment: command not found
 gedit environment
 .bashrc
bash: .bashrc: command not found
 sudo gedit /etc/apt/apt.conf
 sudo /etc/apt/apt.conf
sudo: /etc/apt/apt.conf: command not found
 gedit .bashrc


i don't know if it was this you were asking.
I have been searching in the forum for a few hours, and i'm amazed with the amount of people that seem to have the same problem. Aparently is an Edgy problem.
Someone has said that it might be some kind of blocking in the system to all protocols exept http

in windows everything works just fine. I don't have any proxy configuration. I don't know if it&#347; relevant, but to have internet, i had to disconnect ipv6

---

### Post by Pulka on 2007-05-07
> **SD-Plissken said:**
> As for the gaim issue what service are wre you trying to connect too eg: msn aim jabber?

jabber

---

### Post by Pulka on 2007-05-07
> **SD-Plissken said:**
> Try copy pasting this sources.list over your current one. 

Run: ```
gksudo /etc/apt/sources.list  
```

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
```

Then run ```
gksudo aptitude update
```

that's for feisty though, i'm using edgy

---

### Post by John.Michael.Kane on 2007-05-07
> **Pulka said:**
> that's for feisty though, i'm using edgy

I updated the post with a minimal edgy sources.list.

---

### Post by Pulka on 2007-05-07
sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c




and stays like this

---

### Post by bapoumba on 2007-05-07
> **bapoumba said:**
> Please check:
/etc/environment
.bashrc
/etc/apt/apt.conf

for some kind of proxy settings.
Something with your ISP? Your modem/router ?
Sorry, do what SD has recommended, and run the update.

What I asked you was:
```
cat /etc/environment
cat .bashrc
cat /etc/apt/apt.conf

```
and look in the output, or paste it in here, for any proxy or unusual set ups.

---

### Post by Pulka on 2007-05-07
**gksudo aptitude update**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c


**cat /etc/environment**
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"

**cat .bashrc**

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi



**cat /etc/apt/apt.conf**
cat: /etc/apt/apt.conf: No such file or directory

---

### Post by bapoumba on 2007-05-07
A DNS problem ?
**cat /etc/resolv.conf**

---

### Post by Pulka on 2007-05-07
> **bapoumba said:**
> A DNS problem ?
**cat /etc/resolv.conf**

cat /etc/resolv.conf
nameserver 192.168.1.1

---

### Post by Rui Pais on 2007-05-07
a 1.0.0.0 it's a dns problem. 
(it happens with some routers, usually D-Link, but not only.)

Try this :
[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)



Edit: alternatively, if you wont' want to use the openDNS ones, you can open your router configuration window (on a browser) and check which dns servers are listed there and use those.

---

### Post by Pulka on 2007-05-07
Worked!!!!

DNS problem

tinha de ser um tuga a resolver :)

---

### Post by Rui Pais on 2007-05-07
> **Pulka said:**
> Worked!!!!

DNS problem

tinha de ser um tuga a resolver :)

:p 
(fico contente por estar resolvido)


The working internet but failing apt-get with 10.0.0.0 it's a classic that appears on the forums once in a while.

Someone should make one of those thread a sticky. Or made a main thread with a warning on Network forum  (or Beginner Talk...)

---

### Post by bapoumba on 2007-05-07
Why not a nice tutorial we could link to ?
Thanks Rui Pais ^^

---

### Post by Rui Pais on 2007-05-07
Well, thats a twisted case because the focus on that issue is specific symptoms more then the solution that it's very simple to implement.

The solution could be almost a copy past from or a link to openDNS and alternatively a more detailed version on how to find the DNS information on the router configuration window.

If you want, i'll do a thread with a mini-howto (very mini ;))

---

### Post by bapoumba on 2007-05-07
Can "Connecting to archive.ubuntu.com (1.0.0.0)" be something else ? I know, I have not done my homework).

---

### Post by Rui Pais on 2007-05-07
> **bapoumba said:**
> Can "Connecting to archive.ubuntu.com (1.0.0.0)" be something else ? I know, I have not done my homework).

as far as i know, references to 10.0.0.0 on updating repos (and ping some sites using the url) in conjugation with a working internet (i mean, user can browse the web) is always a router specific issue related with dns.

It's late here and i'm very tired (i had a very long day) but tomorrow i'll try to find some links to the subject...
It's a weird issue, 'cause it's directly related with the router, and apparently with some specific labels, but it happens only on Linux (the same machine with same router on Windows work normally)

If i'm not mistaken i have read some good (and more technical) explanation here on this forums... 
i'll try to search tomorrow.

good night.

---

### Post by bapoumba on 2007-05-07
Good night Rui Pais. ANd thanks. Getting late here too :)

---

### Post by Rui Pais on 2007-05-11
hi,
sorry this time without posting (terrible days, this last ones...)

I've been trying to find a thread where someone explained very clearly the issue with a good technical basis, but can't find it... Anyway here some "references":

1st a Launchpad entry with this issue (discover that tonight, i should have checked for one before):
[https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057)

a good discussion on the hardware "part" of the problem, on mepis forum:
[http://www.mepis.org/node/10306](http://www.mepis.org/node/10306)

random threads on Ubuntu forum with this:
[http://ubuntuforums.org/showthread.php?t=77889](http://ubuntuforums.org/showthread.php?t=77889)
[http://ubuntuforums.org/showthread.php?p=2192861](http://ubuntuforums.org/showthread.php?p=2192861)
[http://ubuntuforums.org/showthread.php?p=2049586](http://ubuntuforums.org/showthread.php?p=2049586)
[http://www.ubuntux.org/problem-synaptic-update-manager-could-not-download-all-repository-indexes](http://www.ubuntux.org/problem-synaptic-update-manager-could-not-download-all-repository-indexes)

[here a recent one]("http://ubuntuforums.org/showthread.php?p=2620291")... i will point the OP to 
this one, hope that will solve his/her problem.

i'll post with more if i found anything interesting or more relevant.

Good night.

---

### Post by ShirishAg75 on 2007-05-12
Just to add I have a D-Link 502T which runs busybox.

---

