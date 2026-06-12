---
title: "How to stop auto startup daemons?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by bobmct on 2006-10-27
](*,)  Gentlemen;
I've been using ubuntu (actually Kubuntu) for approx three months now and have grown quite fond of it.  However, one issue that I cannot seem to overcome is the control of what is getting started automatically at boot time. 

I've used boot up manager (BUM) as well as Webmin (start up) and other tools in various attempts to stop these things.  All without success.

Some of the items that I see in when I run "ps -e" are:

kbluetoothd, bonobo-activati, evolution-data-, artsd (multiple times), gam-server, and a host (literally) of other items.  I've tried to search the ubuntu-wiki to identify some of them and those that seemed necessary I've not mentioned.  

So, can someone PLEASE advise as to what one can use to actually stop these daemons from starting in the first place?  Ideas, suggestions and recommendations will be GREATLY appreciated.  Because, even with todays hardware, too many unnecessary daemons and performance goes down the tubes.

Thanks,

B   :confused:

---

### Post by John.Michael.Kane on 2006-10-27
Have you tried this [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Also you can go in adept and search for those packages,and remove them if you know you don't need them. make sure other apps are not dependent on them.

---

