---
title: "Unbutu on macbook pro X Server Failed to Start"
date: 2007-04-22
forum: Apple Intel Users
---

### Post by furbys on 2007-04-22
Hello all,

Bit new to Linux and caught up in all the Ubuntu stuff I thought I'd give it a go my macbook pro.

Made a partition and installed rEFIt. Was told I needed X11, so installed that  and ran software update

Not so bad so far. Booted the Cd and got an error page that Says "Failed to start X Server" and then error for the xorg file?

I went to the directory where the logs and conf file were stated, but they're both not there?

The install in Vmware fusion  was flawless and really quick, what am I doing wrong. I'm getting a bit frustrated but don't want to give up. :(

Help. Please

---

### Post by ronocdh on 2007-04-22
> **furbys said:**
> Hello all,

Bit new to Linux and caught up in all the Ubuntu stuff I thought I'd give it a go my macbook pro.

Made a partition and installed rEFIt. Was told I needed X11, so installed that  and ran software update

Not so bad so far. Booted the Cd and got an error page that Says "Failed to start X Server" and then error for the xorg file?

I went to the directory where the logs and conf file were stated, but they're both not there?

The install in Vmware fusion  was flawless and really quick, what am I doing wrong. I'm getting a bit frustrated but don't want to give up. :(

Help. Please
Welcome! Perhaps [this thread]("http://ubuntuforums.org/showthread.php?t=398959") will treat you well. =) I agree that the VMWare Fusion installation is incredible slick, but wouldn't you rather have Ubuntu running natively? ;)

Post back with any more problems, and the community shall sic themselves on them like so many nanobots upon a cancerous tumor.

---

### Post by furbys on 2007-04-23
lol, thanks for the reply. I definitely want to get it installed natively.

Tried what was posted there but no joy. 

The X server thing fails so, keep hitting ok, and there is a bit more of code and then it gets to:

```
running local boot scripts (/etc/rc.local)
``` and then nothing seems to happen, the _ keeps blinking so it doesn't seem to have crashed but it never seems to get past that.

Should I be waiting a while for it to pass that stage? I typed in all the commands from the other thread at this point but again nothing seems to happen.

It doesn't tell me what's wrong so I am stuck again

---

### Post by ronocdh on 2007-04-23
> **furbys said:**
> lol, thanks for the reply. I definitely want to get it installed natively.

Tried what was posted there but no joy. 

The X server thing fails so, keep hitting ok, and there is a bit more of code and then it gets to:

```
running local boot scripts (/etc/rc.local)
``` and then nothing seems to happen, the _ keeps blinking so it doesn't seem to have crashed but it never seems to get past that.

Should I be waiting a while for it to pass that stage? I typed in all the commands from the other thread at this point but again nothing seems to happen.

It doesn't tell me what's wrong so I am stuck again
Hm well what's happening there is you're not getting back to the command prompt, which has happened to be several times when X fails like that. I imagine I succeeded in getting back to the command prompt by being polite and actually viewing the output, pretending to read it over, viewing the detailed output, pretending, then saying OK. 

If that still doesn't work, meaning you still can't type commands, I recommend you just install from the alternate CD. That's have I've done it, twice now, actually, on my MacBook Pro because it's just too much of a pain to try and use the live CD.

---

### Post by furbys on 2007-04-23
Progress :D The Alternate disc seemed to actually install!

But, I'm now back to my initial problem. 

It boots into Ubuntu and to the command line but it say the xserver fails to start. 

I get the following error
```
(EE) VESA(0) : No Matching modes
(EE) Screen(s) found but none have a usuable configuration
```

So I entered ```
sudo apt-get install xorg-driver-fglrx
```

and get the error that it couldn't find the package. What now? I get the feeling maybe I'm not ready for Linux, should it be this tricky?

---

### Post by ronocdh on 2007-04-23
> **furbys said:**
> Progress :D The Alternate disc seemed to actually install!

But, I'm now back to my initial problem. 

It boots into Ubuntu and to the command line but it say the xserver fails to start. 

I get the following error
```
(EE) VESA(0) : No Matching modes
(EE) Screen(s) found but none have a usuable configuration
```

So I entered ```
sudo apt-get install xorg-driver-fglrx
```

and get the error that it couldn't find the package. What now? I get the feeling maybe I'm not ready for Linux, should it be this tricky?
Totally bizarre that it didn't find this. Are you plugged into a DHCP-enabled ethernet connection? Wireless definitely doesn't work out of the box, so you'll need to be on ethernet for a while till you get it working. What is the exact message you get? Could you transcribe it for us?

---

### Post by Technoviking on 2007-04-23
This is a known bug. Here is a fix for it.
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by furbys on 2007-04-23
I wasn't plugged in while I was setting it up and I picked my wifi connection (which has WPA)  during the setup. Seems silly now.

The messages after I enter that command?

```
Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package xorg-driver-fglrx
```

Do I need to reinstall and select the ethernet connection? Seems a more sensible idea now.

Thanks for the help by the way, it is really appreciated.

I'm on a 1.83ghz core duo macbook pro btw

---

### Post by ronocdh on 2007-04-23
> **Mike said:**
> This is a known bug. Here is a fix for it.
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
And here I thought it was just me! Does that mean that all you other MBP C2D users here used the alternate CD as well? I thought I was weird. :lolflag:

---

### Post by furbys on 2007-04-24
Yay \o/ it installed! Everything seems to be working from the get go as well :D

Thanks for the help ronocdh, I may have given up without you but sure I'll be posting back here soon enough.

---

### Post by Brian Kueck on 2007-07-06
If you install Ubuntu and it boots to the * Running local boot scripts (/etc/rc.local) message and shows a status of "[ OK ]", then press the ENTER key. It will load the version number, your maching name and the server login prompt. I just did that and it worked for me. You don't have to wait an hour. The terminal is waiting for you to input your login info. Hope that saves someone some time in the future! :-)

Brian

---

