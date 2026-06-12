---
title: "How to setup the Display after installing Desktop for Ubuntu server"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by lafaki on 2008-02-10
Hi,

I am a very happy user of Ubuntu Server 7.10.

Recently I tried to install the GNOM desktop by using the below command:

sudo apt-get install ubuntu-desktop

It worked 98% fine except the below errors/warnings:

[SIZE="4"][COLOR="Silver"]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.11+2nobinonly-0ubuntu0.7.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.11+2nobinonly-0ubuntu0.7.10_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.11+2nobinonly-0ubuntu0.7.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.11+2nobinonly-0ubuntu0.7.10_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14_2.6.22-14.47_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14_2.6.22-14.47_all.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.47_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.47_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/COLOR][/SIZE]

After that I did a reboot over SSH  (as I do not have any keyboard connected to the server), but there was no desktop loaded locally on the server. 

Do you know what do I have to do in order to run the DEsktop (level 5) on the Ubuntu server right after installing it??

Btw, how can I install the above failed packages?

Thanks for your help!
Akis

---

### Post by njparton on 2008-02-11
Try the following and post back:

```
sudo /etc/init.d/gdm start
```

You'll then need to install an xclient in windows (e.g. xming) or a vnc client in linux to connect to it.

---

### Post by lafaki on 2008-02-11
I ran the command and got the following error:

sudo: /etc/init.d/gdm: command not found

---

### Post by njparton on 2008-02-11
You did run it without the colons didn't you?

I've never tried to install gnome onto a server installation so unfortunately all I can say is that what you did wasn't sucessful.

There are loads of thread in the forum for how to do it, you may need more packages than just ubuntu-desktop.

Once it's installed properly, you may need to run that command if it doesn't automatically start on boot up.

---

### Post by hyper_ch on 2008-02-11
what happens if you run

```

startx

```

---

### Post by lafaki on 2008-02-12
Startx didn't work either.

What I did and worked was to run locally on the machine the command 

sudo aptitude install ubuntu-desktop

Now it is working fine, thanks for your help!

:-)

---

