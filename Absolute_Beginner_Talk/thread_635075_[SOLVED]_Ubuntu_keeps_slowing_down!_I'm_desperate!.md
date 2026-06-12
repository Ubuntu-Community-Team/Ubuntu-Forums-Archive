---
title: "[SOLVED] Ubuntu keeps slowing down! I'm desperate!"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-08
I've reinstalled Ubuntu for the thrid time in 2 days and the system keeps slowing down after the first boot. It starts just a few seconds after booting, getting slower and slower each second. Then it remains like this forever.

When I reboot the system it takes more than 5 minutes to boot. Then, any app takes at least 10 seconds before it loads.

In the first boot the progress bar under the logo doesn't even go to the end before the login process begins. Then, in the following boots the progress bar got to the end (very, very slow) and then freezes for a while. Then the gnome terminal appears, showing app that are being loaded. The last entry is: starting common unix printing system: cupsd, which takes forever.

What's the problem?

I have a fairly fast PC: dual core 1.86, 2GB RAM, two 250GB HDD's.

I have even set a 2GB swap!

I've checked the monitor and RAM is not the issue here. I have plenty! And CPU usage is around 2% for each processor.

What puzzles me is that the system did work properly the first day..... and I even rebooted many times then. Another thing that strikes me is that he problem persists even though I have reinstalled the whole system from scratch 3 times!!!....... formatting all the pertitions!!!

I'm trying Ubuntustudio.

Also, I still can get it to connect to the internet. But I don't think this has anything to do.

I've been posting about this problem but can't get anybody to help me through it.

Please, help me! I'm loosing my mind here!

---

### Post by agerfe on 2007-12-08
sorry, wrong typing, should say "I can't get it to connect to the internet" :)

---

### Post by agerfe on 2007-12-08
Ubuntu is soooooooo slow!!!!!

I've posted several times in the beginners forum but still no answer. I appologize for posting this thread but I just don't know what else to do. 

Since reposting is not allowed I'll just indicate the link in the beginners forum:

[http://ubuntuforums.org/showthread.php?t=635075]("http://ubuntuforums.org/showthread.php?t=635075")

If you can please take a look at my posting.

Thank you!

---

### Post by tyggna1 on 2007-12-08
With Gutsy--I've been having that same problem--but with me, it indicates that nautilus is using exhorbant amount of resources.  CLI program top might help.  For me a 
```
sudo dpkg-reconfigure xserver-xorg
```
was all it took to fix.  If you run that from the command line only (ctrl-alt-f1) and then go through the setup, that can help things along quite a bit (alt-f7 goes back to normal).  

WARNING:  If you use restricted video drivers, you'll have to re-enable them, but I suspect that was part of my original problem

---

### Post by agerfe on 2007-12-08
Thank you!
However, I became so desperate that I just replaced Ubuntustudio with Ubuntu.
Ubuntu doesn't show the problem so I guess it was a bug in Ubuntustudio.
Bad part is that now I have to Install all those wonderful app's that come with Ubuntustudio. Maybe I'll just wait for the next version.
In the meantime I'll be able to become part of the Linux experience through Ubuntu.
Thanks again for replying to my post. Almost thought nobody would. :)

---

### Post by cmnorton on 2007-12-08
It seems like you solved your problem. You installed Ubuntu, replacing Ubuntu Studio. What are the hardware requirements for Ubuntu Studio? Was your hardware just meeting those requirements or over?

It seems like after installing Ubuntu, things are slowing down again. I suggest posting output of your logs, dmesg, /var/log/messages, and /var/log/syslog

---

### Post by agerfe on 2007-12-09
Yesterday I discovered the problem. It seems there's a bug in Ubuntu. I posted a thread in the launchpad. Here's the link: [https://bugs.launchpad.net/ubuntu/+bug/174989]("https://bugs.launchpad.net/ubuntu/+bug/174989")

---

