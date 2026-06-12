---
title: "Processor scaling"
date: 2011-03-02
forum: Apple Hardware Users
---

### Post by rsavage on 2011-03-02
Hi, I'm after some advice about CPU frequency scaling on a G4 1.2GHz ppc. Following the advice of this post ([http://art.ubuntuforums.org/showthread.php?t=1498559](http://art.ubuntuforums.org/showthread.php?t=1498559)) I installed cpudyn to do the job. However, for me I think it is switching too much. For example, even when the computer is idle and the system monitor applet is barely registering anything it is still cycling the processor up and down.
 
So I've now installed powernowd and followed the instructions on the known issues page ([https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)). This solves the cycling up and down when idle, but I think it could do with a bit of tweaking to make it more responsive. For example, the polling could be reduced (initially it is set to every 1 second!). Also, I'm not sure but it doesn't seem to detect root processes (for example, when the update manager was maxing out the processor it refused to step up). So I think the 80/20 percentage levels could be lowered. Running "man 1 powernowd" in a terminal gives the options that can be set. I think the file /etc/default/powernowd contains the startup options. It's hard to tell because I thought running the command "powernowd -v" would display the current options (which it does) but it sets them all to the standard values first! 
 
So I'd welcome the advice of anyone using powernowd and what values they use. Also, are there any tweaking options for cpudyn as I haven't looked into that yet? Basically what is best to do/use? 
 
Finally, has anybody tried out the ondemand governor using the advice in this post ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706)?]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706%29?") Did ondemand used to work for ppc in old kernels?
 
EDIT: The reason the root processes did not cause a step up was because the default setting is for 'nice'd processes not to be used in the calculations.

---

