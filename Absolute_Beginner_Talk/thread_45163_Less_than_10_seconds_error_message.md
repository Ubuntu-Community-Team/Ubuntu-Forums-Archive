---
title: "Less than 10 seconds error message"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by thoffland on 2005-06-29
I did a couple of things today that I thought would be harmles.. I followed 2 different howto's and something went awry. 

The one I think I'm having the problem with is the sound card configuration for gnome on ubuntuguide.org. I rebooted and started getting a 10 second error: 

View details in (~/.xsession-errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "myusrname"
/etc/gdm/Xsession: Beginning Session Setup.....
x-session-manager: error while loading shared libraries: libesd.so.0: cannot open shared object file: Error 40

Part  of the tutorial had the following command in it: 
sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

and since I dont know what "ln -fs" means, I dont know how to fix it... 

I tried reversing the command with the two files, but that didn't help. 

Any advice is appreciated!! 

update: I just looked at both of the files and they are blank... 
sudo vi /usr/lib/libesd.so.0

maybe I can replace them somehow.

(note that I typed this all out, I cannot login to gdm at all except the terminal window)

-------------------

I found the solution... I remembered aptitude and launched it and then uninstalled and reinstalled libesd0 and libesd-alsa and that did the trick. I rebooted and everything popped up perfectly. Another great learning experience!!

---

