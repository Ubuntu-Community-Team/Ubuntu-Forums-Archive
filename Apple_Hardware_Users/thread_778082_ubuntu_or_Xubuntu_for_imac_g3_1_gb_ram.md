---
title: "ubuntu or Xubuntu for imac g3 1 gb ram"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by oisuxx on 2008-05-01
i put ubuntu on my imac G3, but it seems to be running a bit slow. i didnt know if anyone else has done both and maybe has a speed comparison. all im using it for is audacity. i wanted it for ardor but that wont work right with my tangerine imac.
i figured it wouldnt scream, but i upgraded the memory to 1 gig and its still kinda slow. 

i also tried debianppc (business card disk instal) but it kept saying natilus failed and had like 10 warning screens pop up before anything even started.

---

### Post by stream303 on 2008-05-02
It definitely won't be a speed demon, although you can very roughly compare a PPC G3 to an Intel at twice the speed, ie if you are running a 266 mhz iMac, it would be roughly equivalent to a 532mhz Intel.

Good deal on the 1gb ram!  That means that the box has had a firmware upgrade, but I'd definitely check to be sure by running

```
free -m
```

and see what shows up in the first column.

If you installed the extra ram after the installation, your swap partition will probably be too small, but with 1gb you'd be very unlikely to hit swap anyway - unless you pull up a lot of heavy-duty programs all at once.

---

### Post by oisuxx on 2008-05-02
yea it just seems super slow loading things. i might just go with xubuntu for speed. i did put the memory in before i installed ubuntu. i wanted it to see everything i had, so i didnt have to make it update or whatever later on.

the one thing i noticed was i have 2 programs running, firefox and audicity or however its spelled. i can record 1 track fine, but then the second and every OTHER track is garbled. i have to save 1 track then import it into another track i record seperatly . offtopic sorry, just odd to me.






> **stream303 said:**
> It definitely won't be a speed demon, although you can very roughly compare a PPC G3 to an Intel at twice the speed, ie if you are running a 266 mhz iMac, it would be roughly equivalent to a 532mhz Intel.

Good deal on the 1gb ram!  That means that the box has had a firmware upgrade, but I'd definitely check to be sure by running

```
free -m
```

and see what shows up in the first column.

If you installed the extra ram after the installation, your swap partition will probably be too small, but with 1gb you'd be very unlikely to hit swap anyway - unless you pull up a lot of heavy-duty programs all at once.

---

### Post by stream303 on 2008-05-02
Xubuntu is nice, you can get it without reinstall by just installing xubuntu-desktop, and then at your next logon session, change to it.  The desktop should be a bit faster, although resource-intensive programs won't.

One thing you can do is to make sure that no other processes are hogging the cpu.  I like to run top, or even better, download and run HTOP.  For instance, on my G4 iBook, Network Manager was hogging the whole show, so I had to disable it - but that was with Gutsy and on only this machine.  Top revealed it.

---

### Post by oisuxx on 2008-05-02
would that command be sudo apt-get xubuntu-desktop    ????

ive onl been running ubuntu on my main machine for about 3-4 months
im still very new when it comes to all that stuff.



> **stream303 said:**
> Xubuntu is nice, you can get it without reinstall by just installing xubuntu-desktop, and then at your next logon session, change to it.  The desktop should be a bit faster, although resource-intensive programs won't.

One thing you can do is to make sure that no other processes are hogging the cpu.  I like to run top, or even better, download and run HTOP.  For instance, on my G4 iBook, Network Manager was hogging the whole show, so I had to disable it - but that was with Gutsy and on only this machine.  Top revealed it.

---

### Post by stream303 on 2008-05-03
actually it would be
```
sudo apt-get install xubuntu-desktop
```

Perhaps easier would be to just use the Synaptic Gui.

When xubuntu desktop is installed, it won't delete any of the regular Ubuntu gnome apps, and you are likely to find duplicates - such as the regular Ubuntu nautilus file manager, and also Thunar, Xubuntu's file manager for instance.  So you can optionally keep some of those heavyweight apps like nautilus around, or delete them - you choice.

To get back to a "pure" Ubuntu/Kubuntu/Xfce4 environment when another one has already been installed, I find the following from psychocat very handy when you would like to totally remove one or multiple desktop environments:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Once loaded, in the lower left of the Ubuntu screen is "Options" and from there you can choose a specific desktop session (and more) to run.

---

### Post by abtabt on 2008-05-03
if you need speed on a slow imac like 333mz install xfce4-desktop and icewm 
and use icewm then you have a start with program and ulities

this post came from imac 333mz 96mb with mobilmodem huawai usb 
its not super fast but fast when a use icewm if i use xfce4 it slows 
down a lott but you can use icwwm and xfce4 things too like panel etc

---

### Post by oisuxx on 2008-05-03
im not sure what those are. i tried the command i THOUGHT it was and of course it didnt work, so i went to just do a fresh install of xubuntu. the screen went into a sleep type mode and i couldnt recover. so now it looks like i have to install regular ubuntu again. is there like a DSL for the ppc though? the closest i got to any kind of speed was just regular debian but i ran into a bunch of errors with natilus before.
i dont know if that was because i hadnt upgraded the memory though.



> **abtabt said:**
> if you need speed on a slow imac like 333mz install xfce4-desktop and icewm 
and use icewm then you have a start with program and ulities

this post came from imac 333mz 96mb with mobilmodem huawai usb 
its not super fast but fast when a use icewm if i use xfce4 it slows 
down a lott but you can use icwwm and xfce4 things too like panel etc

---

### Post by ssam on 2008-05-03
the package preload will make programs load a bit faster. (it caches things into ram before you use them).

also have a look in system->administration->services, and system->preferences->sessions. the chances are that you can turn things like bluetooth off.

---

### Post by stream303 on 2008-05-03
> **oisuxx said:**
> is there like a DSL for the ppc though?

Not sure if there is a netinst-like ppc image.  Perhaps the closest thing would be to download and install the ppc-server, and then tack on just what you need like xorg, xdm, and the like.  A good intro to doing that is here, even though it initially targets Intel, but is just as useful for ppc:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I used it even though I was running 1.5gb of ram. :)

---

