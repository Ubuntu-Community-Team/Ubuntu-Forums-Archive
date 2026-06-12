---
title: "Desktop Shortcuts for Terminal commands?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by marksy1984 on 2008-03-06
Hi All,
Right I've been a Ubuntu 7.10 user for 24 hours now and need some advice. I managed to get my Huawei E220 modem working on 3 mobile broadband in the UK. 

To connect I type **sudo wvdial hsdpa **into the terminal. This is fine by me but if my wife tries to use my laptop, which she does very occasionally she will insist I put Windows back on, as she'll be scared of using terminal.

Is there a way of putting a shortcut on the desktop to execute **sudo wvdial hsdpa** instead? It seems obvious to me that there should be. 

Please detail very simply and step by step for me if there is.....:)

---

### Post by hyper_ch on 2008-03-06
there is, right-click the desktop, add a launcher and paste the command in there... she'll get then a password prompt - but that can't be stopped.

---

### Post by kerry_s on 2008-03-06
you could also try putting it in rc.local which runs as root at startup, so it will be ready by the time you get to the desktop.

press> alt+f2
in the launcher type> gksu gedit /etc/rc.local
just above the exit put the command with "&" at the end.

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

wvdial hsdpa &
exit 0

---

### Post by marksy1984 on 2008-03-06
Thanks guys. Hyper_ch I tried that but it wouldn't do anything. I'm wondering if I have a problem in my Ubuntu install. 

Kerry_s, Thanks that sounds like a good idea to me. If the laptop is started with the modem disconnected, with it flag some sort of error message or simply boot as normal?

---

### Post by lswest on 2008-03-06
about creating a launcher, make sure you change the type to "application in terminal" from the drop down, then it should work

to do so right-click the launcher you made and choose properties (or make a new one) and then where it says Type: [drop down menu] change it from application to application in terminal

---

### Post by kerry_s on 2008-03-06
> **marksy1984 said:**
> 
Kerry_s, Thanks that sounds like a good idea to me. If the laptop is started with the modem disconnected, with it flag some sort of error message or simply boot as normal?

that's what the "&" is for, it will continue to boot as normal.

---

### Post by marksy1984 on 2008-03-06
Legends. Thank you

---

### Post by forrestcupp on 2008-03-06
If you change your launcher to "application in terminal" and you just can't get it to work, you could make a bash script and put it on your desktop.  Open up your text editor and type:
```
#!/bin/bash
sudo wvdial hsdpa
```
Then save that file somewhere safe.  Then in a terminal, type:
```
chmod +x /path/to/file/Filename
``` replacing it with the actual path to the file you saved and the name of the file.  That makes it executable.

Then you can make a shortcut to that script.

But you should be able to just get the launcher to work.

---

