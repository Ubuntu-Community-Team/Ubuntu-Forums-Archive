---
title: "Stopping X"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by BodaciousBrian on 2007-12-05
Im trying to figure out how to stop the x server so i can run nvidia's installer.

Ive tried:

/etc/init.d/gdm stop (says it stops it, but x still runs)
/usr/sbin/gdm stop (seems to try to START gdm)
Ctrl-Alt-Backspace (restarts X)

which gdm says that /usr/sbin is the one that is running.

Everyone seems to say that the first on i listed here is how its done.  But that just isn't working =(

---

### Post by Dr Small on 2007-12-05
Try:
```
ps aux | grep x
```

Find, "/usr/bin/X", look at the pidnumber, then run:
```
sudo kill *pidnumber*
```

---

### Post by shad0w_walker on 2007-12-05
What version of Ubuntu are you using? If it is 7.04 or newer then you don't need manually install the drivers. Just goto System > Adminsitration > Restricted drivers.

If you are using an older version then try using Envy, it will manage the installation by itself so you don't need to mess around with anything.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

You can download Envy from that link. It is alot easier to deal with than manually installing the drivers.

---

### Post by BodaciousBrian on 2007-12-05
IM using 7.10  I have the drivers installed.  I'm just trying to get the most up-to-date version(allthough i never checked the version i have :)) becasue my FPS are quite low running Counter-strike in Wine.

 ps aux | grep x :
root      2094  0.0  0.0      0     0 ?        S<   18:51   0:00 [ata_aux]
root      5057  0.0  0.1   2928  1188 ?        Ss   18:51   0:00 /usr/sbin/hcid -x -s
1000      5652  0.0  1.2  43872 12688 ?        Ssl  18:53   0:01 x-session-manager
1000      5687  0.0  0.0   4436   548 ?        Ss   18:53   0:00 /usr/bin/ssh-agent x-session-manager
1000      5789  0.0  1.2  44772 13204 ?        Sl   18:53   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=19
1000      5980  0.0  0.0   1752   528 ?        S    18:55   0:00 /bin/sh /usr/bin/firefox
1000      5992  0.0  0.0   1752   528 ?        S    18:55   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
1000      5996  2.8  5.4 171088 56916 ?        Sl   18:55   0:32 /usr/lib/firefox/firefox-bin
1000      6565  0.0  0.0   2620  1000 pts/0    R+   19:14   0:00 ps aux
1000      6566  0.0  0.0   2972   748 pts/0    R+   19:14   0:00 grep x


I dont know what colum the pid is, and i dont know which one X is =(

---

### Post by Hospadar on 2007-12-05
The correct way to stop and start x is with one of the following commands
```
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm restart
sudo /etc/init.d/gdm stop

```the script "/etc/init.d/gdm" is the script that your machine uses to startup X and Gnome when you start your machine.  you'll need to run this script from a non-graphical terminal, you can get to one with ctrl-alt-F1, the virtual terminal where gnome typically resides is at ctrl-alt-F7

That said, you really shouldn't install the nvidia drivers manually, you should use the restricted driver manager System->Administration->Restricted Drivers Manager, and if that doesn't work, try the envy script as linked above

---

### Post by Dr Small on 2007-12-05
Hmm. I don't see "/usr/bin/x" like I did on mine.
By the way, the pidnumber is the second column over,

Example:
```
1000 5652 0.0 1.2 43872 12688 ? Ssl 18:53 0:01 x-session-manager
```
The pidnumber there, would be **5652**

Dr Small

---

### Post by BodaciousBrian on 2007-12-05
Hospadar, using that stop command says that gdm stops, but it doesn't work.

Thanks Small... sudo kill 5652 restarts X =P

I cheated and used envy.  But i still would really like to know how to kill the x server, and keep it off rather than letting it reset itself..

---

### Post by Hospadar on 2007-12-05
I dunno, that's always worked just fine for me.  at any rate, it should start x just fine for you.  that is unless you are using kde, in which case you need to replace gdm with kdm (I believe)

---

### Post by 3rdalbum on 2007-12-05
System > Administration > Services (not sure if it's still there on Gutsy)

Uncheck the Xorg service. This might kill X immediately, and leave it off. If it doesn't, then you will need to press Control-Alt-Backspace.

To turn it back on, do:

```
sudo /etc/init.d/gdm start
```

From then on, X will automatically start up again on startup. I believe. If not, then simply recheck it in the Services panel.

---

### Post by BodaciousBrian on 2007-12-07
Sorry its been so long since i've responded but stopping the service worked perfectly!!!  That does seem to be the only way to disable gdm for the latest versions of Ubuntu.

Thank you!

---

