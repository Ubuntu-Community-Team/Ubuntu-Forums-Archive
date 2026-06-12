---
title: "Can use Breezy Install CD to repair?"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-03-30
Hi
I am writing using Knoppix.
I fiddled around and messed it up. Does not seem to be a grub problem since it shows when I boot .686-smp on my Toshiba Satellite A40 Intel(R) Celeron(R) 2.70 GHz 512 MB.

My system does things like>

-check root file system at every single boot
-cannot log-in in console
-lots of lines fly by with loads of failed...I find it difficult to explain.
-the very last line I get is>

> cannot access /dev/xconsole

Thanks much for helping me. I am totally lost.:-?

---

### Post by Mustard on 2006-03-30
What were you fiddling with?

---

### Post by xyz on 2006-03-30
[QUOTE=Mustard]What were you fiddling with?[/QUOTE]

Well, I fiddled with this [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)
to save a few seconds on boot time and possibly learn something. And it certainely is not i3dmaster fault!
I ended up booting in over 10 minutes!...and,in console, typed ```
sudo /etc/init.d/gdm restart
``` to get to log in and proceed with Gnome.
I installed/opened ```
sysv-rc-conf
``` adding&deleting X to lessen boot time.

Then I went back into sysv...to try to fix it and ended up making it worse! Now I cannot log in at all as my system remains stuck on > cannot access /dev/xconsole.

Thanks for answering, Mustard.

---

### Post by Mustard on 2006-03-30
Hmmm..its a pretty sticky problem you are in.  I'm not even sure where to start! :)

Reading the last post in the thread, I wonder whether you have made a backup of inittab?  Or whether someone elses inittab would do as a replacement?

---

### Post by xyz on 2006-03-30
[QUOTE=Mustard]Hmmm..its a pretty sticky problem you are in.  I'm not even sure where to start! :)

Reading the last post in the thread, I wonder whether you have made a backup of inittab?  Or whether someone elses inittab would do as a replacement?[/QUOTE]

I found this on a French forum. From what I understood it is meant to repair Breezy from Knoppix.Dont know if it helps.
> Tu démarres un live cd, tu ouvres un terminal et avec les droits administrateur tu
passes la commande :
fdisk -l
Cela va lister tous les disques et toutes les partitions de ta machine.

Ensuite il faudra que tu montes la partition système, toujours avec les droits
administrateur :
mount -t ext3 /dev/hdxn /mnt (xn à remplacer par les indications données par fdisk)
puis
cat  /mnt/etc/fstab
pour éditer le fichier fstab puis
cat /mnt/boot/grub/menu.lst
pour éditer le fichier menu.lst

Tu n'auras qu'à reporter les indications de ces commande ici ou corriger en éditant
les fichiers fstb et menu.lst.
Pour modifier /etc/fstab, faire une sauvegarde :
cp /mnt/etc/fstab /mnt/etc/fstab_sav
puis ouvir le fichier avec un éditeur :
nano /mnt/etc/fstab
ou avec gedit :
gedit /mnt/etc/fstab

I tried but...here is what it said. Thanks a lot for trying to help.

```
root@0[knoppix]# fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1689    13566861    7  HPFS/NTFS
/dev/hda2            3507        4863    10900102+   f  W95 Ext'd (LBA)
/dev/hda3            1690        3506    14595052+  83  Linux
/dev/hda5            3589        4863    10241406    7  HPFS/NTFS
/dev/hda6            3507        3588      658602   82  Linux swap / Solaris

Partition table entries are not in disk order

```


And when I type

```
root@0[knoppix]# mount -t ext3/dev/hda3/mnt

```

it just says
```
root@0[knoppix]#   
```....and nothing more.

Am I even on the right track?

---

### Post by Mustard on 2006-03-30
Actually reading through the thread I wonder whether inittab is even the issue.  I'm still trying to wrap my head around what is being altered and how you might manually edit it to fix it.  Which startup process were you playing with?

From what I can understand of the French above, it seems to be irrelevant to the problem.  That looks like its trying to fix the menu.lst for grub, but grub is not your problem.  Your problem seems to be that you have disabled a service at startup that is  essential for the system to work.

I'm just recalling what the knoppix live CD looks like, and I am pretty sure that all the hard drives show up as icons on the desktop and you can mount them by clicking on the icons.

---

### Post by xyz on 2006-03-30
This may help....

> root@0[knoppix]# cat /etc/inittab
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.9 2001/05/31 10:37:50 knopper Exp $

# The default runlevel.
id:5:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:respawn:/bin/bash -login >/dev/tty1 2>&1 </dev/tty1

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/knoppix-halt
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/knoppix-reboot

# What to do when CTRL-ALT-DEL is pressed.
ca::ctrlaltdel:/etc/init 0

# Action on special keypress (ALT-UpArrow).
kb::kbrequest:/bin/echo "Keyboard Request -- edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
# 4 virtual consoles with immortal shells
1:12345:respawn:/bin/bash -login >/dev/tty1 2>&1 </dev/tty1
2:2345:respawn:/bin/bash -login >/dev/tty2 2>&1 </dev/tty2
3:2345:respawn:/bin/bash -login >/dev/tty3 2>&1 </dev/tty3
4:2345:respawn:/bin/bash -login >/dev/tty4 2>&1 </dev/tty4


# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

#-- isdnutils begin
# Change the lines below for your local setup and uncomment them.
# Use "init q" to reread inittab.
# look at the vboxgetty / mgetty manpage for more information (mgetty isn't
# standard!)
#
#I0:2345:respawn:/usr/sbin/vboxgetty -d /dev/ttyI0
#I1:2345:respawn:/sbin/mgetty -D -m '"" ATZ OK AT&Eyourmsnhere OK AT&B512 OK' -s 38400 ttyI1
#-- isdnutils end
# Run X Window session from CDROM in runlevel 5
w5:5:wait:/bin/sleep 2
x5:5:wait:/etc/init.d/xsession start


---

### Post by xyz on 2006-03-30
Which startup process were you playing with?

I promised I will nerver do this again...and I do not really remember which I was playing with! I more or less followed i3dmaster advice on his thread...marking/unmarking X at the different run levels.

---

### Post by Mustard on 2006-03-30
You know the output of the above inittab file is the inittab file for knoppix don't you?

I'm as much in the dark as you at the moment as to how to proceed.

---

### Post by xyz on 2006-03-30
[QUOTE=Mustard]You know the output of the above inittab file is the inittab file for knoppix don't you?

I'm as much in the dark as you at the moment as to how to proceed.[/QUOTE] I went into my hda3 and got this out of it
```
#!/bin/sh
# /etc/init.d/xorg-common: set up the X server and ICE socket directories

set -e

PATH=/bin:/usr/bin:/sbin:/usr/sbin
SOCKET_DIR=/tmp/.X11-unix
ICE_DIR=/tmp/.ICE-unix

. /lib/lsb/init-functions
. /etc/default/rcS

do_restorecon () {
  # Restore file security context (SELinux).
  if which restorecon >/dev/null 2>&1; then
    restorecon "$1"
  fi
}

set_up_socket_dir () {
  if [ "$VERBOSE" != no ]; then
    log_begin_msg "Setting up X server socket directory $SOCKET_DIR..."
  else
    log_begin_msg "Setting up X server socket directory..."
  fi
  if [ -e $SOCKET_DIR ] && [ ! -d $SOCKET_DIR ]; then
    mv $SOCKET_DIR $SOCKET_DIR.$$
  fi
  mkdir -p $SOCKET_DIR
  chown 0:0 $SOCKET_DIR
  chmod 1777 $SOCKET_DIR
  do_restorecon $SOCKET_DIR
  log_end_msg 0
}

set_up_ice_dir () {
  if [ "$VERBOSE" != no ]; then
    log_begin_msg "Setting up ICE socket directory $ICE_DIR..."
  else
    log_begin_msg "Setting up ICE socket directory..."
  fi
  if [ -e $ICE_DIR ] && [ ! -d $ICE_DIR ]; then
    mv $ICE_DIR $ICE_DIR.$$
  fi
  mkdir -p $ICE_DIR
  chown 0:0 $ICE_DIR
  chmod 1777 $ICE_DIR
  do_restorecon $ICE_DIR
  log_end_msg 0
}

case "$1" in
  start)
    set_up_socket_dir
    set_up_ice_dir
  ;;

  restart|reload|force-reload)
    /etc/init.d/xorg-common start
  ;;

  stop)
   :
  ;;

  *)
    log_success_msg "Usage: /etc/init.d/xorg-common {start|stop|restart|reload|force-reload}"
    exit 1
    ;;
esac

exit 0

# vim:set ai et sts=2 sw=2 tw=0:

```

I think this is relevent to Breezy!

Hi Mustard...I reallz have to head for work now. Thanks a lot.I will be back on the thread as soon as I can.

---

### Post by Mustard on 2006-03-30
Heh..the more I look into this the more complex it gets. 

I found some documents on how it all works and opened one using this command...

```
zcat /usr/share/doc/sysv-rc/README.runlevels.gz
```

[quote=runlevels.gz debian manual] Order of scripts run in /etc/rc?.d
                ==================================

0. Overview.

   All scripts executed by the init system are located in /etc/init.d.
   The directories /etc/rc?.d (? = S, 0 .. 6) contain relative links to
   those scripts. These links are named S<2-digit-number><original-name>
   or K<2-digit-number><original-name>.

   If a scripts has the ".sh" suffix it is a bourne shell script and
   MAY be handled in an optimized manner. The behaviour of executing the
   script in an optimized way will not differ in any way from it being
   forked and executed in the regular way.

   The following runlevels are defined:

   N       System bootup (NONE).
   S       Single user mode (not to be switched to directly)
   0       halt
   1       single user mode
   2 .. 5  multi user mode
   6       reboot

1. Boot.

   When the systems boots, the /etc/init.d/rcS script is executed. It
   in turn executes all the S* scripts in /etc/rcS.d in alphabetical
   (and thus numerical) order. The first argument passed to the
   executed scripts is "start". The runlevel at this point is "N" (none).

   Only things that need to be run once to get the system in a consistent
   state are to be run. The rcS.d directory is NOT meant to replace rc.local.
   One should not start daemons in this runlevel unless absolutely
   necessary. Eg, NFS might need the portmapper, so it is OK to start it
   early in the bootprocess. But this is not the time to start the
   squid proxy server.

2. Going multiuser.

   After the rcS.d scripts have been executed, init switches to the
   default runlevel as specified in /etc/inittab, usually "2".

   Init then executes the /etc/init.d/rc script which takes care of
   starting the services in /etc/rc2.d.

   Because the previous runlevel is "N" (none) the /etc/rc2.d/KXXxxxx
   scripts will NOT be executed - there is nothing to stop yet,
   the system is busy coming up.

   If for example there is a service that wants to run in runlevel 4
   and ONLY in that level, it will place a KXXxxxx script in
   /etc/rc{2,3,5}.d to stop the service when switching out of runlevel 4.
   We do not need to run that script at this point.

   The /etc.rc2.d/SXXxxxx scripts will be executed in alphabetical
   order, with the first argument set to "start".

3. Switching runlevels.

   When one switches from (for example) runlevel 2 to runlevel 3,
   /etc/init.d/rc will first execute in alphabetical order all K
   scripts for runlevel 3 (/etc/rc3.d/KXXxxxx) with as first argument
   "stop" and then all S scripts for runlevel 3 (/etc/rc3.d/SXXxxxx)
   with as first argument "start".

   As an optimization, a check is made for each "service" to see if
   it was already running in the previous runlevel. If it was, and there
   is no K (stop) script present for it in the new runlevel, there is
   no need to start it a second time so that will not be done.

   On the other hand, if there was a K script present, it is assumed the
   service was stopped on purpose first and so needs to be restarted.

   We MIGHT make the same optimization for stop scripts as well-
   if no S script was present in the previous runlevel, we can assume
   that service was not running and we don't need to stop it either.
   In that case we can remove the "coming from level N" special case
   mentioned above in 2). But right now that has not been implemented.

4. Single user mode.

   Switching to single user mode is done by switching to runlevel 1.
   That will cause all services to be stopped (assuming they all have
   a K script in /etc/rc1.d). The runlevel 1 scripts will then switch
   to runlevel "S" which has no scripts - all it does is spawn
   a shell directly on /dev/console for maintenance.

5. Halt/reboot

   Going to runlevel 0 or 6 will cause the system to be halted or rebooted,
   respectively. For example, if we go to runlevel 6 (reboot) first
   all /etc/rc6.d/KXXxxxx scripts will be executed alphabetically with
   "stop" as the first argument.

   Then the /etc/rc6.d/SXXxxxx scripts will be executed alphabetically
   with "stop" as the first argument as well. The reason is that there
   is nothing to start anymore at this point - all scripts that are
   run are meant to bring the system down.

   In the future, the /etc/rc6.d/SXXxxxx scripts MIGHT be moved to
   /etc/rc6.d/K1XXxxxx for clarity.

[/quote]

This is a directory listing of this folder..

```
mustard@slave:/usr/share/doc/sysv-rc$ ls
changelog.gz  copyright  README.invoke-rc.d.gz  
README.policy-rc.d.gz  README.runlevels.gz

```

You can open the '.gz' extension documents using the zcat command.  I'll have a bit of a read, but its all pretty heavy stuff. :)

---

### Post by xyz on 2006-03-31
Thanks and yes indeed it does look like heavy stuff but I will check it out.good day to you.

Would I find that in Knoppix...
root@0[knoppix]# zcat /usr/share/doc/sysv-rc/README.runlevels.gz
zcat: /usr/share/doc/sysv-rc/README.runlevels.gz: No such file or directory

---

### Post by Mustard on 2006-03-31
[QUOTE=xyz]Thanks and yes indeed it does look like heavy stuff but I will check it out.good day to you.

Would I find that in Knoppix...
root@0[knoppix]# zcat /usr/share/doc/sysv-rc/README.runlevels.gz
zcat: /usr/share/doc/sysv-rc/README.runlevels.gz: No such file or directory[/QUOTE]

You would have to mount your Ubuntu partition (using Knoppix) and look for it on there.

---

### Post by xyz on 2006-03-31
[QUOTE=Mustard]You would have to mount your Ubuntu partition (using Knoppix) and look for it on there.[/QUOTE]

Yes of course...my head is backwards...I think I do not even remember my real name!!!

---

### Post by Mustard on 2006-03-31
[QUOTE=xyz]Yes of course...my head is backwards...I think I do not even remember my real name!!![/QUOTE]

I'm off to watch a DVD.  Good luck.  I'll check back in later to see how you are going. :)

---

### Post by xyz on 2006-03-31
I am not going to say I understood everything because I surely did not!
What I think I understood is that the ** /usr/share/doc/sysv-rc/README.runlevels.gz** explains how it all works<however it does not seem to give solutions to problems.

What do you think about this...

The big mess began when I played around in **sysv-rc-conf** under Breezy adding and/or deleting X to start and/or stop services at various runlevels on boot.
Is there a way from Knoppix to reopen sysv-rc-conf in my hda3 which is where my Breezy is located? I would then put X all over the place thus making sure all and absolutely all services start on boot..
It is probably a stupid idea or impossible to achieve.Don t know!

---

### Post by Mustard on 2006-03-31
[QUOTE=xyz]I am not going to say I understood everything because I surely did not!
What I think I understood is that the ** /usr/share/doc/sysv-rc/README.runlevels.gz** explains how it all works<however it does not seem to give solutions to problems.

What do you think about this...

The big mess began when I played around in **sysv-rc-conf** under Breezy adding and/or deleting X to start and/or stop services at various runlevels on boot.
Is there a way from Knoppix to reopen sysv-rc-conf in my hda3 which is where my Breezy is located? I would then put X all over the place thus making sure all and absolutely all services start on boot..
It is probably a stupid idea or impossible to achieve.Don t know![/QUOTE]

The way I look at it, the only way you are going to recover from this is to manually re-enable the processes.  To do this you would have to come to a clear understanding of how this process works.  I know I have no clue, even after reading the above guide. :)

If you were to run sysv-rc-conf from knoppix, it would only be affecting the sysv-rc settings for Knoppix (assuming Knoppix even uses this method), so I can't see how you can use sysv-rc-conf to edit the Ubuntu settings, as Ubuntu is not the currently running system (Knoppix is currently running).

I guess it comes down to two options.

1. You can become the master of the sysv-rc guidelines and learn how to manually set it all up from a Knoppix live CD.

2.  You can backup your critical data now, and reinstall Ubuntu.

Neither option is really exciting. :D

---

### Post by xyz on 2006-03-31
Maybe I could add some mustard to my breezy sauce....just kidding!

If I ever become the master of  sysv-rc guidelines, you will be the 1st to know...but frankly there is ,no doubt, more important things to try to master prior to this one. 

Well, like they say, reinstalling ain t gonna be easy for the noob that I am but that s how one learns!
If, by any chance, you knew of the simplest,easiest to understand link to a howto reinstall,please let me know.
This is just in case you have that link right at the tips of your fingers. I can search by myself,no problem.

Again thank you for all the attention you ve given me.I am very touched.
Will let you know <PM< how all this turns out.
Good day ...or night..don t know what time it is in Australia..here its 3.40 PM.

---

### Post by engla on 2006-03-31
[QUOTE=xyz]I am not going to say I understood everything because I surely did not!
What I think I understood is that the ** /usr/share/doc/sysv-rc/README.runlevels.gz** explains how it all works<however it does not seem to give solutions to problems.

What do you think about this...

The big mess began when I played around in **sysv-rc-conf** under Breezy adding and/or deleting X to start and/or stop services at various runlevels on boot.
Is there a way from Knoppix to reopen sysv-rc-conf in my hda3 which is where my Breezy is located? I would then put X all over the place thus making sure all and absolutely all services start on boot..
It is probably a stupid idea or impossible to achieve.Don t know![/QUOTE]
I have absolutely no idea how to solve this in detail, but you should be able to use the Breezy Install CD, booted in "rescue" mode.

That should give you a *chrooted* shell to your normal hard disk; that is a shell "from your normal point of view", but really booted from the CD. So in a chrooted shell, you should be able to run sudo sysv-rc-conf and make changes to your install.

---

### Post by xyz on 2006-03-31
[QUOTE=engla]I have absolutely no idea how to solve this in detail, but you should be able to use the Breezy Install CD, booted in "rescue" mode.

That should give you a *chrooted* shell to your normal hard disk; that is a shell "from your normal point of view", but really booted from the CD. So in a chrooted shell, you should be able to run sudo sysv-rc-conf and make changes to your install.[/QUOTE]

Thanks engla...this answers my very first question! Somehow we got carried away from that 1st question. I will try your way.Back for news when I get there...if I don t mess everything up!In that case, Knoppix is great help.

---

### Post by Mustard on 2006-03-31
[QUOTE=engla]I have absolutely no idea how to solve this in detail, but you should be able to use the Breezy Install CD, booted in "rescue" mode.

That should give you a *chrooted* shell to your normal hard disk; that is a shell "from your normal point of view", but really booted from the CD. So in a chrooted shell, you should be able to run sudo sysv-rc-conf and make changes to your install.[/QUOTE]

Ah well there you go. :)  Thanks for chiming in at the right time engla.

I wish I could see how that works now, but I'm not so sure I want to bust my own system and attempt it. :D

I was already mucking around today destroying grub and then reinstalling it so I could get some more practice installing grub.

---

### Post by xyz on 2006-03-31
[QUOTE=Mustard]Ah well there you go. :)  Thanks for chiming in at the right time engla.

I wish I could see how that works now, but I'm not so sure I want to bust my own system and attempt it. :D

I was already mucking around today destroying grub and then reinstalling it so I could get some more practice installing grub.[/QUOTE]

Yes, Sir...I don t think you should try and bust your system just for kicks...I will let you guys know how it turns out. But I have to leave now.So later...

---

### Post by xyz on 2006-04-01
Hi guys
Well I booted on the Ubuntu Install CD and went through the motions until I got to a shell in rescue mode.
I did type ```
sudo sysv/rc/conf
``` and got the following message
> sudo unable to lookup x1-6-00-08-00-fe-f6-f6 via gethostbyname
error opening terminal  bterm

Any ideas?

---

### Post by xyz on 2006-04-01
I just had a thought and I am probably on the wrong track but I just do not know how to go about my problem anymore.
I am now running Dynebolic Live CD with full access,viewing and editing of my hda2 which is where Breezy is.
Could I modify fstab, boot/grub/menu.lst to fix the problem? Would that be any good?
Oh boy...am I lost?

---

### Post by Mustard on 2006-04-01
Maybe you should try going back to the install disk rescue method but see if you can do it without using sudo ie get a root prompt using sudo -i or sudo -s or even setting a root password and using su.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by xyz on 2006-04-14
Nothing worked! Had to reinstall, my first one, and it works!!!
Don't ask me how I did it! It just happened!
I wish I had a dozen computers to practice installing instead of waiting for the next crash. That way it would sink in.
Anyway, thanks for the help...all of you.

---

### Post by Mustard on 2006-04-14
[QUOTE=xyz]Nothing worked! Had to reinstall, my first one, and it works!!!
Don't ask me how I did it! It just happened!
I wish I had a dozen computers to practice installing instead of waiting for the next crash. That way it would sink in.
Anyway, thanks for the help...all of you.[/QUOTE]

Install ubuntu again on another new partition and practice breaking that install. :D

---

### Post by xyz on 2006-04-14
[QUOTE=Mustard]Install ubuntu again on another new partition and practice breaking that install. :D[/QUOTE]
Good idea! I'm reading this [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)
and I think I almost understand what I'm reading!:D

---

### Post by Mustard on 2006-04-14
[QUOTE=xyz]Good idea! I'm reading this [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)
and I think I almost understand what I'm reading!:D[/QUOTE]

Ah yes.  Herman's guides are excellent. :)

---

