---
title: "can't start nautilus w/o internet"
date: 2007-10-17
forum: Apple PPC Users
---

### Post by crm.114.ope on 2007-10-17
I've been running ubuntu for a while on my home machine. Recently I came into possession of a number of iMac blueberries and have installed ubuntu 6.06 on them. The machines work great when connected to the internet, however nautilus doesn't boot when they aren't, instead I receive the following three error messages:

There was an error starting the GNOME Setting Daemon. 
Some things, such as theme. so0unds, or background settings may not work correctly. 
The Settings Daemon restarted too many times 
the last error message was: 
System exception:IDL: omg.org/COBRA/COMM_FAILURE:1.0
GNOME will still try to restart the Settings Daemon next time you log on.

Nautilus can't be used now, due to an unexpected error 
(details) 
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem. 

There was a problem registering the panel with the bonobo activation server. 
The error code is: 3 
The panel will now exit.

As it doesn't need Nautilus the failsafe terminal works just fine. Any help getting nautilus to work would be appreciated, thanks in advance.

P.S. [this poster]("http://ubuntuforums.org/showthread.php?t=277337") seemed to have a related problem but am not sure how to implement this solution. I am also hoping for a more permanent solution a I won't be around them.

---

### Post by guidop on 2007-10-18
If you are having this issue because time (date) is set incorrectly, you may need to replace the PRAM battery in these iMacs.  Since the tray loading blueberry iMacs were made in 1999, and the slot loading ones in 1999-2000, it's likely the batteries are run down.   

If you boot without the internet connection, and can login and open a terminal, you should be able to test this using the date command:
```
$ date
Wed Oct 17 21:24:10 PDT 2007
$

```

Anything far from reality indicates this is likely your problem.

The default Ubuntu install will use the internet to retrieve and set the time each time it boots, so that would explain why it works OK when you boot with a live connection.


Here's a link to one place that sells the part, so you can see what the battery looks like:

[http://eshop.macsales.com/item/Newer%20Technology/BAA36VPRAM/]("http://eshop.macsales.com/item/Newer%20Technology/BAA36VPRAM/")

Post back if this is the problem, and you need take apart instructions.  I think I have the info  somewhere in my files.

---

### Post by crm.114.ope on 2007-10-18
Thanks so much, apparently the computer thinks it is 1904. I'll get the part as soon as I can, however I was wondering if their is a way to manually set the date as a proof of concept (I'm not buying the part myself and need to show the powers that be that this will work.) Thanks again.

---

### Post by guidop on 2007-10-18
I haven't done it in Ubuntu, but on other Linux/Unix systems I've used something like:

```
$ sudo date 101814292007      # Set date to Oct 18 14:29 (local) 2007
```

I suggest reading the manual page (man date) on the specific machine, just in case there are subtle differences.

I hope you have the slot-loading iMacs.  It's much easier to replace the battery on those, compared to taking apart the older tray-loading models. 
(Xubuntu runs quite well on my 400 MHz iMac with 640 MB RAM.)

---

### Post by crm.114.ope on 2007-10-18
Thanks so much that works great. By the by they are slot loading iMacs.

---

