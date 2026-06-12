---
title: "[SOLVED] HELP!! What did I DO?!?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-07-26
Ok.. so things were going fine and I was attempting to get my Nvidia GeForce 5200 vid card to work. For some reason it just didn't want to go and would freeze up at the splash screen. Switched back to onboard and would have to reconfigure. Then after my "26th attempt" my puter decides it's going to do a check disk to make sure things are ok. After that it booted back up and I went to sign into Ubunutu. Then it froze after log-in! Logged into terminal... settings were fine! Now here's my prob. I installed displayconfig. Upon running it, it's showing that it thinks there's 2 monitors. I now have 5 xorg.conf backups that I can't delete and I keep getting permission denied when trying to delete them. How do I fix this?!? Thanks everyone!!!

---

### Post by phidia on 2007-07-26
To delete files from the CLI you need to preface the command with "sudo".
I'm not sure what's up with your video card. What method are you using to get the nvidia driver installed?
You may want to check out the video section of the forums.

---

### Post by Tomosaur on 2007-07-26
> **andyho said:**
> Ok.. so things were going fine and I was attempting to get my Nvidia GeForce 5200 vid card to work. For some reason it just didn't want to go and would freeze up at the splash screen. Switched back to onboard and would have to reconfigure. Then after my "26th attempt" my puter decides it's going to do a check disk to make sure things are ok. After that it booted back up and I went to sign into Ubunutu. Then it froze after log-in! Logged into terminal... settings were fine! Now here's my prob. I installed displayconfig. Upon running it, it's showing that it thinks there's 2 monitors. I now have 5 xorg.conf backups that I can't delete and I keep getting permission denied when trying to delete them. How do I fix this?!? Thanks everyone!!!

In Linux, you generally only have sufficient permissions to mess with files inside your home directory. Everything outside that, you need root permissions. To temporarily gain root permissions, you use the 'sudo' prefix command:

```

sudo rm /etc/X11/xorg.conf.backup

```

to delete a file, or:
```

sudo nano /etc/X11/xorg.conf

```

to open and edit a file.

This will ask you for your own user password (to make sure it's not an attacker or other malicious person). You will not see your password being typed, so be sure to spell it correctly.

---

### Post by andyho on 2007-07-26
> **Tomosaur said:**
> In Linux, you generally only have sufficient permissions to mess with files inside your home directory. Everything outside that, you need root permissions. To temporarily gain root permissions, you use the 'sudo' prefix command:

```

sudo rm /etc/X11/xorg.conf.backup

```


yep.. I actually tried that and it automatically just gives me permission denied?! As far as methods.. When I could login in using the onboard I tried using Synaptic or maybe it was restricted drivers?! I also tried installing the drivers from the terminal. One thing right away that happens when rebooting after putting the nvidia drivers in is it'll tell me the xserver isn't configured correctly. There's also a place to select nv or nvidia.. which I've seen it selected both ways, so I'm not sure which one is correct either. For now I'm just trying to at least be able to use the onboard.

---

### Post by justin whitaker on 2007-07-26
> **andyho said:**
> yep.. I actually tried that and it automatically just gives me permission denied?! As far as methods.. When I could login in using the onboard I tried using Synaptic or maybe it was restricted drivers?! I also tried installing the drivers from the terminal. One thing right away that happens when rebooting after putting the nvidia drivers in is it'll tell me the xserver isn't configured correctly. There's also a place to select nv or nvidia.. which I've seen it selected both ways, so I'm not sure which one is correct either. For now I'm just trying to at least be able to use the onboard.

Login as root. That will give you permissions...if you haven't done so, sudo passwd, and give root a separate password. Then you can really mess up your system. :)

---

### Post by andyho on 2007-07-26
Well yea! I was able to delete the backups, but still no luck on startup.. still freezes after login.. :(

---

### Post by andyho on 2007-07-26
woo hoo!! I was able to get back up and running with the onboard by using sudo dpkg-reconfigure -phigh xserver-xorg. Does that make any sense??? I'm assuming somewhere my settings got jacked up, obviously. Now I just gotta figure out WHAT I actually did!! At least it isn't freezing up though! ;) Thanks for the help guys!!

---

### Post by andyho on 2007-07-26
> **andyho said:**
> woo hoo!! I was able to get back up and running with the onboard by using sudo dpkg-reconfigure -phigh xserver-xorg. Does that make any sense??? I'm assuming somewhere my settings got jacked up, obviously. Now I just gotta figure out WHAT I actually did!! At least it isn't freezing up though! ;) Thanks for the help guys!!

Ok.. so I figured out the whole "what I did"! Yea go me! Not only that BUT I got my graphics card working!!! WOO HOO!!!!! :KS

---

