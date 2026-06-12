---
title: "problem with X Server"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-11-04
Hi,
I have been using Ubuntu for a while now...and every thing was fine..till today....

(possibly due to incorrect shutdown) i have landedup with the X Server problem... During startup i am getting the following message

"Failed to Start X Server (Your Graphical Interface). It is likely that it is not setup correctly. Would You like to view the X Server output to diagnose the problem"

On seleceting "Yes", i get the following message

X: Cannot start /tmp/.X11-unix (No such file or directory), aborting..

I am however able to reach the Command line login interface by selecting the recovery mode...
I also have Ubuntu Live and Ubuntu alternate CD...

Some help on how to restore my graphical interface (X Server)

Thanks

pkj

---

### Post by Pumalite on 2007-11-04
Say 'No'. Then at the command line:
sudo dpkg-reconfigure xserver-xorg

---

### Post by pkj on 2007-11-04
Does that mean i go upto the command line interface...login and then do "sudo apt-get"

pkj

---

### Post by pkj on 2007-11-04
Sorry i meant "sudo dpkj...."

pkj

---

### Post by pkj on 2007-11-04
Hi,

I am able to run the command "sudo dpkg-reconfigure xserver-xorg" once i login after starting the system in recovery mode (command line is available in the recovery mode). However even after sudo dpkg-reconfigure....., system is showing the same problem..

Any further help...

pkj

---

### Post by Pumalite on 2007-11-04
Then problem is not xserver. (did you choose 'vesa' as the driver?)

---

### Post by pkj on 2007-11-04
The driver i chose was via

After running sudo dpkg-reconfigure xserver-xorg
i am getting this nessage at the end

Xserver-xorg postinst warning: overwriting possibly-customised configuration file: backup in /etc/X11/xorg.confg 20071104231908

mkdir: cannot create directory ' /tmp/dexconf-tmp-4761': Too many links

dexconf : error: creating of temporary work directory "/tmp/dexconf-tmp-4761" failed

Xserver-xorg postinst warning: error while preparing new X org X server configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to update existing configuration

I am not able to make much out of this message..

Some help.........

pkj

---

### Post by Pumalite on 2007-11-04
'The driver i chose was via'
You have to accept most defaults, choose VESA as the driver, then: startx

---

