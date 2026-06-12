---
title: "wireless not working..."
date: 2008-10-25
forum: Arch and derivatives
---

### Post by jimi_hendrix on 2008-10-25
hi so i just installed arch over ubuntu

the install went well and now im looking at a command line trying to set up my internet because apparently i messed something up with the script during install

so while looking at a bunch of tutorials i try and run the iwconfig command but bash says its not found

any pointers (tried the wiki and arch forums...kinda last shot here)

---

### Post by fwojciec on 2008-10-25
On my system:
```
$ pacman -Qo /usr/sbin/iwconfig
/usr/sbin/iwconfig is owned by wireless_tools 29-2
```
In other words -- package "wireless_tools" provides this particular tool.  Maybe you didn't install it for some reason during the initial installation...

---

### Post by jimi_hendrix on 2008-10-25
well since i cant access the internet i cant get to the repo...so what should i do?

---

### Post by fwojciec on 2008-10-25
It's somewhere on the install CD, I imagine, so you should be able to mount the cd manually and install the package from there using pacman -U /path/to/package.pkg.tar.gz.

---

### Post by jimi_hendrix on 2008-10-25
ok one last thing then...how will i find the package?

---

### Post by jimi_hendrix on 2008-10-25
got it

but new problem

when i enter iwlist scanning it says 

wlan0        interface doesnt support scanning : Network is down

when i am posting this from the same network

---

### Post by fwojciec on 2008-10-25
You probably need to bring the interface up first: "ifconfig wlan0 up" as root.

---

### Post by jimi_hendrix on 2008-10-25
i get this back

```

SIOCSIFFLAGS :  No such file or directory

```

---

### Post by fwojciec on 2008-10-25
I don't know what sort of wifi hardware you have, but it sounds like, for example, you haven't installed the correct firmware package or something like this.  You should search Arch wiki and forums for information specific to your wifi chipset.

---

### Post by jimi_hendrix on 2008-10-25
thanks i got it to work

---

### Post by jimi_hendrix on 2008-10-25
ugg i had to reboot and i forgot how i got connected...now i get that same error about how network is down

---

