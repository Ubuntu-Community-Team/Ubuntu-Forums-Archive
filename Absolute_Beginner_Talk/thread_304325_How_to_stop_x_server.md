---
title: "How to stop x server"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by quickk on 2006-11-21
Hi everyone, 

   I was wondering how I could stop the X server.  I'm trying to install nvidia drivers, and I keep getting an error message that an X server is still running.

I've tried:

CTRL-ALT-F1
sudo telinit 3

I still got the same message. 

I've tried CTRL-ALT-BACKSPACE, but then I'm just back to the login screen and I still have an X server.

I've tried
CTRL-ALT-F1
sudo gdm stop

but then I get the message: "aborting: gdm is allready running" (or something like that).  Why the error? Isn't this the whole point, that I'm trying to stop gdm?


Anyway, I really can't figure this out!  Can anyone help?

Thanks!

---

### Post by JNowka on 2006-11-21
CTRL-ALT-F1

sudo /etc/init.d/gdm stop

good luck :)

---

### Post by quickk on 2006-11-21
Thanks!

"sudo gdm stop" wasn't working but "sudo /etc/init.d/gdm stop" did the trick.

---

### Post by NT4usB on 2006-11-21
> **JNowka said:**
> CTRL-ALT-F1

sudo /etc/init.d/gdm stop

good luck :)

When I try to stop X, I cd /etc/init.d/
Then I sudo gdm stop
and I get the gdm is already running bla bla bla...

Apparently (for me, anyway) changing to the directory first and then stopping gdm is not the same as sudo /etc/init.d/gdm stop
But then, I haven't tried sudo /etc/init.d/gdm stop so I can't say if that'll work.
Should either way give the same result?

---

### Post by procco on 2006-11-21
If you change directories to /etc/init.d then type gdm, you are executing gdm from /usr/sbin.  
To verify this, type:
which gdm

It will say:
/usr/sbin/gdm 
Which is the default path for this application - no matter which directory you are in or whether the command is in that directory or not.

If you want to run gdm from /etc/init.d, change to that directory and type:
./gdm 
which will execute from the current directory, not the default path.  Alternatively you can explicitly state where to run the command from:
/etc/init.d/gdm.


Sorry to make this more confusing than it really is.  Basically, if you type a command it will run from your default path.  If you have a command you want to run from your present directory and NOT default path, type ./command-name.

---

### Post by NT4usB on 2006-11-22
I guess I think I kinda' understand... At least I get why what I did didn't work.
I'm still stuck in Windows thinking. You want to run an application you either browse to the folder it's in and run it there or type the path\to\app\ in the runbox (or just click the icon shortcut *g*)
Thanks for the explanation.

---

### Post by steve.horsley on 2006-11-22
The only difference to Windows here is that in Linux, the current directory "." is not normally in your path, so navigating to a directory makes no difference. Windows users are definitely not used to typing ./appName, but it is common on *nix.

---

### Post by streeto on 2006-11-22
I think the recommended way of running/stopping system services is

sudo invoke-rc.d servicename start|stop|restart

I.e.

sudo invoke-rc.d gdm stop

This the way I do it, not necessarily the best way. ;)

---

### Post by ubm on 2007-07-22
Thank you to all who posted/responded to this thread... I was having a hell of a time trying to get the Nvidia script to run and install the latest drivers. It seems that by stopping gdm 

ctrl alt f1
/etc/init.d/gdm stop 

i was able to run the script.

Thanks guys.

---

### Post by kaltenba on 2007-10-18
Hello,
I've the same problem. I stopped gdm (stopping gdm [OK]) an then I tried to install the NVDIA driver. The same error message occurred (...there is still a x server running ....).
I don't know what to do.
Do I have to kill/stop some other processes?

Best regards, Tom

---

### Post by pdoxey on 2007-12-17
Hi All,

I have tried all of the mentioned commands, and gdm refuses to die.  It just restarts every time. What is the method to kill it completely, including X?  I'm trying to install the correct Nvidia driver for the at least 6th time at least but it won't install while X is running.  The last upgrade killed my screen resolution and I'm back to 800 x 600.  

thanks,  paul.

---

### Post by pdoxey on 2007-12-17
the best way that I have found is running 'sudo rcconf' from a terminal window, unchecking 'gdm' or whatever your x session is, and then restarting the computer.  that prevents the GUI from starting.  whenever i tried the gdm stop command it would error out or attempt to restart immediately.  rcconfig seems the best way.

Paul

---

### Post by NTolerance on 2008-02-19
> **pdoxey said:**
> the best way that I have found is running 'sudo rcconf' from a terminal window, unchecking 'gdm' or whatever your x session is, and then restarting the computer.  that prevents the GUI from starting.  whenever i tried the gdm stop command it would error out or attempt to restart immediately.  rcconfig seems the best way.

Paul

Thanks, this works well if you get an "xserver is running" error when attempting to manually install the NVidia drivers from their website.  This is much cleaner than having to muck around with runlevels or edit critical startup text files.

---

### Post by Lukky on 2008-05-17
ok I found my Syntax error. It seems I didnt have the "L" in linux capitilized. So the command it working but know I get an No Matching Kernel interface was found. What does that mean. It wanted to connect to the internet and download it but offcourse I cant make my wireless work yet so that didnt work. Did I get the wrong driver or is this Kernel just too new?

Thanks Dustin

---

