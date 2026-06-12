---
title: "Installing Xubuntu - some questions I have..."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-17
Question # A: It says "cannot find package xubuntu-desktop" when I go "sudo apt-get install xubuntu-desktop". FOrtunately, this one has an easy answer: What needs to be added to my sources.list?

Now the more difficult one (question B, of course): I"ve tried editing my sources.list in numerous ways, but each gets about the same result:

> kdesu kwrite /etc/apt/sources.list

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0


NOte that trying kate without kdesu gets this:

> mkdir: Owner of /tmp/.ICE-unix should be set to root
QPixmap: Cannot create a QPixmap when no GUI is being used
QPixmap: Cannot create a QPixmap when no GUI is being used
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-12553' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-12541' to 'kate'
kate: ERROR: Communication problem with kate, it probably crashed.


while using it with kdesu just gets the first error. kwrite doesn't have this issue, both are the first error...

I'm sure my problem lies somewhere in connecting to X server :0.0, but I can't seem to find a solution to this...

---

### Post by Synth3t1c on 2007-07-17
please post your sources.list here for us to look at.
> sudo kate /etc/apt/sources.list
copy and paste that please


also, try using sudo instead of kdesu

---

### Post by ARandomKid on 2007-07-17
I can't seem to access my sources.list at all...

the command you gave "sudo kate /etc/apt/sources.list" gets me this:

> mkdir: Owner of /tmp/.ICE-unix should be set to root
QPixmap: Cannot create a QPixmap when no GUI is being used
QPixmap: Cannot create a QPixmap when no GUI is being used
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-22171' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
kate: ERROR: KUniqueApplication: Registering failed!
kate: ERROR: Communication problem with kate, it probably crashed.


Using sudo kwrite just gets me this:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0


---

### Post by davidjmayo on 2007-07-17
re-read your other thread [http://ubuntuforums.org/showthread.php?t=502538](http://ubuntuforums.org/showthread.php?t=502538) 

It may be clearer if you tell people you use Knoppix. What is your text editor?

---

### Post by ARandomKid on 2007-07-17
I have kate && kwrite...


And yes, I use Knoppix 3.8

---

### Post by davidjmayo on 2007-07-17
I am trying to help you but never used knoppix.

So you want to edit your /etc/apt/sources.list in Knoppix as root but don't know how to

try these links 
[http://www.knoppix.net/wiki/Root](http://www.knoppix.net/wiki/Root)

[http://www.linuxforums.org/forum/knoppix-help-forum/29814-knoppix-root-password.html](http://www.linuxforums.org/forum/knoppix-help-forum/29814-knoppix-root-password.html)  see #3

hth

EDIT: if the links don't help I got them from  google searching for "knoppix root" and I only looked at the first 2 or 3 links so you may have to look a bit more

---

### Post by ARandomKid on 2007-07-17
> **davidjmayo said:**
> I am trying to help you but never used knoppix.

So you want to edit your /etc/apt/sources.list in Knoppix as root but don't know how to

try these links 
[http://www.knoppix.net/wiki/Root](http://www.knoppix.net/wiki/Root)

[http://www.linuxforums.org/forum/knoppix-help-forum/29814-knoppix-root-password.html](http://www.linuxforums.org/forum/knoppix-help-forum/29814-knoppix-root-password.html)  see #3

hth

EDIT: if the links don't help I got them from  google searching for "knoppix root" and I only looked at the first 2 or 3 links so you may have to look a bit more

I know how to and can get into root and all that, but when I attempt to access sources.list, all that stuff above pops up and I can't even read it, much less edit it.

---

### Post by bodhi.zazen on 2007-07-17
I do not know why date is acting up, but you can access your sources with nano or vim

sudo nano /etc/apt/sources.list


Why are you trying to install xubuntu-desktop on Knoppix ?

---

### Post by ARandomKid on 2007-07-17
> **bodhi.zazen said:**
> I do not know why date is acting up, but you can access your sources with nano or vim

sudo nano /etc/apt/sources.list


Why are you trying to install xubuntu-desktop on Knoppix ?

It's the only version of Ubuntu Feisty my computer can sucessfully run. Not enough RAM for the others...

so I figure I can install xubuntu on here, or am I going about this wrong?

> root@box:/home/alex# sudo nano /etc/apt/sources.list
sudo: nano: command not found
root@box:/home/alex# nano /etc/apt/sources.list
bash: nano: command not found


But "vim" let me in, now I need to figure out how to edit it properly and get the repositories....

---

### Post by bodhi.zazen on 2007-07-18
Well, you can install nano ...

Or here is a crash course on vim ...

To edit type "i"

navigate with with the arrow keys (or page up / page down)

When you are don editing, hit the "esc" key, then shift + :

You will see a : at the bottom left. 

Type wq and enter (wq = write quit)

To quit withou saving changes , hit the Esc key, type shift :, enter q!

HTH

---

