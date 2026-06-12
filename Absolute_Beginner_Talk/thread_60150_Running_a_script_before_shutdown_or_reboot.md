---
title: "Running a script before shutdown or reboot"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by ummo on 2005-08-26
i would like to run a script that does some logging of data automatically whenever i shutdown or reboot my system.

The script is already made and works fine however i am at a loss as to how to have it automatically run right before the shutdown and reboot commands are run.

I initially thought of adding the following aliases to my /root/.bashrc file:

```
alias shutdown='echo running script...; /home/user/scripts/script.py; echo Done; shutdown'
alias reboot='echo Running script...; /home/user/scripts/script.py; echo Done; reboot'
```

however executing sudo reboot does not run my script, just reboots like normal.

Also i have no idea what happens when the system is shutdown from the Gnome Panel's System menu.  And that is fairly important to me sincie i often use both the shutdown option from the menu as well as the command line method.

Am i not setting my aliases correctly?
Is there some universal system-wide shutdown / reboot script that lists tasks to do on those events?

---

### Post by Juergen on 2005-08-26
I think you have to become familiar with the runlevels.
[This](http://newbiedoc.sourceforge.net/system/runlevels-intro.html) seems to be a nice intro. (a bit old, though. So some locations/commands might have changed... )

In short you should put your script into /etc/init.d (as root) and then set up the right links in /etc/rcX.d where you want them executed when the runlevel changes.

The shutdown-runlevel is 0, but maybe you also want to do your logging for a change from runlevel 2 (Debian/Ubuntu default for normal operation) to 1 (single user)?
Thats up to you. Just create the links.

---

### Post by cwaldbieser on 2005-08-27
[QUOTE=ummo]
Am i not setting my aliases correctly?
Is there some universal system-wide shutdown / reboot script that lists tasks to do on those events?[/QUOTE]
If you create a function or an alias in bash, and you want to make sure the command you issue is what you expect it should be, the type command will help you:
```

$ hello () { echo Hello'!'; }
$ alias hi="echo Hi."
$ hello
Hello!
$ hi
Hi.
$ type hello
hello is a function
hello () 
{ 
    echo Hello'!'
}
$ type hi
hi is aliased to `echo Hi.'

```

---

### Post by ummo on 2005-08-29
Thanks for the help guys.  I think I've got it working now.
 :grin: 
For completeness sake I'll post what i did, for anyone else who wants to do something similiar:
From the link Juergen provided I learned to put my script: scriptname.blah in the /etc/init.d directory and create a link to the script named K02scriptname.blah in both the /etc/rc0.d/ and /etc/rc6.d/ directories.

Runlevel 0 is halt.
Runlevel 1 is single-user.
Runlevels 2-5 are multi-user.
Runlevel 6 is reboot.
There are /etc/rc#.d/ folders for each # of the Runlevels.

Normally during typical ubuntu use the computer is at Runlevel 2, at least thats the default setting in my /etc/inittab file.   
 Runlevel 0 shuts the computer down and runlevel 6 reboots.    /etc/rc0.d/ and /etc/rc6.d/ contain links to the scripts to be executed when switching to those runlevels.   The names of the links in these folders begin with either a K or S followed by some 2-digit number and then the name of the script in /etc/init.d/ they are linked to.  The K stands for kill and indicates that init will send the stop argument to the script linked to, S is for start and init sends the start argument to the script if the link begins with S.  The K links are run first in the order of the 2-digit numbers that follw the K followed by the S scripts in the same way.  Following the digits is the exact name of the script in the /etc/init.d/ directory.

So since i wanted my script run at shutdown and reboot I named the links in the /etc/rc0.d/ and rc6.d/ directories as a kill script with a low number even though my script doesnt kill any processes and doesnt use the 'stop' argument given to it.   I wanted my script to run before all of the services my script utilizes are stopped for shutdown.  So now it runs right after gnome is killed and before all the other vital processes are stopped everytime my system shuts down.

I hope this makes sense and definitely check Juergen's link for the real story.

---

### Post by d00d on 2006-05-08
My question is related to this only...

This is an example when one wants to run the script ***after*** gnome has exited, what do we do if we want to run the script ***before*** Gnome exits but after we have either killed the window manager of shut it down using the Shutdown/Logoff dialog.

---

### Post by coquinho on 2006-05-10
I think you can influence the order in which programs are shutdown with the runlevel system. Check [this part]("http://newbiedoc.sourceforge.net/system/runlevels-intro.html#STARTSTOP") of juergens description...

---

