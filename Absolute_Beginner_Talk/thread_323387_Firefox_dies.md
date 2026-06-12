---
title: "Firefox dies"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by topez on 2006-12-22
The minute I try to strat firefox, it quits. Worked alright in dapper but, just upgraded to edgy.
No problem using opera.

---

### Post by bruenig on 2006-12-22
> **topez said:**
> The minute I try to strat firefox, it quits. Worked alright in dapper but, just upgraded to edgy.
No problem using opera.

Run firefox in the terminal and post the output.

---

### Post by topez on 2006-12-22
Here is request

---

### Post by towsonu2003 on 2006-12-22
looks more like a bug than a simple glitch...

[list]
[*]first, do a 
```
sudo apt-get update
sudo apt-get dist-upgrade
``` to check out if you are up-to-date. if not, update the packages and try again. 

[*]does this work: 
```
firefox -safe-mode
``` and try starting firefox without extensions and plugins for once.

[*]if that doesn't work, try starting with a new profile:
```
cd
mv .mozilla ~/Desktop/mozilla
firefox
```

[*]if that doesn't work either you're stuck. file a bug report here: [https://bugs.launchpad.net/distros/ubuntu/+source/firefox/+filebug](https://bugs.launchpad.net/distros/ubuntu/+source/firefox/+filebug) following the guidelines here (crashing bugs): [click on this]("https://wiki.ubuntu.com/DebuggingFirefox#head-0b1c7e52ff381ff6a33a4575bbeee1b1ec9b9618")

[*]in the meantime, if you'd prefer firefox, you could use the following guide to install firefox temporarily (quick and dirty):
[click here]("https://help.ubuntu.com/community/FirefoxNewVersion#head-4f560dcd726b6eda7682e45ed7925c641e9e279b") 

[*]don't forget to copy back your profile: 
```

cd
mv .mozilla .mozilla-clean
cp -r ~/Desktop/mozilla .mozilla

```

[*]leave the mozilla folder on your desktop in case you need it later on.[/list]

---

### Post by topez on 2006-12-23
I did a add & remove firefox and it did not clear the problem. (More info......I upgraded bigdaddy to edgy doing the different upgrade steps. It got me to edgy but with problems so I figured if I went and got the edgy iso and did a complete reformat and install I would have a better product. No way, many many missing parts, one I really like is synaptic, no gedit, the k menu is very small). I sure hope there is a short cut to solve my problem.](*,)
](*,)

---

