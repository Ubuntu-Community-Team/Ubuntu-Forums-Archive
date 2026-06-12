---
title: "can i improve the performance of ubuntu 6.10"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by freelancer1995 on 2007-01-29
can i improve the performance of ubuntu 6.10 on my celeron 1.7ghz, nvidia mx4000, 640mb ram, 40 gb harddisk?

it seems quite sluggish not really fun to use, can i cache more resource to memory? any suggestion?

thanks :)

---

### Post by shoaibi on 2007-01-29
Well to me your system is reasonable, still if its slow, install XFCE, or eplace Nautlis with Fluxbox which is really light.
I would recommed going to XCFE as i do....

---

### Post by aktiwers on 2007-01-29
You could install a more light Shell, like openbox or xubuntu.

---

### Post by freelancer1995 on 2007-01-29
thanks, but doesn't installing a new shell seem a bit extreme?  is there a minimum spec for ubuntu 6.10? 

for my reference:
XFCE : [http://www.xfce.org/](http://www.xfce.org/)
Fluxbox : [http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)
OpenBox : [http://icculus.org/openbox/](http://icculus.org/openbox/)
xubuntu : [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by userundefine on 2007-01-29
Strange because that system's more than adequate.  I have Ubuntu on a nearly identical system and I don't have any issues.  Do you have a swap partition?

---

### Post by ajmorris on 2007-01-29
> can i improve the performance of ubuntu 6.10 on my celeron 1.7ghz, nvidia mx4000, 640mb ram, 40 gb harddisk?

it seems quite sluggish not really fun to use, can i cache more resource to memory? any suggestion?

My system specs are quite a bit worse than that, and my ubuntu is never sluggish.

---

### Post by Medieval_Creations on 2007-01-29
One other option is to see what services are being started at boot and disable any that you don't need.  I use rcconf (CLI) & Boot Up Manager (GUI).

---

### Post by felix.rommel on 2007-01-29
You can use Preload for preloading some apps in memory:

sudo apt-get install preload

The Gnome interface won't be faster but some apps will start much faster. Disadvantage of preload is that the boot time is a little bit longer.

---

### Post by glabouni on 2007-01-29
you can remove all unneeded services you don't use.

a bit late but still: from Ubuntu Blog:
[Removing or Editing a Startup Script ]("http://ubuntu.wordpress.com/2005/09/09/removing-or-editing-a-startup-script/")

for example if you don't use any pcmcia you can remove pcmcia service with:
```
sudo update-rc.d pcmcia remove
```

more on this in debianadmin article: [Debian and Ubuntu Linux Run Levels]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html")

---

### Post by freelancer1995 on 2007-01-29
i allowed ubuntu to configure itself on installation on a clean drive, no partitions or previous OS, i assumed it(6.10) installed a swap drive by default, as i have access to 35gb not 40gb.  is there a way to tell and if so, how do i tell if it is in use, or even turn it back on?

---

### Post by freelancer1995 on 2007-01-29
rcconf says :                                                                        
                                                                             
     &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; rcconf - Debian Runlevel Configuration tool &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;     
     &#9474;                                                                    &#9474;     
     &#9474;    [*] dbus                                                    &#8593;   &#9474;     
     &#9474;    [*] firestarter                                             &#9646;   &#9474;     
     &#9474;    [*] gdm                                                     &#9618;   &#9474;     
     &#9474;    [*] hplip                                                   &#9618;   &#9474;     
     &#9474;    [*] nfs-common                                              &#9618;   &#9474;     
     &#9474;    [*] nfs-kernel-server                                       &#9618;   &#9474;     
     &#9474;    [*] preload                                                 &#9618;   &#9474;     
     &#9474;    [*] samba                                                   &#9618;   &#9474;     
     &#9474;    [*] usplash                                                 &#9618;   &#9474;     
     &#9474;    [ ] avahi-daemon                                            &#8595;   &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474;                 <Ok>                     <Cancel>                  &#9474;     
     &#9474;                                                                    &#9474;     
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;     
nothing else, i did setup nfs-common, nfs-kernel-server and samba only just added preload, after reading this forum.

---

### Post by Medieval_Creations on 2007-01-29
if you type the command

sudo fdisk -l

it will show how many and what your partitions are.

---

### Post by glabouni on 2007-01-29
to get info about swap you can use:
```
cat /proc/swaps
```

the command to specify a swap partition is: swapon

---

### Post by kerry_s on 2007-01-29
> **freelancer1995 said:**
> can i improve the performance of ubuntu 6.10 on my celeron 1.7ghz, nvidia mx4000, 640mb ram, 40 gb harddisk?

it seems quite sluggish not really fun to use, can i cache more resource to memory? any suggestion?

thanks :)

Yes, you can cache some applications for faster first start. You put a line in /etc/init.d/rc.local, it looks like this> 
sudo -u (user) find /usr/lib/(application) ! -type d | xargs cat > /dev/null &

replace (user) with the account name and (application) with the name of the app you want to cache at boot time.

I haven't tried it on gnome so i can't be sure of what applications would work. The only thing i cache is firefox for faster first start, cause that's the main thing i use at startup. here's a pic of my rc.local->

---

### Post by freelancer1995 on 2007-01-30
> **Medieval_Creations said:**
> if you type the command

sudo fdisk -l

it will show how many and what your partitions are.

well, i have a swap partition, as shown, thanks

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

---

### Post by freelancer1995 on 2007-01-30
> **kerry_s said:**
> Yes, you can cache some applications for faster first start. You put a line in /etc/init.d/rc.local, it looks like this> 
sudo -u (user) find /usr/lib/(application) ! -type d | xargs cat > /dev/null &

replace (user) with the account name and (application) with the name of the app you want to cache at boot time.

I haven't tried it on gnome so i can't be sure of what applications would work. The only thing i cache is firefox for faster first start, cause that's the main thing i use at startup. here's a pic of my rc.local->

i will give it a try, thanks

---

### Post by freelancer1995 on 2007-01-30
i managed to max out my processor to 100% usage again by browsing to this website [http://fantasy.premierleague.com/](http://fantasy.premierleague.com/), why is firefox so unhappy?

---

### Post by kerry_s on 2007-01-30
It's got to be the site trying to run some scripts in the background. It maxed mine out a 100% too. See pic->

---

### Post by freelancer1995 on 2007-01-30
the site runs a ticker for current news and football results.  concerning reaction from our linux os to this scripting.  when run from MS XP using firefox it doesn't behave in the same way, CPU usage drops to 1% after it is downloaded.

---

### Post by kerry_s on 2007-01-30
No, there using some kind of java based script in the background. If you disable java and go there it does nothing to the cpu. Windows lets any site do what ever they want behind your back, there suppose to ask permission first. what it does is try and put a ".java" run time script on your system, but since they never asked permission they can't.For example if you used runescape it asks you first. see pic with java off.

---

### Post by freelancer1995 on 2007-01-31
i thought, it may have been something like that about 5 minutes after logged off last night.  thanks for your help :-)

---

### Post by freelancer1995 on 2007-01-31
just tried it again, java disable, javascript enabled; 100% cpu usage again then tried java enabled, javascript disabled; cpu drops to nothing after initial load of page.  looks like the javascript on this page.

---

### Post by freelancer1995 on 2007-01-31
looks like a known bug for large scale javascripts.

[https://bugzilla.mozilla.org/show_bug.cgi?id=313967](https://bugzilla.mozilla.org/show_bug.cgi?id=313967)

---

