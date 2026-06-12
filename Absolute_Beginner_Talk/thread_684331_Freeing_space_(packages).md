---
title: "Freeing space (packages)"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by LordCthulu on 2008-02-01
I have Ubuntu installed on a 5gb partition, and I was wondering what are some packages I can get rid of to free up some space? I've use localepurge, apt-get autoclean, and deborphan already. I'm trying to get rid of some packages I don't need (like bluetooth utilities) but using synaptic there is hundreds of entries. I tried using the add/remove tool, but it says I have to use synaptic. Are there any fairly large programs I can get rid of that are installed by default on gutsy? Or an easier way to find things I don't need? Thanks in advance. :KS

---

### Post by mikeyphi on 2008-02-01
This guide may provide further ideas: [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by jan quark on 2008-02-01
I would be very cautious with deleting packages 
many packages depend on each other 
only remove one when you really know what you are doing

just being curious 

you can't increase the size of the partition?

---

### Post by oedha on 2008-02-01
may i ?
what about sudo apt-get autoremove ?
or have you clean up your cache ?
/var/cache/apt/archives

i suggest you to remove by program name and i dont really agree to remove something like bluetooth utilities........
~E~

---

### Post by kpkeerthi on 2008-02-01
You should be really careful trying to slim down your ubuntu by removing packages. Do not attempt to remove something you are not sure of. 

That being said, you may consider removing gnome-games, openoffice (and/or replace with lighter abiword & gnumeric). Also consider removing the kernels you no longer use. Cleanup unused nautilus $HOME/.thumbnails. To remove thumbnails not used in the last 14 days
```

find ~/.thumbnails -name *.png -atime +14 -exec rm '{}' ';'

```

Disable unneeded services from System > Administration > Services. Again, please be careful here. gnome-bluetooth and bluez-utils are the bluetooth related packages if you wish to remove. 

And finally, you should use synaptic to remove these packages so the dependencies are taken care of.

---

### Post by LostMagix on 2008-02-01
Dont do it until someone more experienced gives the go ahead on this.....


```
sudo apt-get autoremove
```

---

### Post by bollix47 on 2008-02-01
To remove the archives of packages that Synaptic or apt-get downloaded:

```
sudo apt-get clean
```

This won't uninstall any packages from your system, it just removes the downloaded package install files.  i.e. /var/cache/apt/archives/*

---

### Post by SOULRiDER on 2008-02-01
> **bollix47 said:**
> To remove the archives of packages that Synaptic or apt-get downloaded:

```
sudo apt-get clean
```

This won't uninstall any packages from your system, it just removes the downloaded package install files.  i.e. /var/cache/apt/archives/*

I was going to suggest that too, autoclean does not remove everything.
Aptitude can also clean the cache:
```
sudo aptitude clean
```

---

