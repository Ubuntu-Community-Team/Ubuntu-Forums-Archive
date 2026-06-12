---
title: "Vmware Broken at the Worst time"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by xxrealmsxx on 2006-06-15
I did some updates that ubuntu asked me to do and now Vmware wont work, when I click on the icon nothing comes up and when I run it in console i get this: 

[I]jamiewitter@jamiewitter-laptop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

jamiewitter@jamiewitter-laptop:~$ cd /usr
jamiewitter@jamiewitter-laptop:/usr$ cd /bin
jamiewitter@jamiewitter-laptop:/bin$ sudo vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your runningkernel? [/usr/src/linux/include]
The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
[/I]

---

### Post by bluevoodoo1 on 2006-06-15
Did you just upgrade to the newest kernel? You will need the kernel-headers that match your "uname -r" command. 

```
bluevoodoo1@ubuntu:~$ uname -r
2.6.15-25-686
```

An example...

I just upgraded to the 2.6.15-25 kernel image so I needed the following:

linux-headers-2.6.15-25
linux-headers-2.6.15-25-686

(installed with Synaptic)

then as it says run the following:
```
sudo /usr/bin/vmware-config.pl
``` hitting enter at each question and you should be fine.

---

### Post by xxrealmsxx on 2006-06-15
[QUOTE=bluevoodoo1]Did you just upgrade to the newest kernel? You will need the kernel-headers that match your "uname -r" command. 

```
bluevoodoo1@ubuntu:~$ uname -r
2.6.15-25-686
```

An example...

I just upgraded to the 2.6.15-25 kernel image so I needed the following:

linux-headers-2.6.15-25
linux-headers-2.6.15-25-686

(installed with Synaptic)

then as it says run the following:
```
sudo /usr/bin/vmware-config.pl
``` hitting enter at each question and you should be fine.[/QUOTE]


worked thanks!

---

### Post by bigken on 2006-06-16
Worked a treat cheers :D

---

### Post by someusernoob on 2006-06-16
It is realy so stupid that an update f*cks up your whole configuration. It keeps you busy and busy to solve problems. 

I had the same problem. Found out how to solve it, but it took a lot of time. It shouldnt. Why do they develop things this way? This is why people go back to Windows. I think. I wont by the way. I got the time to solve problems. But if i didnt had the time for it, i would go back to Windows right away. Install some software and it will work forever.

---

### Post by emperon on 2006-06-16
[QUOTE=someusernoob]It is realy so stupid that an update f*cks up your whole configuration. It keeps you busy and busy to solve problems. 

I had the same problem. Found out how to solve it, but it took a lot of time. It shouldnt. Why do they develop things this way? This is why people go back to Windows. I think. I wont by the way. I got the time to solve problems. But if i didnt had the time for it, i would go back to Windows right away. Install some software and it will work forever.[/QUOTE]


dude you are wrong. you are upgrading your kernel that's something huge when compared to windows world. 

Its vmware's responsibility that it should have clearly told us why It was not working. Until then It would be more user friendly for everyone I guess

---

### Post by someusernoob on 2006-06-16
Unfortunatly VMware isnt the only issue. It's just scary to press the update button, coz you never know what will break this time.

I used to use Ubuntu a few months ago, and this is excactly the reason why i dumped it. I thought, hmm, maybe if Dapper is released in June it will be more stable. But it isn't. But hey, i like Ubuntu and Linux, more then Windows even when it messes up by some update. But a lot of people wont be happy with stuff like this when they just want to email and browse the internet and have some fun.

---

### Post by xxrealmsxx on 2006-06-16
[QUOTE=someusernoob]Unfortunatly VMware isnt the only issue. It's just scary to press the update button, coz you never know what will break this time.

I used to use Ubuntu a few months ago, and this is excactly the reason why i dumped it. I thought, hmm, maybe if Dapper is released in June it will be more stable. But it isn't. But hey, i like Ubuntu and Linux, more then Windows even when it messes up by some update. But a lot of people wont be happy with stuff like this when they just want to email and browse the internet and have some fun.[/QUOTE]

I agree.

I actually installed ubuntu to be more productive, I play games in Windows too much.

Now I spend all my time learning about linux through user error.

It's just as fun

but more time is required

and my girlfriend still complains that i'm being unproductive.

---

### Post by angkor on 2006-06-16
[QUOTE=someusernoob]It's just scary to press the update button, coz you never know what will break this time.
[/QUOTE]

Don't make it worse than it is. Upgrading the kernel is about the only time things can stop working. I've been upgrading dapper through that button since march and this is the first time things stopped working.

I agree it is a shame it happens, but it's not like every update is very dangerous for your system.

---

### Post by brentoboy on 2006-06-16
I dont really ever see any issues updating -- except with third party packages (things I didnt install from the ubuntu repo's)

maybe ubuntu could work out a deal with vmware, and put the vmware player (the free version) in the repo's, so the update would update it as well.

heck, vmware workstation is a free download with an unlock code, maybe it could be in the repo's as well, and then installing it and updating it would work like a charm.

--anything you have to compile in order to install will probably have to be recompiled if you update your kernel AT ALL.  expecially something as closely tied to the OS as vmware, it has to connect to that kernel in just about every way possible.

---

### Post by Thund3rstruck on 2006-06-16
Whew...thought I lost my VMWare but your fix worked like a charm. Thanks guys!

---

### Post by Jose Catre-Vandis on 2006-06-17
vmplayer still broken here, all headers updated, config.pl works through OK, but still says its not configured properly. Any other clues?

I get this single error when compiling with config.pl

> Building modules, stage 2.
  MODPOST
Warning: could not open /tmp/vmware-config0/vmnet-only/includeCheck.h: Invalid argument      **<----<----<---**
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.


---

### Post by DavidW2 on 2006-06-17
[QUOTE=brentoboy]maybe ubuntu could work out a deal with vmware, and put the vmware player (the free version) in the repo's, so the update would update it as well.[/QUOTE]

Vmware-player is in the repos - multiverse. 

I have WinXP Home running in vmware player and did the minor kernel upgrade last night with no ill effects.  I already had the headers loaded for the previous version because I had to compile acerhk.  I wonder if that is what saved me.

---

### Post by nzgreen on 2006-06-17
[QUOTE=someusernoob]It is realy so stupid that an update f*cks up your whole configuration. It keeps you busy and busy to solve problems. 

I had the same problem. Found out how to solve it, but it took a lot of time. It shouldnt. Why do they develop things this way? This is why people go back to Windows. I think. I wont by the way. I got the time to solve problems. But if i didnt had the time for it, i would go back to Windows right away. Install some software and it will work forever.[/QUOTE]

Who are you referring to here when asking why they develop things that why?  If it's the Ubuntu devs then they have absolutely no responsibility for making sure your *unsupported* software continues to work after an upgrade.  If you want to make sure nothing breaks after upgrading stop using packages from universe, multiverse and any other repository that takes your fancy and stick to supported software.

If you are going to use software from unsupported repositories then understand the risks (breakages during upgrades) and how to mitigate them (wait a few days before applying updates, let someone else feel the pain, then search the forums).

---

### Post by nmsa on 2006-06-18
my vmware-player packages is also broken
vmnet modules is not loaded and I can't have the player service started
If I try to remove it I get errors:

```

(Reading database ... 100649 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing vmware-player-kernel-modules ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

I tryed also in many ways to remove the package, even in recovery mode, but I can't.
where do I load the module vmnet from? and how?
Thank you

Edit 1h later :
just checked again vmplayer and is working, all things are loaded and this is after I added by hand the module:
insmod /lib/modules/2.6.15-23-amd64-generic/misc/vmmon.ko

then, if I run the command from the /etc/init.d/vmware-player:
  /sbin/lsmod | awk 'BEGIN {n = "no";} {if ($1 == "'"vmmon"'") n = "yes";} END {print n;}'
yes <-- OK

if I start the player and load a vmx after is loaded and I check the modules I get:
lsmod | grep vm
vmmon                 152184  7
vmnet                  45720  20

still I don't know where or if there is a problem.

I will try a reboot and edit later the post if required

nope, after the reboot I still don't have the modules loaded and if I try to start the player I get:
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

I appreciate an idea on how to solve this issue
Thank you

---

### Post by nzgreen on 2006-06-18
@ nmsa check ncbb's post (#6) in this thread:
[http://ubuntuforums.org/showthread.php?t=197512](http://ubuntuforums.org/showthread.php?t=197512)

---

### Post by cjm5229 on 2006-06-18
VMware player is in the Dapper Repo's,  I have  VMware Server installed in my computer, which is  beta software.  I upgraded with no problems at all. I also have "linux-image headers K7" installed which updates the headers when ever neccessary.

---

### Post by nmsa on 2006-06-18
[QUOTE=nzgreen]@ nmsa check ncbb's post (#6) in this thread:
[http://ubuntuforums.org/showthread.php?t=197512](http://ubuntuforums.org/showthread.php?t=197512)[/QUOTE]
thank you
:D I am very happy indeed

just to make a recap on this
is then confirmed that the new kernel 2.6.15-25 had no misc dir and therein vmmon and vmnet modules. a copy of old modules was enough.

maybe something like this will be the solution for my sound which is also ko. I'll check.

from my previous post my arch info is not available.
I am runing Ubuntu 6.06 on amd64.

---

### Post by joris.brus on 2006-06-19
I updated linux-header 2.6.15-25 386

But when reinstalling vmware player it ends with the following.


> The subnet 172.16.111.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

The vmware kernel module is still at 2.6.15-23 even after apt-get upgrade > vmware-player-kernel-modules-2.6.15-23 (2.6.15.10-6)

---

### Post by ukbob on 2006-06-24
I HAVE THE SAME PROBLEM HELP!


Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up cdda2wav (2.01+01a01-4ubuntu6) ...
Setting up gnomebaker (0.5.1-0ubuntu1) ...

Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@ubuntuhome:~$

---

