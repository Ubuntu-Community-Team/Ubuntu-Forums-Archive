---
title: "questions about installing and configuring usb dsl drivers"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by zexoc on 2005-11-18
There are several linux version drivers for my usb dsl modem [here](http://eciadsl.flashtux.org/download.php?lang=en)

which kernel does ubuntu 5.10 use?

ubuntu is a debian based, so is the debian i386 one i need?

i also have no idea how to install it.

would someone please offer advice?

thanks

---

### Post by ChrisTheGeek on 2005-11-18
Hi,

Load up a terminal and type:

uname -a

It will come back with some information about your computer including the full kernel version.

You are correct that Ubuntu is debian based so the debian package should work ok for you.  Assuming you are running a 'regular' pc and not a mac or 64 bit processor, then you probably want the file called eciadsl-usermode_0.11-1_i386.deb.  The output from the command above will confirm that for you.

Download this file somewhere on your Desktop, then go to a terminal and type:

dpkg -i ~/Desktop/eciadsl-usermode_0.11-1_i386.deb

Hopefully this should work.  If there are any dependency problems then the site lists a repository address which you could add to synaptic.  Write back if you need help with this.

---

### Post by zexoc on 2005-11-18
[QUOTE=ChrisTheGeek]Hi,

Load up a terminal and type:

uname -a

It will come back with some information about your computer including the full kernel version.[/QUOTE]

this gives me 'command not found'

---

### Post by zexoc on 2005-11-18
I tried: 

```
sudo dpkg -i ~/desktop/eciadsl-usermode_0.11-1_i386.deb
```

and errors saying 'no such file or directory' and 'errors were encountered'.

I'm sure I got the right path and filename.

I also tried opening it wth the Archive Manager, but got 'Archive type not supported'

any suggestions?

---

### Post by zexoc on 2005-11-19
I retried it, I think I didnt use the correct path last time, and this time I got this:

```

(Reading database ... files and directories currently installed.)
Preparing to replace eciadsl-usermode 0.11-1 (using .../eciadsl-usermode_0.11-1_i386.deb) ...
Unpacking replacement eciadsl-usermode ...
dpkg: dependency problems prevent configuration of eciadsl-usermode:
  eciadsl-usermode depends on pppoe; however:
   Package pppoe is not installed.
dpkg: error processing eciadsl-usermode (--install):
  dependency problems - leaving unconfigured
Errors were encountered while processing:
 eciadsl-usermode
```

I guess I needed a pppoe package. 

After reading [this](http://www.ubuntuguide.org/#rp-pppoe) I then download [http://frankandjacq.com/ubuntuguide/rp-pppoe-3.6.tar.gz](http://frankandjacq.com/ubuntuguide/rp-pppoe-3.6.tar.gz) on to another machine since I dont have an internet connection on the ubuntu machine and later copy it onto the ubuntu desktop.

Can anyone please recommend what I should do to install the tar.gz?

---

### Post by zexoc on 2005-11-19
ok that didnt do anything since what I have is a usb dsl modem not an ethernet connection.

this is something thats so much better in winxp, just a matter of plugging in the modem, putting the cd that comes with it and installing all the necessary drivers and config utilities.

I should add that when I plug in the modem, and open the device manager, it sees that its a usb modem, but thats all. Is there someway I can install the driver package through the gui?

Can someone please help?

---

### Post by teaker1s on 2005-11-19
not wanting to dampen your spirits I got as far as installing that driver and I had problems with a bt voyager 105 modem and they were less than helpful lot.
asdl router and ethernet by far the easiest and reliable.
you can  'sudo synaptic' and search for pppoe and pppoeconf when you have dependencies solved it will install fortunately you shouldn't need kernel patch

good luck

---

### Post by bonzodog on 2005-11-19
I hate to say this but usb modems can be a bugger to get working in Linux, I normally advise people that it might be worth obtaining an ethernet modem and router. When my ISP connected me, I actually asked them to make sure that the DSL modem could use ethernet - which it could. It's a very good modem (a Zyxel Prestige 623R-T1). I went down to my local computer store and noted that there were a few DSL modems with ethernet connections available.

---

### Post by zexoc on 2005-11-19
I'm not sure that ethernet and a router would be a simpler option, well not for a novice. Besides I'd rather use the hardware I already have. 

The problem is that the ubuntu guide is for 5.04 and assumes that pppoe is up and running, which in my system it isnt. Infact having had a look inside the pppoe folder everything is locked.

I do feel that this (installating and configurating the usb dsl modem) is something that could easily be solved by an experienced Ubuntu user.

---

### Post by zexoc on 2005-11-19
Anyone?

---

