---
title: "Can't remove program"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2006-09-01
I recently tried to install MLDonkey, and in looking at Synaptic I saw there was a mldonkey-server program to go with it. So I installed it. It ended with an error, so I decided that it's probably not a great idea to keep it around. MLDonkey was removed without issue, but mldonkey-server errors out without uninstalling with the following output:

Removing mldonkey-server ...
Stopping MLDonkey: mlnetNo process in pidfile `/var/run/mlnet.pid' found running; none killed.
invoke-rc.d: initscript mldonkey-server, action "stop" failed.
dpkg: error processing mldonkey-server (--remove):
 subprocess pre-removal script returned error exit status 1
Starting MLDonkey: mlnetinstall: invalid option -- f
Try `install --help' for more information.
invoke-rc.d: initscript mldonkey-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mldonkey-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone know what I can do about this?

---

### Post by macdo on 2006-09-01
Try, in a console: ```
sudo apt-get remove mldonkey-server
```
If that doesn't work, then reinstall it: ```
sudo apt-get install mldonkey-server
``` then remove it again.
You could also try ```
sudo apt-get -f install
```

Good luck

---

### Post by pteri498 on 2006-09-01
Those options still result in errors and (as far as Synaptic is concerned) the program mldonkey-server is still installed. Is there a way I can get into console mode without having it load anything that isn't critical? That line:

Stopping MLDonkey: mlnetNo process in pidfile `/var/run/mlnet.pid' found running; none killed.

It leaves me thinking that if I could just keep that thing from loading, I might be able to solve this problem. any ideas?:confused:

---

### Post by pteri498 on 2006-09-01
*bump* this is a serious problem. It's interfering with my installations of other programs. I just tried to install the build-essential package, and it returned an error concerning mldonkey.

cedric@cedbuntu:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mldonkey-server (2.7.1-2ubuntu2) ...
Starting MLDonkey: mlnetinstall: invalid option -- f
Try `install --help' for more information.
invoke-rc.d: initscript mldonkey-server, action "start" failed.
dpkg: error processing mldonkey-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mldonkey-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pyrokenx on 2006-09-21
I've got the exact same problem, no matter what I do to remove it or install it that I've found, this still happens.

---

### Post by kaath on 2006-09-23
you should try this:

```
sudo gedit /etc/init.d/mldonkey-server
```

then comment this line

```
start-stop-daemon --stop --pidfile $PIDFILE
```

save and retry 

```
sudo apt-get remove mldonkey-server
```

shoul work now

---

### Post by cashon on 2006-09-25
If still cannot, try this:

sudo chmod -x /etc/init.d/mldonkey-server

sudo reboot

sudo apt-get remove mldonkey-server

---

### Post by -Leo- on 2006-09-25
Cheers, cashon. :KS

---

