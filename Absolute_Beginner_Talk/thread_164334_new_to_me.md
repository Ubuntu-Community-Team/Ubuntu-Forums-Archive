---
title: "new to me"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by stableflame on 2006-04-22
OK, this is Linux is brand new to me but I wanted to give it a go without cocking up W*nd$ws :rolleyes: :rolleyes: . Anyway I have a spare HDD in an external caddy with USB2 connection. I unplugged my C drive and booted up with the Install Ubuntu CD, followed the instructions installing to the USB drive right to the end when I was instructed to remove the CD and reboot, which I did. The reboot ended with a command line --- and I am now totally lost](*,) ](*,) can anyone help?

stableflame

---

### Post by Qrk on 2006-04-22
There can be several issues. 

You should have seen about 20 minutes worth of text scroll down the screen as the rest of ubuntu was installed. If this happend, try logging in with you username and password and then typing:

```
startx
```

This probably won't work, but thats Ok. If you get a dialog telling you to reconfigure X, type this command at the prompt:

```
sudo dpkg-reconfigure xerver-xorg
```

Follow the onscreen instructions.

If it didn't flash 20 min of unreadable text in front of you, or if it complains about X not being found, perhaps your installation didn't install the graphical part of Ubuntu, fix it by typing this:

```
sudo apt-get install ubuntu-desktop
```

with either your cd in the drive or an active internet connection.

---

