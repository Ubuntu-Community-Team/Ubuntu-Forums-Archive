---
title: "Disable Bluetooth services from terminal plzz"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by abedbajia on 2007-11-26
i installed ubuntu 7.10 on my laptop hp dv9500

it all worked fine but when i restart the load screen reaches the end and the screen goes black to where they say

starting bluetooth services and stops there

so i want to sisable bluetooth services but i cant start ubuntu desktop
so i want to it in recovery mode 

does anyone know to disable **_bluetooth services_** using terminal
plzzzzzzz

---

### Post by bodhi.zazen on 2007-11-26
[http://ubuntu-tutorials.com/2007/11/24/disable-bluetooth-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/11/24/disable-bluetooth-on-ubuntu-710/)

---

### Post by luisfcup on 2007-11-26
Try to uninstall the bluetooth packages from terminal:
```
sudo apt-get remove bluetooth
sudo apt-get remove bluetooth-alsa
```

If the problem was on bluetooth packages this should be enough. You can always reinstall if you have bluetooth equipment, try updating the packages.

---

### Post by abedbajia on 2007-11-28
i tried the first one 

putting bluetooth on blacklist it didnt work\

i also tried

sudo /etc/init.d/bluetooth stop

it says stoping bluetooth services and freezes thanks anyway

i try to remove blue tooth

post soon

---

### Post by abedbajia on 2007-11-28
hey i tried to remove bluetooth packeges as to your code it didnt work i

 need to stop bluetooth services bec i cant start ubuntu except in 

recovery mode plzz anything

---

### Post by Dedoimedo on 2007-11-28
Hello,

All services have start and kill scripts in /etc/rc.d directories.

The sub-directories include scripts for each run-level, 0-6.
The start scripts begin with S and a number, indicating priority 0-99.
The kill scripts begin with K and a number, indicating priority 0-99.

Example: in runlevel 5 - the normal daily level - you might find S86ppp, for example.

In order to prevent a service from starting in a certain runlevel, simply delete or rename the script of that service. You will not be touching the service itself - it is located in etc/init.d

This might help you keep bluetooth from starting.

Of course, the best thing is to backup the script before proceeding.

Cheers,
Dedoimedo

---

### Post by bodhi.zazen on 2007-11-28
> **Dedoimedo said:**
> Hello,

All services have start and kill scripts in /etc/rc.d directories.

The sub-directories include scripts for each run-level, 0-6.
The start scripts begin with S and a number, indicating priority 0-99.
The kill scripts begin with K and a number, indicating priority 0-99.

Example: in runlevel 5 - the normal daily level - you might find S86ppp, for example.

In order to prevent a service from starting in a certain runlevel, simply delete or rename the script of that service. You will not be touching the service itself - it is located in etc/init.d

This might help you keep bluetooth from starting.

Of course, the best thing is to backup the script before proceeding.

Cheers,
Dedoimedo

The default run level in Ubuntu is 2

You can also use update-rc.d

If you manually update the scripts, you should not delete links in the various runlevels, rather since *nix is case  sensitive, change them from Sxxx to sxxx (just change the large S to a small s).

---

### Post by Dedoimedo on 2007-11-28
Hello,
I did write delete OR rename ... Plus, I advised backing up, which is not a bad thing ever ...
As to runlevel, well I assumed it was kind of standard, just like the default shell...
Anyhow, thanks for the clarification.
Cheers,
Dedoimedo

---

### Post by abedbajia on 2007-11-29
i couldnt do anything of what u all said but thanks anyway

i solved the problem 
i booted in recovery mode

than i wrote this code:> sudo pico /etc/init.d/bluetooth

this opens the bluetooth code so i wrote at the top of the code :

[SIZE="4"]exit 0[/SIZE] and saved reboot  and it worked 

than i was able to disable blutooth services from desktop and returned the code to what it was

hope this helps anyone who had my problem

---

