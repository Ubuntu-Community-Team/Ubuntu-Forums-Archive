---
title: "[SOLVED] Start Hiawatha upon reboot"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by mnealon on 2007-09-08
I am struggling to get [Hiawatha ]("http://hiawatha.leisink.org/index.php?page=hiawatha")running under Ubuntu.

I need to have the server startup at boot time. This is however a desktop installation, not a server installation, I want to allow the desktop to function as a local web server for web site development training.

I seem to have successfully built the program, and I believe that I have correctly edited the startup script, which currently resides in /etc/init.d (I did need to run make as sudo in order to build, although this is not related to the problem I believe)

My problem is that I need the server to startup upon reboot, (thus without a user logged in).

I seem to need to run the script as root (sudo /etc.init.d/hiawatha) in order to get the server started, once logged in as user.

Is there something I am missing here? It should be possible to start the server as a service under Ubuntu upon reboot, shouldn't it? Just for good measure I will admit to having almost zero experience with Linux, and have only just installed Ubuntu 7.04 (OK 6.10 updated to 7.04 without problem).

Do I need a symlink in one of the rcX.d folders? and if so, which one? All of them for good measure? and how do I create a symlink in these folders?


Can anyone who has successfully installed Hiawatha under Ubuntu lend a hand?

If I try running the script as user I receive the error 
> Error binding 0.0.0.0:80
bind http: permission denied

Which led me to believe that I needed to be root to start the server.

sudo /etc/init.d/hiawatha works, the server begins and I can access the web site from a second computer on my network. This however requires my password and is therefore unsuitable for the occasion when the computer is rebooted and not yet logged in/accessed.

Thanks
Mal

---

### Post by kane77 on 2007-09-08
> **mnealon said:**
> I am struggling to get [Hiawatha ]("http://hiawatha.leisink.org/index.php?page=hiawatha")running under Ubuntu.

I need to have the server startup at boot time. This is however a desktop installation, not a server installation, I want to allow the desktop to function as a local web server for web site development training.

I seem to have successfully built the program, and I believe that I have correctly edited the startup script, which currently resides in /etc/init.d (I did need to run make as sudo in order to build, although this is not related to the problem I believe)

My problem is that I need the server to startup upon reboot, (thus without a user logged in).

I seem to need to run the script as root (sudo /etc.init.d/hiawatha) in order to get the server started, once logged in as user.

Is there something I am missing here? It should be possible to start the server as a service under Ubuntu upon reboot, shouldn't it? Just for good measure I will admit to having almost zero experience with Linux, and have only just installed Ubuntu 7.04 (OK 6.10 updated to 7.04 without problem).

Do I need a symlink in one of the rcX.d folders? and if so, which one? All of them for good measure? and how do I create a symlink in these folders?


Can anyone who has successfully installed Hiawatha under Ubuntu lend a hand?

If I try running the script as user I receive the error 

Which led me to believe that I needed to be root to start the server.

sudo /etc/init.d/hiawatha works, the server begins and I can access the web site from a second computer on my network. This however requires my password and is therefore unsuitable for the occasion when the computer is rebooted and not yet logged in/accessed.

Thanks
Mal

I don't have experience with hiawatha, but to run a script on startup even with no users logged in put it into rc.local

---

### Post by schorsch on 2007-09-08
Just leave it in "/etc/init.d", that is the place start scripts are living in.
```
sudo ln -s /etc/init.d/hiawatha /etc/rc2.d/S99hiawatha
```
will add a link from the default runlevel under ubuntu to your start script so that hiawatha will be started on every boot. The number (in my case 99) used depends on the time when hiawatha should be started. "S99" means start it after anything else is already running. You can put it in the starting order whereever you want to but take care of dependencies. It would not make sense to start it before the network starts ...

---

### Post by mnealon on 2007-09-08
> **schorsch said:**
> Just leave it in "/etc/init.d", that is the place start scripts are living in.
```
sudo ln -s /etc/init.d/hiawatha /etc/rc2.d/S99hiawatha
```
will add a link from the default runlevel under ubuntu to your start script so that hiawatha will be started on every boot. The number (in my case 99) used depends on the time when hiawatha should be started. "S99" means start it after anything else is already running. You can put it in the starting order whereever you want to but take care of dependencies. It would not make sense to start it before the network starts ...

This doesn't work.

I did find an error with the script, but this did nopt vorrect the problem.

How do I make the script run **before** the graphic manager, then I could see the output of the script in text mode?

---

### Post by schorsch on 2007-09-08
The first line of your script should look like
```
#!/bin/bash
```
You can edit it to look like
```
#!/bin/bash -x
```
This way you will get the output of the script running  step by step but only on the text console #1 which is available via pressing "CTRL-ALT-F1" after the gui has started. 
On my system GDM is started via "/etc/rc2.d/S13gdm" so you might put the starting link a little bit to the front .... perhaps S12hiawatha?

---

### Post by mnealon on 2007-09-09
Thanks for the help. I finally managed to trace the problem to the script. I have, in the script, the path as > PATH="/bin:/usr/bin:/sbin:/usr/sbin:/usr/local/sbin" but I needed to specifically point to a program>  /usr/local/sbin/wigwam -q in order to get the server to start up.

In any case, thanks for the help, it now functions as required.

Mal

---

### Post by schorsch on 2007-09-09
Glad to hear that. Could you please mark this thread as solved as it may help others, too?

---

