---
title: "static ip address in gutsy- booting problem"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by bhi24 on 2008-03-26
dear all,

i have recently installed gutsy 7.10 in my sony vaio VGN-NR260EW laptop, from the LiveCD. i configured the network manager for a static ip address in my lab, and i could connect to the internet after a reboot.

however, once back from the lab, i am trying to boot my machine (now no more connected with an ethernet cable), and it wouldn't load the desktop.pressing CTRL+ALT+F1 gives a login prompt for the machine, and on logging in - i get a command line prompt. the desktop is missing, and hence i can't see network manager in order to configure it.

is there a way to configure the network manager in a way so that it doesn't keep searching for the network connection ( which is associated with the static ip address) while booting when there is no ethernet cable attached?

many thanks for any help!

---

### Post by spiderbatdad on 2008-03-26
Seems like the Network issue is unrelated to the loss of Desktop Environment. try running ```
sudo /etc/init.d/gdm start
``` and see if your desktop comes up.

I'm guessing the network "static" address should be set in your router and roaming enabled for eth0.
If this is not an option for your lab, Create a new wired connection for the lab.

---

### Post by bhi24 on 2008-04-03
hi spiderbatdad, 

thanks for the prompt reply - i eventually figured that it was not that my desktop would not load at all, but it would take about 15 minutes to do so. once loaded, i realised that i could get  switch between the gnome desktop and the terminal mode with CTRL+ALT+F7.
i am now going to try out the solution given in [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903) to see if i can resolve the slow boot issue.

thanks again!

---

### Post by Tatty on 2008-04-03
> **bhi24 said:**
> hi spiderbatdad, 

thanks for the prompt reply - i eventually figured that it was not that my desktop would not load at all, but it would take about 15 minutes to do so. once loaded, i realised that i could get  switch between the gnome desktop and the terminal mode with CTRL+ALT+F7.
i am now going to try out the solution given in [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903) to see if i can resolve the slow boot issue.

thanks again!

It sounds like it might be a network manager issue.  I know it gets blamed a lot for slow boots, and is a little buggy.

First confirm if it is a problem with network manager by installing bootchart, rebooting, then checking the graph in /var/log/bootchart/

if so then it might be worth uninstalling network manager to see if that helps.

---

### Post by bhi24 on 2008-04-09
hi tatty,

thanks for the tip - it seems like it was a network manager issue. i installed wicd following the instructions from [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php), and it automatically removed network manager. plus of course, i used ndiswrapper (using chalewa's solution on [http://ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ubuntuforums.org/showpost.php?p=3868406&postcount=48)) to get wireless working on my sony vaio VGN-NR260E machine.

all seems to be well now, *touchwood*.
thanks again for the helpful suggestion.

---

