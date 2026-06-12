---
title: "Iptables + firestarter"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by edm1 on 2006-09-10
I've just installed firestarter as a gui frontend for iptables. I was led to believe it only needs to be run in order to alter the iptables configuration files as iptables is built into the kernel and runs constantly in the background.

Once i run firestarter everything seems fine, using nmap from another computer on my LAN it is unable to detect any open ports however once i restart the system everything seems to have reset itself and about 5 ports are visibly open when scanned, i only seem to be protected when running firestarter. Is this normal or is something not working?

---

### Post by mlind on 2006-09-10
firestarter contains also a service/daemon part which loads the rules for iptables once the service process has been started. This should all happen automatically.

firestarter gui component is just for modifying rules and shouldn't affect the results of a port scan no matter if it's running or not.

Does grc scanner report same results as nmap?
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by edm1 on 2006-09-11
well i'm behind a hardware firewall so i cant use grc. the reason im trying to set up the firewall is because im off to uni soon and im sure there will be plenty of people interested in trying to "hack" my machine. It appears that the firestarter daemon isn't running at start up. I've heard this might happen if you compile firestarter from source but i didnt, i used aptitude. Can anyone help?

---

### Post by thechemist on 2006-09-11
I can confirm this. See my bug report at:

   [https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647](https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647)

---

### Post by thechemist on 2006-09-15
Comments anyone ? This looks major. What are Edm1 and I doing wrong ? What is preventing the Firestarter daemon from starting at boot ?

---

### Post by mlind on 2006-09-15
> **thechemist said:**
> Comments anyone ? This looks major. What are Edm1 and I doing wrong ? What is preventing the Firestarter daemon from starting at boot ?

What's the output of 
```

sudo /etc/init.d/firestarter restart

```

---

### Post by steve.horsley on 2006-09-15
Just a note. If you can't get firestarter to confiugre iptables at boot, you could try guarddog instead. I have used guarddog, and it does configure iptables at startup. It creates a script /etc/rc.firewall.

Sorry I can't help with firestarter - I've never tried it.

---

### Post by edm1 on 2006-09-17
> **mlind said:**
> What's the output of 
```

sudo /etc/init.d/firestarter restart

```

i did this after rebooting

> ed@edlaptop:~$ sudo /etc/init.d/firestarter status
Password:
 * Firestarter is stopped
ed@edlaptop:~$ sudo /etc/init.d/firestarter restart
 * Stopping the Firestarter firewall...                                  [ ok ]
 * Starting the Firestarter firewall...                                  [ ok ]
ed@edlaptop:~$ sudo /etc/init.d/firestarter status
 * Firestarter is running...


EDIT: just tried to uninstall firestarter using synaptic and get this error message

> E: firestarter: subprocess post-removal script returned error exit status 1

---

### Post by thechemist on 2006-09-18
edm1;

my output to

  sudo /etc/init.d/firestarter restart

is the same as yours. The inability to uninstall Firestarter is a known bug (see [https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/39598](https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/39598))

the fix is to delete the line

   'set -e'

from /var/lib/dpkg/info/firestarter.postrm

You should then be able to uninstall and reinstall cleanly. I have gone through that process to no avail. Firestarter still won't set up the iptables at boot.

This is puzzling as many in the forums state that Firestarter is merely a GUI frontend to iptables and after the initial set up, the GUI doe not need to run for the firewall to be active. That is also what the manual says. 

Well, not so for you and I. I wonder how widespread that problem is.

---

### Post by edm1 on 2006-09-18
It's quite a large security flaw for those whom are unaware it's happening to them.

I've stopped trying to find a fix now, i've tried everything i can thing of.

I'm off travelling for 8 months so I plan to do a fresh install of Ubuntu with whatever comes after Edgy when i get back and hope that it all works then.

---

### Post by 5-HT on 2006-09-19
I've tried to get firestarter (not the GUI: there seems to be a bug/feature with that as well) to start on boot without sucess by appending **/etc/init.d/firestarter restart** to **/etc/rc.local**.

```
* Running local boot scripts (/etc/rc.local)           [ok]       
* Starting the Firestarter firewall                        [fail]
* Stopping the Firestarter firewall                       [fail]
```Anyone have any ideas of what I'm doing wrong?

---

### Post by 5-HT on 2006-09-22
Funny with how often Firestarter comes up in these forums that not much attention is being paid to this alleged bug of not starting without either the GUI running or manually starting the service.

*bump for previous post*

---

### Post by YeahBuntu on 2006-09-22
found [this]("http://www.linuxforums.org/forum/linux-security/43065-iptables-start-boot-debian3-1-a.html") whilst looking around since I am using firestarter too.

Ubuntu is based off Debian so this should work for us too.

---

### Post by taxus on 2006-12-05
Can't say why it won't work with rc.local (I'm a newbie). But I added firestarter to the startup boot sequence in /etc/rcS.d, and it works: firestarter is now executed on boot.

I'm a DSL/PPPoE user; my Internet connection is activated on boot (I used pppoeconf, which added a few lines to /etc/network/interfaces to connect at boot time), so I assumed I could start firestarter at boot, after networking, or else I suppose firestarter won't do anything if it does not detect a valid Internet connection.

So in a Nautilus window opened as root, I created a symbolic link from

```
/etc/init.d/firestarter
```

to

```
/etc/rcS.d/S99firestarter
```

Or, if you really want to do it console-style,

```
sudo ln -s /etc/init.d/firestarter /etc/rcS.d/S99firestarter
```

The S99 prefix means that firestarter will be loaded last. (Networking is set up at point 40, and ppp at 55 if I correctly understand.)

---

### Post by kakalaky on 2006-12-05
Works fine here in Edgy.

---

