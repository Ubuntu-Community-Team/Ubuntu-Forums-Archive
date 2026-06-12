---
title: "Ubuntu mac slowing down with thunderbolt display (solution)"
date: 2012-07-29
forum: Apple Hardware Users
---

### Post by thesillymoose on 2012-07-29
Hi,

I am running Ubuntu 12.04 on a macbook air 4,2 (mid 2011). When I cold boot with the Thunderbolt display, I found the GUI slows down dramatically. I'm not sure what the root cause is but running top from the command line showed a kworker process eating up my CPU.

Fortunately there is a fix for this, as helpfully documented by souriguha [**here**]("http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/").

For 12.04 Ubuntu users, open up the terminal and become root by typing:
```
sudo su
```
To fix the issue for the current session only type:
```
#echo N> /sys/module/drm_kms_helper/parameters/poll
```

And to change the setting for all future sessions type:
```
#echo "options drm_kms_helper poll=N">/etc/modprobe.d/local.conf
```

Thanks again to souriguha for sharing the solution online.

---

### Post by Mb0742 on 2012-07-30
> And to change the setting for all future sessions type:
Code:
#echo "options drm_kms_helper poll=N">/etc/modprobe.d/local.conf

>> is the correct redirect. Safety first :)

---

### Post by thesillymoose on 2012-08-24
Redirect updated following helpful addition by Mb0742:
 
> **thesillymoose said:**
> Hi,
 
I am running Ubuntu 12.04 on a macbook air 4,2 (mid 2011). When I cold boot with the Thunderbolt display, I found the GUI slows down dramatically. I'm not sure what the root cause is but running top from the command line showed a kworker process eating up my CPU.
 
Fortunately there is a fix for this, as helpfully documented by souriguha [**here**]("http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/").
 
For 12.04 Ubuntu users, open up the terminal and become root by typing:
```
sudo su
```
To fix the issue for the current session only type:
```
#echo N>> /sys/module/drm_kms_helper/parameters/poll
```
 
And to change the setting for all future sessions type:
```
#echo "options drm_kms_helper poll=N">>/etc/modprobe.d/local.conf
```
 
Thanks again to souriguha for sharing the solution online.

---

### Post by domhans on 2013-04-15
I have a similar problem but this solution does not work for me. When I attach my thunderbolt displayt to my 13" intel macbook retina the system needs several minutes to boot and the mouse is extreamly delayed. Everything else seems to work great  and I did not notice any unusual high cpu usage. I'm running Kubuntu 13.04 beta2. X.org log file seems to be ok.

Any suggestions?
Thanks
Dom

---

### Post by kc600 on 2013-04-26
This answer was very helpful. 

Unfortunately it stopped working on Ubuntu 13.04 Raring.

$ sudo echo N> /sys/module/drm_kms_helper/parameters/poll
bash: /sys/module/drm_kms_helper/parameters/poll: Permission denied

And modifying local.conf is possible but makes no difference after reboot.

(Lenovo Thinkpad S430)

---

### Post by mattm79 on 2013-04-29
> **kc600 said:**
> This answer was very helpful. 

Unfortunately it stopped working on Ubuntu 13.04 Raring.

$ sudo echo N> /sys/module/drm_kms_helper/parameters/poll
bash: /sys/module/drm_kms_helper/parameters/poll: Permission denied

And modifying local.conf is possible but makes no difference after reboot.

(Lenovo Thinkpad S430)

Hi,

You can try the below, it works on 12.04 (which had similar problem to what you described)

just add the echo N line to /etc/rc.local and restart, that'll make sure the parameter gets changed by root on restart, if you have nothing else there it should look similar to this:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo N> /sys/module/drm_kms_helper/parameters/poll
exit 0

regards,

matt

---

