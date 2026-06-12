---
title: "i did something wrong"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2007-02-16
i tried to install the trial verion of nerolinux, but as i was installing the package, i accidentally had the updater open, so it notified me and i closed it. but now, everytime i try to run gdebi package installer, it always returns the same message

> Could not open 'nerolinux-2.1.0.4-x86.deb'

The package might be corrupted or you are not allowed to open the file. heck the permissions of the file.

so, naturally i tried opening it through root, and same problem. Then i went on to redownload, but still the same problem. And i recently noticed this message from synaptic package manager

> E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


So, how can i fix this. Because no packages show up in the package manager, and my updater isn't working either.

---

### Post by jacksonz123z on 2007-02-17
Same problem here.  No more debs for me.

---

### Post by kerry_s on 2007-02-17
In terminal try running-> sudo apt-get -f install

---

### Post by jacksonz123z on 2007-02-17
Thanks for the help.  The command gives " The package nerolinux needs to be reinstalled, but I can't find an archive for it."

---

### Post by CodyJarrett on 2007-02-17
This command finally got rid of the cursed thing for me:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq nerolinux
```

you might need to remove all files beginning with nerolinux from the /var/lib/dpkg/info/ folder.

Hope this helps.

---

### Post by mcduck on 2007-02-17
> **jacksonz123z said:**
> Same problem here.  No more debs for me.

Actually .deb package is by far the safest and easiest way of installing apps (apt-get and Synaptic uses them). Just make sure that you only use .deb packages that are made for Ubuntu, and that you get them from a reliable source..

edit: Why do you want Nero anyway? It's probably the worst burning app available for Linux, both Gnomebaker and K3B beat it in about every way..

---

### Post by Cardmaster91 on 2007-02-17
Sorry i was late to respond, i had to sleep.

> **CodyJarrett said:**
> This command finally got rid of the cursed thing for me:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq nerolinux
```

you might need to remove all files beginning with nerolinux from the /var/lib/dpkg/info/ folder.

Hope this helps.

Thanks man, this worked great.

Now, mcduck. 
I'm sort of new to the whole writing to dv thing, but why is nero so bad? I used it on windows, and was excellent for me, never had a problem. I tried getting gnome baker off the synaptic, to take a look at it. I then tested it, wrote a short clip to a dvd, but it wont play in a dvd player. How do i get it to play in a dvd player?

If i do decide to use nero, is there a "safe" way i can get it?

---

### Post by mcduck on 2007-02-17
It might not be very bad, but the last time I tried it it was nowhere close to the windows version, or any native burning app in Linux. It also crashed a lot.

I really can't see any reason to pay for it (or use it instead of Gnomebaker/K3B which are both free, work great and can be installed with Ubuntu's package management.)

After installing I find Gnomebaker in both Applications/Accessories and Applications/Sound & Video. You might need to run 'killall gnome-panel' to refreshh the panel (or log out & back again)

---

### Post by Cardmaster91 on 2007-02-17
yea, i found gnome baker, it started with cd/dvd i was looking in g.

but gnome baker can only make data dvds. i need these dvd's to play in older model dvd players.

and i was just trying the trial nerolinux, to see if it was good. I still woould like to try it for myself. i tried installing it again, and it worked. but i cant find it,

---

