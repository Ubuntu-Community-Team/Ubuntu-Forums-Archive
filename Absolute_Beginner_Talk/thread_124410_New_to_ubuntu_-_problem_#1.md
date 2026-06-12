---
title: "New to ubuntu - problem #1"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Avalanche on 2006-02-01
Hi

I'm completely new to Linux/Ubuntu, having been a Windows 95, 98, 2000 and then XP user. Been meaning to make the switch for a while - now I'm forcing myself onto this new OS!

I have one irritation though that I need to get sorted before I can get on and use this computer again. Graphics drivers! My screen will not go any higher than 1024x768, and 60Hz. 

Edit : Found device manager (duh)

I need to find out what the GPU is, locate the drivers (hopefully), and install them. Anyone who could push me in the right direction, I would greatly appreciate it.

Cheers,
Andy.

---

### Post by Lord Illidan on 2006-02-01
So what is your GPU then?

To save you some trouble, go to XP and write down a list of your hardware, including the video card, the soundcard, and modem settings.
Then we can see if there are drivers available. If you use NVIDIA you are in luck, and if you use ATI, driver support should be pretty good too.

---

### Post by Avalanche on 2006-02-01
Thanks, the GPU is an nVidia GeForce2 MX

I have downloaded one of the packages from nVidia, the  'IA32' package, hope that is right :-? 

Just need to figure out how to log on as root now, in order to install it (lol)

---

### Post by dueY on 2006-02-01
[QUOTE=Avalanche]

Just need to figure out how to log on as root now, in order to install it (lol)[/QUOTE]

Set a root password ```
sudo passwd root
```

---

### Post by towsonu2003 on 2006-02-01
don't logon as root. use sudo command.
so if you were to launch synaptic(package manager) as root, you'll do:
```
sudo synaptic
```
also, don't set a root password. if you did, search the forums to get more info about it...

for nvidia, search the forum's tips and trick section using nvidia as keyword. you will be looking for a howto that describes the steps. (I wish I had nvidia and not ati)

---

### Post by Avalanche on 2006-02-01
uh, can't get this working at all. I did apply a password to root, from administration > users&groups, but it won't let me set a blank password.

Anyway, here's what I'm doing (in terminal) :

Edit : Updated
```

andy@ubuntu:~$ sudo sh /home/andy/NFORCE-Linux-x86-1.0-0310-pkg1.run
Verifying archive integrity...OK
Uncompressing NVIDIA nForce drivers for Linux-x86 1.0-0310..........................................................................................................................................................................................................................................................................

```

Ok, this worked, sort of. It launched the nVidia install application in a window, but then complained that 'ld' was not found, and I don't have 'binutils' (or something like that). Now I'm stumped.

I hope I can stick with this long enough to get it working, I feel like a n00b all over again :rolleyes:

---

### Post by AmboyGuy on 2006-02-01
You can get binutils on synaptic just enable/add the repositories.
System > Admin > Synaptic Package Manager > settings > repositories

Automatix will automatically install the Nvidia drivers also.
**Automatix (Automated GUI installation script) **[http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")
You may not learn as much but you'll get it working faster.

---

