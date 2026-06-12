---
title: "Unable to get past login screen (kubuntu)"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by thunderstorm on 2007-03-08
I rebooted my computer last night, and can no longer login.

I enter my password, and the loading icon pops up, the screen goes black, and I am back at the login screen.

I know I am using the correct password, as incorrect passwords do not attempt to load the desktop.

Please help!

---

### Post by taurus on 2007-03-08
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your name and password.  Then, post the output of this command here.

```
df  -h
```

---

### Post by Leonivek on 2007-03-08
This is only in KDE and not Gnome?

---

### Post by dexter on 2007-03-08
Try going into a terminal and restart your gdm

- press ctrl+alt+F1
- log in
- type sudo /etc/init.d/gdm restart

Go back to graphic mode (if it doesn't happen automatic) by pressing ctrl+alt+F7.

If is still doesn't work, it's probably a problem with your X server. Did you upgrade your graphic driver recently ? Try posting the content of /etc/X11/xorg.conf, maybe that can help us track down the problem.

---

### Post by thunderstorm on 2007-03-08
> **taurus said:**
> At the GUI login screen, press <Ctrl><Alt>F2 and log in with your name and password.  Then, post the output of this command here.

```
df  -h
```


/dev/hda1 53g 51g 0 100% /
varrun 506m 76k 506m 1% /var/run
varlock 506m 0 506m 0% /var/lock
procbususb 10m 124k 9.9m 2%
udev same as above
devshm 506m 0 506m 0%

Had to type that on the Wii...

---

### Post by thunderstorm on 2007-03-08
> **dexter said:**
> Try going into a terminal and restart your gdm

- press ctrl+alt+F1
- log in
- type sudo /etc/init.d/gdm restart

Go back to graphic mode (if it doesn't happen automatic) by pressing ctrl+alt+F7.

If is still doesn't work, it's probably a problem with your X server. Did you upgrade your graphic driver recently ? Try posting the content of /etc/X11/xorg.conf, maybe that can help us track down the problem.

That one gave me an error message... command not found.

---

### Post by taurus on 2007-03-08
> **thunderstorm said:**
> **[COLOR="Red"]/dev/hda1 53g 51g 0 100% /[/COLOR]**
varrun 506m 76k 506m 1% /var/run
varlock 506m 0 506m 0% /var/lock
procbususb 10m 124k 9.9m 2%
udev same as above
devshm 506m 0 506m 0%

Had to type that on the Wii...

You just filled up your 53GB of space!  

While still in recovery mode, clean out your cache to give you some room with

```
aptitude clean
```
Then, reboot and you should be able to log in now.  Now, post the output of this command from a terminal.

```
sudo du -h /var
```

---

### Post by thunderstorm on 2007-03-08
> **taurus said:**
> You just filled up your 53GB of space!  

While still in recovery mode, clean out your cache to give you some room with

```
aptitude clean
```
Then, reboot and you should be able to log in now.  Now, post the output of this command from a terminal.

```
sudo du -h /var
```

That worked!  Thank you SO much!

---

### Post by eyyuplu on 2007-03-17
hi
my problem like this.&#305; dist-upgarade 6.10.and start this problem.

I enter my password, and the loading icon pops up, the screen goes black, and I am back at the login screen.

but &#305; can login recovery mod.write this recovery console.
#kdm
and start kdm login screen and write user and psw.no problem &#305; can start kde.,,,
but cant login normal mod login screen goes black,
tnx..

---

