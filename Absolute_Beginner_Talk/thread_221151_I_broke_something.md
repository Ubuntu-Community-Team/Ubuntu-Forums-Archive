---
title: "I broke something"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Taiden on 2006-07-22
I'm not entirely sure how I did it to be honest. I tried installing some audio drivers for my AC97 on-board audio chipset. It got halfway through the installation and crapped out on me, said there wasn't a C complier that it could use. Anyway, shit stopped working, like I couldn't open a new Terminal from within Gnome. I restarted, and got this message via a message box that popped up saying that I was logged in for less than 10 seconds etc etc.


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "greybox"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

Right now I am in failsafe terminal mode running firefox. :mrgreen: 

Any ideas would be wonderful.

---

### Post by derouge on 2006-07-22
```
sudo apt-get install alsa-base
```
Install that and then clear the temp directory:
```
cd tmp
sudo rm *
```

---

### Post by Sef on 2006-07-22
> there wasn't a C complier that it could use. 

You need to install build-essential to have a C compiler.

Ubuntu: Open the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo aptitude install build-essential

---

### Post by Taiden on 2006-07-22
Okay, one thing that seems to be screwing me over is us.archive.ubuntu.com keeps timing out on me. I tried to do a sudo apt-get update, but it times out for us.archive.ubuntu.com (146.137.96.15).

I will try those things and get back to you. Thanks for your help.

---

### Post by Taiden on 2006-07-22
Okay,

1) alsa-base is already installed and at the most recent version.
2) I cleared the /tmp directory completely.
3) I cannot use apt-get because us.archive.ubuntu.com keeps timing out on me, and yet ping us.archive.ubuntu.com works fine (150 ms average, no drops out of 100 pings).

Hrm.

---

### Post by Taiden on 2006-07-22
Can someone try an apt-get install or apt-get update and tell me if I am the only one that cannot connect to us.archive.ubuntu.com?

---

### Post by jimmygoon on 2006-07-22
> **Taiden said:**
> Can someone try an apt-get install or apt-get update and tell me if I am the only one that cannot connect to us.archive.ubuntu.com?

don't worry... you're not! Just edit your apt repos and remove the us from the beginning of it... (or at least those are the instructions I'm continuing to read)

---

### Post by Taiden on 2006-07-22
alright, thanks for the help guys. finally got myself able to log into gnome, but the only way i did that was to run a sudo ./install for the RealTek drivers I downloaded from their website (NEVER AGAIN!!) after I got build-essential.

So gnome works now, I just have no sound. grah!

that's what happens when you meddle with things that already work. is there any easy way to revert back to ubuntus original sound driver?

---

### Post by Taiden on 2006-07-22
So I followed the Comprehencive Sound Problem thread, and got everything installed on that page, but when I type [b]sudo modprobe snd-intel8x0[b] it says:


greybox@Greybox:/usr/src/modules/alsa-driver$ sudo modprobe snd-intel8x0
FATAL: Module snd_intel8x0 not found.

---

