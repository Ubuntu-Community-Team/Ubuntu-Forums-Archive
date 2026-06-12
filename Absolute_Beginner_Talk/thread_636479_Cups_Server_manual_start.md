---
title: "Cups Server manual start"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by bobbyshafter on 2007-12-09
I have a hp printer setup as a shared printer attach to my desktop, on my lan works fine ,all machines are running gusty.
My problem,when ever i restart my desktop machine i have to restart the cups server manually in order that my laptop and other pc on my lan can see the printer.
How do i get cups server to start on boot up.

---

### Post by spiderbatdad on 2007-12-09
Applications->System->Preferences->Sessions-->+ADD

---

### Post by bobbyshafter on 2007-12-09
Restaring cups server requires a password ie root

---

### Post by blu3ness on 2007-12-09
add a new file in /etc/acpi/start.d/, call it whatever you like, i.e. 50-restart-cupsys.sh


```
#!/bin/sh

/etc/init.d/cupsys restart
```

then 

chmod +x 50-restart-cupsys.sh

try it.. :x

---

### Post by jordanmthomas on 2007-12-09
```
sudo update-rc.d cupsd defaults 
```
will add cupsd to your default runlevel.  (note, this may just need to be cups...look in /etc/init.d/ to see what it's called)

My lazy way is this:
```
gksudo gedit /etc/rc.local
```
and add this:
```
/etc/init.d/cupsd start
```

---

### Post by bobbyshafter on 2007-12-17
Still have to restart cups server manual 
This is my init.d file 
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
/etc/init.d/cupsd start
exit 0

is this correct.

---

