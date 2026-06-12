---
title: "Monitor sleep time always resets in KDE"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Maxwell7 on 2007-01-10
Hello everyone, 

I'm still quite a beginner with Linux, but I can manage to do most things. But I have this very peculiar problem - i guess since i upgraded to edgy. It is as follows: 

I am running Edgy on my Dell Inspiron laptop, which i dual-booted with winxp (only used occasionally for games). I have both Gnome and KDE installed (ubuntu-deskop / kubuntu-desktop package) so i can switch whenever i like. 

Now I would like my monitor to go into power-saving state (i.e. turn off) after 15 mins of inactivity. This works perfectly in Gnome. I set the screensaver to 10 mins, and poweroff to 15. Great so far. 

But when I try the same in KDE, the monitor power-off time ALWAYS resets to 5 hours, if i reboot my pc. Regardless of what value I put in there. What can cause this ? Just to be perfectly clear, as long as I don't reboot my pc, the monitor powers off just as I set it up. But not after rebooting when it sets to 5 hours.  ](*,)  

Has anyone had a similar problem ? Is it because of the  combination Gnome/KDE ? :-k  Any help would be greatly appreciated.

---

### Post by kogber on 2007-01-10
This is a known bug that I also recently noticed after installing kubuntu.  There does not appear to be an elegant solution yet, but I am confident it is only a matter of time till it is resolved.  For now, you can try this workaround 

[http://ubuntuforums.org/showthread.php?t=323860&highlight=monitor+power+save](http://ubuntuforums.org/showthread.php?t=323860&highlight=monitor+power+save)

I cannot confirm that it works, since I have not tried it myself ( I just close the lid on my laptop for now).

---

### Post by ajm2005 on 2007-01-22
I have exactly the same problem, I just googled for solutions, google led me to this thread..

---

### Post by Maxwell7 on 2007-01-23
I didn't find any other solution either, except the one that kogber explained here (thanks for that). But as it involved changing the Xorg.conf I decided to leave it like this. (I have some bad experiences editing that file). 

Hopefully this will be fixed in the next release of KDE... Or is it strictly a Kubuntu problem?

---

### Post by heronbas on 2008-04-11
I found another way round the problem with kde not keeping the monitor power-saving settings between logins/re-boots. I wrote a small bash script which goes in your kde autostart directory (~/.kde/Autostart)
It automatically runs once after logging in and sets the monitor suspend time out. The script is:-

#########################################################

#!/bin/bash

wait_run=25

wait_suspend=600

sleep $wait_run

echo Setting DPMS monitor suspend time-out
xset dpms $wait_suspend $wait_suspend $wait_suspend

#########################################################

Save it as set_suspend.bash in ~/.kde/Autostart
Change permissions on the script to read and execute for everyone
Notes on script:-

wait_run=25
This makes the script wait for 25 seconds before running the xset command as when you login something in kde resets the suspend timeout so this is to makes sure what the script does doesnt get reset. You may need to increase this value on a slow computer.

wait_suspend=600
This sets the monitor suspend timeout value to 10 mins (600 secs). Change this value to whatever you require.

---

### Post by Maxwell7 on 2008-04-11
Thanks for this script. It's a nice workaround that doesn't require too much editing. :-)

---

