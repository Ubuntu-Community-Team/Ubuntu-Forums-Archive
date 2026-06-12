---
title: "Boots to BusyBox ... Need HELP please!"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by ishift on 2006-10-29
hey guys..

last night, i installed firefox 2 on my t20 laptop. and i deleted two packages (don't remember which ones) because the system told me they weren't in use.

now, when i boot up, it takes me to busybox. it says: 

"/bin/sh: can't access tty; job control is off"

i'm running edgy.

i already searched, but the solutions either don't apply to me or the threads haven't been answered or the situations are different.

please help as i use my laptop a lot.

thanks!

---

### Post by ishift on 2006-10-29
i hate to bump so quickly, but it's really an emergency...

---

### Post by ishift on 2006-10-29
again, hate to bump it again, but i need to fix this problem by tomorrow, latest. please. help me out guys!

---

### Post by picpak on 2006-10-29
Can you post the contents of /etc/inittab? (To see if your tty's are enabled).

---

### Post by ishift on 2006-10-29
> **ishift said:**
> hey guys..

last night, i installed firefox 2 on my t20 laptop. and i deleted two packages (don't remember which ones) because the system told me they weren't in use.

now, when i boot up, it takes me to busybox. it says: 

"/bin/sh: can't access tty; job control is off"

i'm running edgy.

i already searched, but the solutions either don't apply to me or the threads haven't been answered or the situations are different.

please help as i use my laptop a lot.

thanks!

> **picpak said:**
> Can you post the contents of /etc/inittab? (To see if your tty's are enabled).

here it is:

> # /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

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
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

---

### Post by picpak on 2006-10-29
Well...that's not the problem. Do you have your Ubuntu CD with you? If so, boot it up, open a terminal and run:

```
sudo -s
mkdir /mnt/linux 
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc
apt-get install sysvinit
```

this will replace the new boot-up mechanism (upstart) with the old-fashioned sysvinit.

---

### Post by ishift on 2006-10-29
> **picpak said:**
> Well...that's not the problem. Do you have your Ubuntu CD with you? If so, boot it up, open a terminal and run:

```
sudo -s
mkdir /mnt/linux 
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc
apt-get install sysvinit
```

this will replace the new boot-up mechanism (upstart) with the old-fashioned sysvinit.

being a newbie, what does that mean? and, would my home folder still be safe?

---

### Post by jd65pl on 2006-10-29
mkdir /mnt/linux - makes a new folder called "linux" in the folder "mnt"
mount /dev/hda1 /mnt/linux - mounts your first harddrive in the previously created folder.
chroot /mnt/linux /bin/bash - changes the default root folder
mount -t proc /proc /proc - mounts proc to /proc
apt-get install sysvinit - You would be installing the package sysvinit see [this link]("http://freshmeat.net/projects/sysvinit/") for some information on the package

---

### Post by ishift on 2006-10-29
> **picpak said:**
> Well...that's not the problem. Do you have your Ubuntu CD with you? If so, boot it up, open a terminal and run:

```
sudo -s
mkdir /mnt/linux 
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc
apt-get install sysvinit
```

this will replace the new boot-up mechanism (upstart) with the old-fashioned sysvinit.

ok, i did that. the system said that there's sysvinit already installed on it.

i rebooted, but i get the same problem, booting into busybox.

the prompt is <initramfs>

---

### Post by jd65pl on 2006-10-29
Are you using edgy or dapper? If you are using the former then the previous commands are obsolete.

---

### Post by jd65pl on 2006-10-29
Have you compiled your own kernel from source? Are you aware that you have been using busybox at any point? [http://www.busybox.net/about.html](http://www.busybox.net/about.html)

---

### Post by ishift on 2006-10-29
i'm using edgy

---

### Post by ishift on 2006-10-29
> **jd65pl said:**
> Have you compiled your own kernel from source? Are you aware that you have been using busybox at any point? [http://www.busybox.net/about.html](http://www.busybox.net/about.html)

my friend had compiled a customized kernel for dapper, but, for edgy, i'm using the default kernel.

and, i'm not sure if i have been using busybox or not. this is the first time i came across it.

---

### Post by jd65pl on 2006-10-29
Ok, did you do a fresh install of edgy? You could try removing busybox if you are not using it. Can you boot into recovery mode(available from the grub menu)?

If so boot up using recovery and then do:

```
sudo aptitude remove busybox
```You may like to note the dependancies of the package at this point. Then do 

```
sudo reboot
```Does the problem still happen?

NOTE: You may wish to back up your system before doing this, use the live cd you have to do it.

---

### Post by ishift on 2006-10-29
> **jd65pl said:**
> Ok, did you do a fresh install of edgy? You could try removing busybox if you are not using it. Can you boot into recovery mode(available from the grub menu)?

If so boot up using recovery and then do:

```
sudo aptitude remove busybox
```You may like to note the dependancies of the package at this point. Then do 

```
sudo reboot
```Does the problem still happen?

NOTE: You may wish to back up your system before doing this, use the live cd you have to do it.

well, i dist-upgraded to edgy.

i don't even know if i'm "using" it or not as this is my first run-in with it. also, i can boot into recovery mode from the grub menu.

finally, how can i back up my system?

---

### Post by jd65pl on 2006-10-29
Do you have any important files in your home folder or any other place (eg work etc) if so you boot using the live cd and mount your ubuntu partition.

```
sudo mkdir /mnt/linux 
sudo mount /dev/hda1 /mnt/linux
```
This assumes that your ubuntu partition is on hda1

 Then copy your files to a CD, removable storage media or some other kind of storage

---

### Post by jd65pl on 2006-10-29
Are you dual booting with windows? If so does this only occur after booting windows the doing a "reboot" from windows and then booting ubuntu? NOTE: These steps seem to be specific.

---

### Post by ishift on 2006-10-29
> **jd65pl said:**
> Do you have any important files in your home folder or any other place (eg work etc) if so you boot using the live cd and mount your ubuntu partition.

```
sudo mkdir /mnt/linux 
sudo mount /dev/hda1 /mnt/linux
```
This assumes that your ubuntu partition is on hda1

 Then copy your files to a CD, removable storage media or some other kind of storage

i actually did that, but i can't seem to copy certain folders as i don't have permission. how can i give myself permission?

> **jd65pl said:**
> Are you dual booting with windows? If so does this only occur after booting windows the doing a "reboot" from windows and then booting ubuntu? NOTE: These steps seem to be specific.

no, i'm not dual booting. after googling it and searching, i found that most people have this problem after early installations, but i don't understand why i'm getting it now, considering i've had edgy for almost 2 weeks now...

---

### Post by jd65pl on 2006-10-29
Is there any piece of software that you have installed recently which could have caused the problem?

To give yourself access to the files you require you could use.

```
cd *file path*
sudo chmod *username filename*
```

---

### Post by ishift on 2006-10-29
> **jd65pl said:**
> Is there any piece of software that you have installed recently which could have caused the problem?

To give yourself access to the files you require you could use.

```
cd *file path*
sudo chmod *username filename*
```

the last thing i installed was firefox 2.0

and thanks for the code :D

---

### Post by ishift on 2006-10-29
> **jd65pl said:**
> Is there any piece of software that you have installed recently which could have caused the problem?

To give yourself access to the files you require you could use.

```
cd *file path*
sudo chmod *username filename*
```

from the code you provided, i'm assuming each filename must be chmodded. also, what does username refer to? the livecd username?

---

### Post by jd65pl on 2006-10-29
> **ishift said:**
> the last thing i installed was firefox 2.0

and thanks for the code :D

DId you compile it from source or download from the repositories? Dont worry about it! We will get through your problems!

---

### Post by ishift on 2006-10-29
i downloaded firefox 2.0 from mozilla's site and followed instructions i found from the ubuntu documentation site to install it.

---

### Post by jd65pl on 2006-10-29
If you are using edgy then you should try getting it from the repo's however they are v. busy at the moment they will probably free up in a few days. has your previous problem been fixed?

---

### Post by ishift on 2006-10-29
i'm currently backing up all of my personal documents and such.

however, no, my boot problem still hasn't been solved. the worst situation that i can think of is a complete reinstall of edgy. i hope it doesn't come to that though...

---

### Post by picpak on 2006-10-29
Glad you guys could help. I had assumed it was a problem with upstart because that won't even boot up my computer.

---

### Post by ishift on 2006-10-29
well, after trying all that, i decided to reinstall edgy. i backed up all the important files anyway and restarting fresh seems like a good idea, considering i had a lot of junk as well.

thanks for the help guys!

i have another question, but i'll start a new thread as it's a completely different topic, but thanks!

---

### Post by RichJacot on 2006-11-12
I'm am now getting the same thing, even after many fresh reinstalls:

[FONT="System"][SIZE="2"]Busybox v1.1.3(Devian 1:1.3-2ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't tty; job control turned off
(initramfs)

#[/SIZE][/FONT]

I have been trying to do a fresh install of edgy and encrypt root, swap and home.  I have done at least 8 or 10 different full installs with the single cd I downloaded.  IT WAS WORKING, at least for a few installs.  At this point I have even downloaded the alt cd and I get the same result after installing from that.

I think it has something to do with the partitioning.  The reason I think so is because...  If I let the installer erase the whole disk and let it do the partitioning piece, after the install it boots-up fine.](*,)   Needless to say the default partitioning setup is not what I need. 

I'm open to suggestions, anyone?

---

