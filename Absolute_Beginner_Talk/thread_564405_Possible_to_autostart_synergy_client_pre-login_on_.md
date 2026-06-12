---
title: "Possible to autostart synergy client pre-login on xubuntu ?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by jakmite on 2007-10-01
Hello, I have just got synergy working between my xubuntu & xp rigs. :) Want to try to configure my xubuntu so it autostarts the synergy client, but it seemed it is not possible to make it autostart pre-login for xdm, as stated in the synergy docs

> Note that some display managers (xdm and kdm, but not gdm) grab the keyboard and do not release it until the user logs in for security reasons. **This prevents a synergy server from sharing the mouse and keyboard until the user logs in.** It doesn't prevent a synergy client from synthesizing mouse and keyboard input, though.

Has anyone using xubuntu managed to get around this problem ? :-s

Heres the current setup:

XP Pro --> synergy server
Xubuntu 7.04 -->synergy client

---

### Post by jfinkels on 2007-10-02
Well, I don't know too much about this, but you may want to look at adding the synergy daemon to the list of daemons to be run at start-up. Daemons are stored in the directory "/etc/init.d/" and there is a README file in there which you might take a look at. Symbolic links to daemons in "/etc/init.d/" are put in "/etc/rc0.d/", "/etc/rc1.d/", etc. so the daemons will be run at each successive runlevel. Again, I don't know much about runlevels, so this may require some other expert. Essentially, the gist of it is, add a shell script that starts synergy to the list of startup programs in /etc/init.d/ and it will start every time you start the system.

---

### Post by BrendanM on 2007-10-05
I was able to get Synergy working before and after login by adding certain lines to some of GDM's files, as follows:
To /etc/gdm/Init/Default
At the start of the file, add
```

/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc --restart -n <name_of_local_machine> <name_of_server>

```

To /etc/gdm/PostLogin/Default add
```

/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc --restart -n <name_of_local_machine> <name_of_server>

```

To /etc/gdm/PreSession/Default/  add the synergy related lines as below

```

 IFS=$OLD_IFS 
  echo "$OUTPUT"
}

# synergyc process, running as root, ends here. This is the last script in #the gdm login sequence before things start running as user. Added by Brendan
/usr/bin/killall synergyc
sleep 1

# Set background color
XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then
```

I've included a little context on the last one to show you where to put the synergy stuff, since I don't think it goes at the very start. If you don't have all of these files, you may need to create them by copying the example file and making it an active file. I remember having to do that for at least one file.

These are links where I got my information:
 [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)
[http://fro.instantspot.com/blog/index.cfm/ubuntu](http://fro.instantspot.com/blog/index.cfm/ubuntu)
[http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)

This works for me, your milleage may vary.

EDIT: I just realized you were asking specifically for Xubuntu. The above will work on Ubuntu. You might try changing Xubuntu to use GDM as the login manager instead. I don't think that would be impossible.

---

### Post by jakmite on 2007-10-05
Thanks, will try out. :cool:

---

