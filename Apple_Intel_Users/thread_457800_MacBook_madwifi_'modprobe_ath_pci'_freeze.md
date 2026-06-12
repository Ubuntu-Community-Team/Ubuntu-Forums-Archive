---
title: "MacBook madwifi 'modprobe ath_pci' freeze"
date: 2007-05-29
forum: Apple Intel Users
---

### Post by jrodia on 2007-05-29
I have a dual boot OS/X and Feisty on my Macbook C2D. Everything was working perfectly up until the point where I needed to enable wireless networking in Linux (makes it easier to follow lectures in class, etc.)

So I read up on the latest madwifi drivers, see that they finally support the new Atheros chips in the C2D, I download the latest snapshot, install it, and everything seems to be running smoothly. I sudo modprobe ath_pci after installing, and the entire system freezes. I wait about 10 minutes, and then hard reboot the computer. But now, Ubuntu won't even boot. It gets about 1/6 of the way through the status bar, and then stops. This has happened twice already, and I've had to reinstall Ubuntu both times.

What could be causing this freeze? I thought the drivers worked swimmingly for most people.

---

### Post by Gen2ly on 2007-05-29
Hmm, sounds like a kernel issue.  See if your config has the required settings:

```
grep WIRELESS /usr/src/linux/.config
```

What does it list?  If you have a kernel thats newer you'll see something like this:

```
CONFIG_WIRELESS_EXT=y
```

Also Benanzo as nice post on howto install these drivers.

[Weblink]("http://ubuntuforums.org/showpost.php?p=2731459&postcount=25")

---

### Post by jrodia on 2007-05-29
The tutorial of sorts that I followed was very similar to that one, up until the point when I had to modprobe the wireless device. That's when the system locked up and would not boot again.

As for the code segments you posted, I'll have the results up when I get back from work and I'm able to reinstall Ubuntu again.

---

### Post by jrodia on 2007-05-29
grep WIERELESS /usr/src/linux/.config yielded:

grep: /usr/src/linux/.config: No such file or directory.

Which is... odd.

And the howto you provided gave the same result. Froze when I tried modprobing the driver.

---

### Post by Gen2ly on 2007-05-29
My bad, you probably have you config in /boot try:

```
grep WIRELESS /boot/config*
```

---

### Post by jrodia on 2007-05-29
Well... I found a howto online that had every step as the one you linked me to, only the sudo modprobe ath_pci wasn't necessary. i rebooted after the make install, and VOILA! there's wireless. i have no idea why it works... I'm just glad it did.

But thanks for all your help.

---

### Post by cevans on 2007-05-30
> **jrodia said:**
> Well... I found a howto online that had every step as the one you linked me to, only the sudo modprobe ath_pci wasn't necessary. i rebooted after the make install, and VOILA! there's wireless. i have no idea why it works... I'm just glad it did.

But thanks for all your help.

Could you give us a link to that howto? I am having the same problem. My guess is that there is a problem with the current trunk, but I do not know how far back I need to go to get working sources.

Edit: I just found one that works - **r2372**, which can be found on the [snapshots page]("http://snapshots.madwifi.org/madwifi-ng/"). It remains to be seen which change actually caused this. If anyone has the free time, it would be a great help to Intel Mac users if someone could download each snapshot past r2372 and compile and install each one, unloading and loading ath_pci each time, until the kernel panics, so that we will know where the problem lies.

---

### Post by jrodia on 2007-05-30
All I did was the following:

```
sudo aptitude install build-essential
wget http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz
tar -zxvf madwifi<tab>
cd madwifi<tab>
make
sudo make install   (answer 'r' when asked)
```

And then instead of 'sudo modprobe ath_pci', just reboot from there. NetworkManager will pick up your device.

---

