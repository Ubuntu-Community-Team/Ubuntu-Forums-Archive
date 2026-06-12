---
title: "Boot Problem"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by P-FUND on 2008-01-06
i've been using ubuntu 7.10 on my old gateway for a week or two. had to use the alternative installer because the livecd wouldnt run. otherwise, its been running fairly smoothly. when i entered my username and password today, i got a blank beige screen and ubuntu would not load. any suggestions? i dont know anything about linux, so please speak in terms which i may understand.

---

### Post by dbbolton on 2008-01-06
> **P-FUND said:**
> i've been using ubuntu 7.10 on my old gateway for a week or two. had to use the alternative installer because the livecd wouldnt run. otherwise, its been running fairly smoothly. when i entered my username and password today, i got a blank beige screen and ubuntu would not load. any suggestions? i dont know anything about linux, so please speak in terms which i may understand.
is it possible that you ran out of hard disk space?

---

### Post by esodin on 2008-01-06
I have had the same issues lately.

What fixed it for me was to remove my old xorg.conf file. To try this solution do the following:

1. When you get your "blank" screen hit "Ctrl"+"Alt"+"F1" this will bring up a terminal. 
2. Log in using your normal user name and pasword
3. Change directory to the location of your xorg.conf file:
```
cd /etc/X11
```
4. Rename your xorg.conf file (that way you have a backup):
```
sudo mv xorg.conf xorg.conf.bakup
```
You will be asked to enter your password.

You can restart your windows manager by either;
a. Rebooting from the terminal
```
sudo reboot
```

or
b. by restarting your windows manager:
1. Go back to your windows manager by hitting "Ctrl"+"Alt"+"F7"
2. Restart your windows manager by hitting "Ctrl"+"Alt"+"Backspace"

Good luck!

---

### Post by P-FUND on 2008-01-07
i found a way around this. i clicked options and selected gnome in the "session" thingy, and it seems to be working, any reason why xclient (or whatever the other one is) is the default? is there any problems with my easy way out?

---

