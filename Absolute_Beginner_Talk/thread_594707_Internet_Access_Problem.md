---
title: "Internet Access Problem"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-10-28
Everytime I start Ubuntu (Gutsy) I have to open the terminal and type "sudo ifconfig eth0 mtu 1492" before I can access the internet.  I've tried some of the fixes that worked on previous versions but they don't seem to work on Gutsy.  What can I do to set the mtu to 1492 at startup?:confused:

---

### Post by MegaJim on 2007-10-28
You can create a shell script that will automate this for you by adding it to the sesion info.

navigate to your home directory

```
cd ~
```

create a new script file

```
touch lanconfig.sh
```

open it up in a text editor

```
gedit lanconfig.sh
```

change it to look like this

```

#!/bin/bash
# automate lan config at boot
ifconfig eth0 mtu 1492

```

save it

add it to your sessions info (system -> preferences -> sessions)

Add startup command

call it something memorable, enter the command as ~/lanconfig.sh

save it

now when you login, the script will set that config for you

---

### Post by WhiteSphinx on 2007-10-28
Okay I'll try that

---

### Post by MegaJim on 2007-10-28
Ok, good luck

---

### Post by MegaJim on 2007-10-28
Oh, I forgot to mention before, that you must have execute permissions on the script or it won't run!  In case your default umask isn't set to touch files as executable, use this command before you try to run it:

```
chmod +x lanconfig.sh
```

please let me know if it works :)

---

### Post by WhiteSphinx on 2007-10-28
Okay I'll give that a try

---

### Post by MegaJim on 2007-10-28
> **WhiteSphinx said:**
> It did'nt work:(
I still have to do "sudo ifconfig eth0 mtu 1492"

in your first post you didn't include the sudo part :(  this script won't work for super user stuff i'm afraid, although it is possible to set that up, its a little more complex

read this article about starting up firestarter automatically: [http://www.howtoadvice.com/AutoFirestarter/](http://www.howtoadvice.com/AutoFirestarter/)

you can use the same method to edit your sudoers file and let ifconfig run without root permissions.

---

### Post by WhiteSphinx on 2007-10-28
This apparently works because you are pointing it to an executable file. I've tried pointing it to the lanconfig.sh file but it still doesn't work.  I still have to manually type in "sudo ifconfig eth0 mtu 1492":confused::(

---

### Post by MegaJim on 2007-10-28
> **WhiteSphinx said:**
> This apparently works because you are pointing it to an executable file. I've tried pointing it to the lanconfig.sh file but it still doesn't work.  I still have to manually type in "sudo ifconfig eth0 mtu 1492":confused::(

you need to add an entry for ifconfig to sudoers

to find out where ifconfig lives, type in 

```
which ifconfig
``` at the terminal

---

### Post by aos101 on 2007-10-28
I think the better way to set the MTU is to set it in the /etc/network/interfaces file:

[http://ubuntuforums.org/showpost.php?p=582018&postcount=5](http://ubuntuforums.org/showpost.php?p=582018&postcount=5)

Running a script at login to change it doesn't seem the best way to do it.  It's pretty easy to just add the MTU line to the file under the eth0 interface, and that works for me.

---

### Post by WhiteSphinx on 2007-10-28
Okay this is too cool.  Problem solved.  This should work for anyone with an A33G PC Chips Motherboard or for anyone with an SiS190/191 ethernet.

First do this:

```
export EDITOR=gedit && sudo visudo
```

This will bring up the sudoers file.

Replace the following line (because of a bug)

> Defaults !lecture,tty_tickets,!fqdn

with:

> #Defaults !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"

Add this line to the end of the sudoers file:

> username ALL=NOPASSWD: /sbin/ifconfig
Be sure to replace "username" with your own username.

Then open System>Preference>Sessions

Click Add

_N_ame > Configure LAN
_C_ommand > sudo ifconfig eth0 mtu 1492

Now you will be able to access the internet with you SiS190 Ethernet after you restart.

---

### Post by MegaJim on 2007-10-28
Nice, you got a solution worked out from all over :) Glad to help.  Please mark the thread as solved

---

### Post by WhiteSphinx on 2007-10-28
how do I mark the thread as solved?

---

### Post by MegaJim on 2007-10-28
click thread tools on the top right, mark as solved

---

