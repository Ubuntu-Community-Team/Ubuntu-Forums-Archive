---
title: "Running stuff at boot (before login)"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Skip Da Shu on 2007-11-14
I don't think this "run at boot" file (at bottom) is really getting executed at boot but I haven't been able to figure out why.  It appears that neither of the commands I added to it worked.  After I logon there is no x11vnc server running that I can see or connect to and my shared mount dir is empty.


In the dir /etc I have a file called rc.local that was a dummy (script?) file having originally only comments and the 'exit 0' command at the end.  I added the x11vnc and the mount commands.  After I edited them with 'sudo gedit .....'  I did ```
sudo chmod a+x /etc/rc.local
```

1) I've got smbfs working with an entry in /etc/fstab so that if I do 'sudo mount -a' from a terminal after I log in it works and a shared folder on my WinXP box is mapped to /home/c17xfer.  Works great except I'd rather it did it at start up automatically.  So I put the mount command in this file... doesn't work. 

/etc/fstab entry:```

//C17-E64desktop/xfer /home/c17xfer smbfs credentials=/home/skip/.smbcredentials,1000 0 0
```

2) This x11vnc command (without the WAIT: on it) also works when issued from a terminal on my desktop.  I have tried it with and without the WAIT: in this file and the x11vnc server doesn't get started.

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5808 -allow 192.168.218. -sb 30 -display WAIT:

mount -a

exit 0
```

---

### Post by Skip Da Shu on 2007-11-14
OK, I decided there was no need to mount the share before logon... so I used used Applications>Settings>Autostarted Applications and added this as the command line for a new entry there:
```
sudo mount -a
```

My shared dir is still empty??

Execute same command from a terminal... share appears!

Oh, Xubuntu 7.10

---

### Post by SpiritIsReality on 2007-11-15
> **Skip Da Shu said:**
> OK, I decided there was no need to mount the share before logon... so I used used Applications>Settings>Autostarted Applications and added this as the command line for a new entry there:
```
sudo mount -a
```

My shared dir is still empty??

Execute same command from a terminal... share appears!

Oh, Xubuntu 7.10

Thankyou pardner!!!

---

### Post by Skip Da Shu on 2007-11-18
After a reinstall of Xubuntu Gutsy (for other reasons so stupid I don't want to tell).

I figured out that a can right click on the Xfce desktop, create a launcher, click "run in terminal" and then enter just this as the command ```
sudo mount //192.win.xps.ip/xfer /home/skip/c17xfer
```.   The terminal will pop open to ask you your password (from sudo) but works fine. 

Another launcher with "run in terminal" and command line of ```
sudo umount /home/skip/c17xfer
```.  

These give me what I need for the occasional time I need to pass/edit files on the XP machine.

I had already installed smbfs but I'm not sure if I really needed it or not... I may try sudo apt-get remove smbfs just to see if the launchers still work... hopefully if not I could just reinstall smbfs.  UPDATE: (It is needed).

Now... back to the x11vnc at boot problem...

---

### Post by Skip Da Shu on 2007-11-18
OK, after the reinstall I now have this in my /etc/rc.local ```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

x11vnc -usepw -forever -allow 192.wrk.grp. -rfbport 5999 -o /home/vnclog

exit 0
```

It works from a terminal in my desktop but I need it to run at boot before a user is logged on.  Is this possible?

---

### Post by krunge on 2007-11-18
> **Skip Da Shu said:**
> OK, after the reinstall I now have this in my /etc/rc.local 

...

It works from a terminal in my desktop but I need it to run at boot before a user is logged on.  Is this possible?

This might help:

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager") 

and perhaps also: 

[http://www.karlrunge.com/x11vnc/#faq-service]("http://www.karlrunge.com/x11vnc/#faq-service")

---

### Post by MobiusNZ on 2007-11-18
If you want your shares to be available at boot, simple put auto in the fstab arguments

```

/source    /mount/point    fstype    rw,defaults,auto 0 0

```

Or something like that ;)

---

### Post by Skip Da Shu on 2007-11-18
> **krunge said:**
> This might help:

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager") 

and perhaps also: 

[http://www.karlrunge.com/x11vnc/#faq-service]("http://www.karlrunge.com/x11vnc/#faq-service")

Man, bunches of good info here!  Most of it is about 1K miles over my head but it's good reading and I'll continue on.  At this point this has me thinking that maybe in Xubuntu 7.10 the "startup" is handled by /etc/xdg/xfce4-session or /etc/xdg/xfce4  but I'm  not sure... this may be after the user has logged on.  I'll continue reading but I wanted to thank you for the links.

---

### Post by krunge on 2007-11-18
> **Skip Da Shu said:**
> At this point this has me thinking that maybe in Xubuntu 7.10 the "startup" is handled by /etc/xdg/xfce4-session or /etc/xdg/xfce4  but I'm  not sure... this may be after the user has logged on.  I'll continue reading but I wanted to thank you for the links.

Yes, I am not sure about xfce.  Like you say, since xfce is a window manager, those scripts may get run only after the user has logged in at the console.  You have to find the config files for the display manager.  I'm not sure if xfce has its own display manager.  KDE has 'kdm' , GNOME has 'gdm' and there is also the traditional 'xdm'. 

Maybe a command like this:
```
ps wwwwwwwwaux | grep dm
``` will help find which display manager you are running (e.g. if you see gdm).  Or skip the grep and hunt around the ps wwwwwwwaux output to see if you can spot it.  Then you "only" have to find its setup script and add the line.

---

### Post by Skip Da Shu on 2007-11-23
> **krunge said:**
> Yes, I am not sure about xfce.  Like you say, since xfce is a window manager, those scripts may get run only after the user has logged in at the console.  You have to find the config files for the display manager.  I'm not sure if xfce has its own display manager.  KDE has 'kdm' , GNOME has 'gdm' and there is also the traditional 'xdm'. 

Maybe a command like this:
```
ps wwwwwwwwaux | grep dm
``` will help find which display manager you are running (e.g. if you see gdm).  Or skip the grep and hunt around the ps wwwwwwwaux output to see if you can spot it.  Then you "only" have to find its setup script and add the line.

That helped greatly.  Guess it is gdm.  Would you take a look at post #96 [HERE]("http://ubuntuforums.org/showthread.php?p=3822473#post3822473").  With the info you pointed me to I have the x11vnc server running and can get to my desktop login.  Once I do login I lose the vnc connection.  So I am having to restart the viewer to get to the 'restarted' x11vnc server that was autostarted with the session.  I am hoping there might be a simple change my setup in /etc/gdm/Init/Default that would fix this and allow me to remove the x11vnc server started with the session.

Thanx in advance, Skip

---

