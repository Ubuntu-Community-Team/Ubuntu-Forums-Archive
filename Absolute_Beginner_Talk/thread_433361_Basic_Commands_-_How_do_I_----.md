---
title: "Basic Commands - How do I ---- ?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-04
Ok Ive got a few questions I really cant figure out: (If you dont want to answer completely, please post a link!)

apt-cache search <package> -- Searches for packages in repositories.
Is there an equivalent command that will search the packages already installed (without knowing the exact name of the package?

How do you figure out services that are started at boot??

How do you list services that are currently running??

How would you disable/enable a service to run at startup??

How do you delay a service from starting (like put a 10 second delay)??

At startup - what determines the order of services starting???
   Seems like I always have to restart /etc/init.d/networking after boot in order for it to actually work!!!

Thanks :)

---

### Post by starcraft.man on 2007-05-04
> **kevdog said:**
> Ok Ive got a few questions I really cant figure out: (If you dont want to answer completely, please post a link!)

apt-cache search <package> -- Searches for packages in repositories.
**Is there an equivalent command that will search the packages already installed (without knowing the exact name of the package?**

[COLOR="Red"]sudo aptitude search <program> if its listed as i its installed, if its v its a dependancy, if its p its not installed.

or System > Administration > Synaptic Package Manager. Go to status tab in lower left, then click installed.
[/COLOR]
**How do you figure out services that are started at boot??**

[COLOR="Red"]System > Administration > Services. List is there.
Also, programs can be listed in System > Administration > Sessions.[/COLOR]

**How do you list services that are currently running??**

[COLOR="Red"]System > Administration > System Monitor. Processes tab.[/COLOR]

**How would you disable/enable a service to run at startup??**
[COLOR="Red"]
System > Preferences > Sessions. Look at startup tab, push add and type in the terminal command that triggers your app.
[/COLOR]
**How do you delay a service from starting (like put a 10 second delay)??**
[COLOR="Red"]
Ummm, why would you want a 10 second delay out of curiosity?[/COLOR]

**At startup - what determines the order of services starting???**

[COLOR="Red"]I dunno >.>, I presume its a combination of a lot of things... most importantly though I suppose the services dependancies i.e. if x depends on y, y loads first and so things load in order of increasing dependancy.[/COLOR]

   Seems like I always have to restart /etc/init.d/networking after boot in order for it to actually work!!!

Thanks :)

There you go, responded in your quote to make it easy :)

---

### Post by kevdog on 2007-05-04
Besides the obvious, are there command line equivalents?  Although GUI's are nice, they really tend to slow the computer down -- a good example of this is Adept.  Great program, but takes a long time to load and close.  I would rather stick with command line if possible

---

### Post by starcraft.man on 2007-05-04
Ummm, I don't think there is a command line version of the System Monitor or the Sessions manager. There likely is however a command that quickly lists all your services in terminal, I just don't know it off the top of my head, its a bit late here >.>.

Have Fun :)

---

### Post by orb9220 on 2007-05-04
Good tuts in my sig.

---

### Post by starcraft.man on 2007-05-04
> **orb9220 said:**
> Good tuts in my sig.

Holy Cow, thats a lotta links on that 180 page :p

One note though, your ubuntuguide link is broken, heres the one that works:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

your missing the "Ubuntu:" bit :)

---

### Post by kevdog on 2007-05-04
Sorry to keep bothering you, however Im running KDE, and some of the links like System->Administration->Sessions are not showing up and I cant seem to find an equivalent~

---

### Post by MRiGnS on 2007-05-04
> **starcraft.man said:**
> Ummm, I don't think there is a command line version of the System Monitor
there is. it's called top

man top for the manual. a miiiiiiighty tool

---

### Post by starcraft.man on 2007-05-04
> **kevdog said:**
> Sorry to keep bothering you, however Im running KDE, and some of the links like System->Administration->Sessions are not showing up and I cant seem to find an equivalent~

Lol, hehe, you have to provide this info at the beginning, most people are running gnome, you should make a point to specify your using KDE :)

And your not bothering me, I usually learn new things by helping other people learn :D

Edit: There, see, just learned top is the command :) I

---

### Post by kevdog on 2007-05-04
Orb9220

You better update your signature -- links contained in your sig, or many of the links which are found in the pages you reference are broken!

---

### Post by darkrose on 2007-05-04
> **kevdog said:**
> Ok Ive got a few questions I really cant figure out: (If you dont want to answer completely, please post a link!)

apt-cache search <package> -- Searches for packages in repositories.
Is there an equivalent command that will search the packages already installed (without knowing the exact name of the package?
sudo aptitude search <program>
i = installed, v = dependancy, p = not installed.

> How do you figure out services that are started at boot??
ls /etc/rc5.d
^ shows the services that start when you boot to a graphical login
ls /etc/rc3.d
^ shows the services that start when you boot to a non-graphical login

> How do you list services that are currently running??
ps aux

> How would you disable/enable a service to run at startup??
to disable: sudo rm /etc/rc5.d/<service name>
to enable: sudo ln -s /etc/init.d/<service name> /etc/rc5.d/Sxx<service name> (where xx is the position in the start order)

> How do you delay a service from starting (like put a 10 second delay)??
1. change it's start order so other processes start before it (although no way to accurately set the delay)
2. edit it's script in /etc/init.d/ and add sleep 10 to the beginning of the start case

> At startup - what determines the order of services starting??
look in /etc/rc5.d and you will see everything is numbered, there's you're start order.

---

### Post by darkrose on 2007-05-04
> **kevdog said:**
> Sorry to keep bothering you, however Im running KDE, and some of the links like System->Administration->Sessions are not showing up and I cant seem to find an equivalent~
Kmenu --> System Settings --> advanced tab --> system services

---

### Post by kevdog on 2007-05-04
Wow -- these answers are even better than what I thought!!

Just one thing.  I went to look for networking in the rc directories.  I found it at:
/etc/rcS.d/S40networking

Good explanations for rc3 and rc5, what is rcS?
Would there be any consequences to moving(renaming) the networking for example to S80networking?

---

### Post by darkrose on 2007-05-04
Services in rcS.d start in all runlevels

If you renamed networking to S80 it would just start a little later in the boot process.
However, I think there are some other services there that require networing (dns & nfs) which would also have to be changed so they still start after networking.

---

### Post by kevdog on 2007-05-04
I guess what you posed is the million dollar question.  Lets say for example I just moved networking to S80. Would errors show up in the sys log to tell me what services failed to start.

Is there any tool that would tell you service dependencies?? (For example what services are dependent on networking to start??)

Thanks

---

### Post by darkrose on 2007-05-04
I don't think there is a tool to show service dependancies, although services such as nfs or dns are likely to need networking running.
You would most likely get errors onn booting which would show if a service failed to start, running *dmesg | grep fail* would show them once you've logged in

---

