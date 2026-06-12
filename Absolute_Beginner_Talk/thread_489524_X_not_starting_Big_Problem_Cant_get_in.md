---
title: "X not starting: Big Problem Cant get in"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-07-01
Hi,

I was installing and uninstalling a lot of stuff today for trying out new things. The last thing I did was to use Kompose and I also enabled transparency effects on the desktop management. I also installed some firewall...I dont remember what the name was...But I know it was not firestarter. Anyway, after all this I turned off my laptop and turned it back on after sometime. It booted and when it was supposed to show the kdm screen, it just showed a blank screen with the cursor blinking at the beginning. I restarted the laptop and went into recovery and tried to startx from there. I got the following error:

xauth: creating new authority file /root/.serverauth.4255

/etc/X11/X is not executable
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

I had a backup of my xorg.conf so I loaded it back and tried again in recovery mode. But I still got the same error. I dont know what else to do now. I have been using Kubuntu for nearly 2 weeks now and I have a lot of stuff inside thats important to me and I dont want to end up having to reinstall the whole thing.

Please help!
Thanks.

P.S: I also have the live cd...

---

### Post by Shazaam on 2007-07-01
Have you tried the "dpkg-reconfigure" yet for x?

---

### Post by linuxnovice on 2007-07-01
I tried it now and got the error:
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed.

:(

---

### Post by linuxnovice on 2007-07-01
Sorry to be annoying but this situation of not able to get into my desktop is killing me.

I just remembered that I also installed gdesklets today.

---

### Post by linuxnovice on 2007-07-01
Help please.
I am still in recovery mode and I can access the internet...but my Xserver is still not starting up. Please help.

---

### Post by linuxnovice on 2007-07-01
Can someone please help me on this?

---

### Post by mendingo84 on 2007-07-01
reintall your X-server
```

sudo apt-get install --reinstall xserver-xorg
```

---

### Post by mendingo84 on 2007-07-01
do you happen to have an NVidia video?

---

### Post by linuxnovice on 2007-07-01
No. I dont have a NVidia Video card.
That did the trick. I think that enabling transperency effects somehow messed up teh X server. I have a few questions.

1) While using recovery mode the system didnt ask me for a password and once xserver was reinstalled i could even get into the x without having to type a password. Isnt this insecure? I mean anyone can boot up the machine and go into recovery and do stuff that shouldnt be done.

2) How do make applications start during login. I installed the autostart extension for kcontrol and added kompose to it. But I got an error saying that its not a valid command or something.

Thanks.

---

### Post by mendingo84 on 2007-07-01
1 question: i never thought of that :), but it's the safest way to recover if things go wrong or you forget your root pass ;). network is not accesible through recovery mode so you can't be hurt from a remote machine only someone having physical access to the PC. good news is you can edit grub so that recovery mode option is not listed when booting so you and only you (knowing the root pass) will be able to change that back ;). i also think that there is an option to set a password for booting in recovery mode. (dunno how it might be done because i never studied that option) . 
2 question: you have to add that apps in the /etc/init.d/ directory i think

---

