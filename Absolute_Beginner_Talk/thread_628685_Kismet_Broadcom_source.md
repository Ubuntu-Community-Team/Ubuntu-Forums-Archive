---
title: "Kismet Broadcom source"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by JO68 on 2007-12-01
I'm trying to configure Kismet to work with my broadcom wireless card, but every time i try to run Kismet I get an error

Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to jordan (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'bcm43xx' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
Done.

I've tried not only the bcm43xx source, but also b43, and b43legacy and have gotten the same error.  I know I have an old laptop 5 years? but it seems like it should work.  Has anyone encountered this error before? If not, does anyone have any ideas on how to fix it?

---

### Post by madamore on 2007-12-03
Ideas, not sure:
As the ouput says:
..."Check the output from 'configure' for more information about why it might not have been compiled in."

There was something that wasn't compiled, you must see  why.

I think when says source type 'bcm43xx' doesn't means "bcm43xx source code", it means that you didn't compile "Kismet" with 'bcm43xx' support.

from kismet documentation:
"
Run ``./configure''.  Pay attention to the output!  If Kismet cannot
      find all the headers and libraries it needs, it won't be able to do
      many things."
"Edit the config file (standardly in "/usr/local/etc/kismet.conf")""
Set the capture source by changing the "source" configuration option.
      FOR A LIST OF VALID CAPTURE SOURCES, SEE THE SECTION OF THIS README
      CALLED "CAPTURE SOURCES".  The capture source you should use depends
      on the operating system and driver that your wireless card uses.
      USE THE PROPER CAPTURE SOURCE.  No permanent harm will come from using
      the wrong one, but you won't get the optimal behavior."

Good luck!!!

---

### Post by Joker5bb on 2008-07-05
here is how to do it 

For a latest version of Kismet compile from source. 

```
wget http://www.kismetwireless.net/code/kismet-2008-05-R1.tar.gz
tar -xzf kismet-2008-05-R1.tar.gz
cd kismet-2008-05-R1
./configure
make dep
make
sudo make install

```

```
sudo gedit /usr/local/etc/kismet.conf
```

change the following line
source=b43,wlan0,broadcom
save

To run Kismet 
```
sudo kismet
```

---

