---
title: "[SOLVED] make a program run as sudo at startup"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-07-19
I have wireless assistant installed because it is the only thing that I have been able to get working

anyways Everytime I reboot it comes up and says that I did not run it as sudo

Does anyone know how I can get this program to automatically run as sudo at startup

Thanks

---

### Post by bodhi.zazen on 2007-07-19
Put the command (without sudo) in /etc/rc.local above the exit 0

---

### Post by Rocket2DMn on 2007-07-19
You can set commands to run at boot (not login) in the /etc/rc.local file.
Typically you call a script from here that is located (or you put) in /etc/init.d/ but you don't have to stick to that.
They should run with root privileges.

---

### Post by jrandolph on 2007-07-19
How would i go about puttin that in there?

---

### Post by Rocket2DMn on 2007-07-19
You can edit the file with 
```
gksudo gedit /etc/rc.local
```
You would just type in the command like bodhi.zazen said - the same command you would run from terminal.  It's possible there is already a script somewhere to run, but I don't know anything about your wireless assistant.

---

### Post by jrandolph on 2007-07-19
This is what it is saying


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

exit 0


When I run it from the terminal as sudo all i have to do is type 
sudo wlassistant
and then it runs correctly

How should i edit this to make it work

---

### Post by Rocket2DMn on 2007-07-19
Stick
wlassistant
above exit 0, without the sudo, like b.z said.

---

### Post by jrandolph on 2007-07-19
Like so?


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
wlassistant
exit 0

---

### Post by Rocket2DMn on 2007-07-19
Yup.

---

### Post by jrandolph on 2007-07-19
Thanks so much 

You all are amazing

---

### Post by bodhi.zazen on 2007-07-19
> **Rocket2DMn said:**
> Yup.

Thanks for your diligence Rocket2DMn

---

### Post by jrandolph on 2007-08-09
I thought this worked but when i restarted today -- again it tells me that i did not run this program as root 

can anyone please help me to get this program to run as sudo at startup

---

### Post by jrandolph on 2007-08-09
Considering this thread says it solved should i make a new thread to address this problem again?

---

### Post by bodhi.zazen on 2007-08-09
What happens when you :
 
```
sudo /etc/rc.local
```

??

can you post the contents of /etc/rc.local ?

---

### Post by jrandolph on 2007-08-09
It goes through alot of stuff then brings up my wirelessassistant 

the out put to that is



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
wlassistant
exit 0

---

### Post by bodhi.zazen on 2007-08-09
The startup script may be running too early, before your network has been fully established (just a guess)

But, if there are no errors, you can add :

sleep 4s

above wlassistant

This will "sleep" (pause) for 4 seconds. Try increasing or decreasing the sleep time as needed.

---

